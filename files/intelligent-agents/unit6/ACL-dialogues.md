# Agent Dialogue: Alice (Procurement) and Bob (Inventory Control)

## 1. Agent Goals and Interaction

- **Alice (procurement agent)**: goal is to decide whether, and how much, stock to order. Before issuing a purchase order she needs to know the current stock level of a product and its specifications (features). Alice is the **initiator** of the conversation.
- **Bob (warehouse inventory agent)**: goal is to maintain an authoritative, accurate record of stock levels and product attributes, and to respond truthfully to queries from authorized agents. Bob is the **responder**, remaining passive until asked. If Bob cannot answer a query (e.g. the product is unknown), he replies with `sorry` instead of `tell`.


## 2. Ontology

Both agents interpret the vocabulary below identically, under the shared ontology `warehouse-stock-ontology`.

**Concepts**
- `product` — a sellable item, identified by a symbol (e.g. `television-50in`).
- `feature` — an attribute of a product (e.g. the number of HDMI ports it has).
- `quantity` — a non-negative integer count of stock.

**Predicates/relations used in `:content`**
- `(stock-level ?product ?quantity)` — the quantity of `?product` currently held in the warehouse.
- `(has-feature ?product ?feature ?value)` — `?product` has `?feature` equal to `?value` (e.g. `hdmi-ports`).
- `(procure-decision ?product ?decision)` — the decision on whether/how much to procure `?product` (e.g. `proceed`, `delay`, `cancel`).


## 3. KQML Dialogue

### Exchange 1 — stock level query

```lisp
(ask-one
  :sender alice
  :receiver bob
  :content (stock-level television-50in ?quantity)
  :reply-with q1
  :language KIF
  :ontology warehouse-stock-ontology)

(tell
  :sender bob
  :receiver alice
  :content (stock-level television-50in 42)
  :in-reply-to q1
  :language KIF
  :ontology warehouse-stock-ontology)
```

### Exchange 2 — HDMI ports query

```lisp
(ask-one
  :sender alice
  :receiver bob
  :content (has-feature television-50in hdmi-ports ?n)
  :reply-with q2
  :language KIF
  :ontology warehouse-stock-ontology)

(tell
  :sender bob
  :receiver alice
  :content (has-feature television-50in hdmi-ports 4)
  :in-reply-to q2
  :language KIF
  :ontology warehouse-stock-ontology)
```


### Exchange 3 — unknown product (error handling)

```lisp
(ask-one
  :sender alice
  :receiver bob
  :content (stock-level television-80in ?quantity)
  :reply-with q3
  :language KIF
  :ontology warehouse-stock-ontology)

(sorry
  :sender bob
  :receiver alice
  :content (unknown-product television-80in)
  :in-reply-to q3
  :language KIF
  :ontology warehouse-stock-ontology)
```


### Exchange 4 — procurement decision

```lisp
(achieve
  :sender alice
  :receiver bob
  :content (procure-decision television-50in ?decision)
  :reply-with q4
  :language KIF
  :ontology warehouse-stock-ontology)

(tell
  :sender bob
  :receiver alice
  :content (procure-decision television-50in proceed)
  :in-reply-to q4
  :language KIF
  :ontology warehouse-stock-ontology)
```

With 42 units in stock, 4 HDMI ports confirmed, and a `proceed` decision, Alice has what she needs to carry on with procurement for `television-50in`.

## 4. Same Dialogue Using FIPA ACL

The exchanges above map onto FIPA ACL performatives as follows:

| KQML performative | FIPA ACL performative | Purpose |
|---|---|---|
| `ask-one` | `query-ref` | request the value of a referential expression |
| `tell` | `inform` | assert that a proposition is true |
| `sorry` | `failure` | report that the request could not be fulfilled |
| `achieve` | `request` | ask the receiver to perform an action / bring about a state of affairs |

FIPA messages add a `:protocol` (the interaction protocol being followed, `fipa-query`) and a `:conversation-id` (groups all messages belonging to this dialogue), and use `fipa-sl` as the content language in place of KIF.

Rather than four standalone exchanges, the dialogue is organized around two standard FIPA interaction protocols, each of which already defines its own success/failure branches:

| Exchange | Protocol | Performatives used |
|---|---|---|
| Stock level, HDMI ports, unknown-product | `fipa-query` | `query-ref` → `inform` / `failure` |
| Procurement decision | `fipa-request` | `request` → `inform-done` |

### FIPA Query Protocol (`fipa-query`)


#### Exchange 1 — stock level query

```lisp
(query-ref
  :sender alice
  :receiver bob
  :content (stock-level television-50in)
  :reply-with q1
  :language fipa-sl
  :ontology warehouse-stock-ontology
  :protocol fipa-query
  :conversation-id conv1)

(inform
  :sender bob
  :receiver alice
  :content (= (stock-level television-50in) 42)
  :in-reply-to q1
  :language fipa-sl
  :ontology warehouse-stock-ontology
  :protocol fipa-query
  :conversation-id conv1)
  ```

#### Exchange 2 — HDMI ports query

```lisp
(query-ref
  :sender alice
  :receiver bob
  :content (has-feature television-50in hdmi-ports)
  :reply-with q2
  :language fipa-sl
  :ontology warehouse-stock-ontology
  :protocol fipa-query
  :conversation-id conv1)

(inform
  :sender bob
  :receiver alice
  :content (= (has-feature television-50in hdmi-ports) 4)
  :in-reply-to q2
  :language fipa-sl
  :ontology warehouse-stock-ontology
  :protocol fipa-query
  :conversation-id conv1)
  ```

#### Exchange 3 — unknown product (failure branch)

```lisp
(query-ref
  :sender alice
  :receiver bob
  :content (stock-level television-80in)
  :reply-with q3
  :language fipa-sl
  :ontology warehouse-stock-ontology
  :protocol fipa-query
  :conversation-id conv1)

(failure
  :sender bob
  :receiver alice
  :content (unknown-product television-80in)
  :in-reply-to q3
  :language fipa-sl
  :ontology warehouse-stock-ontology
  :protocol fipa-query
  :conversation-id conv1)
  ```

### FIPA Request Protocol (fipa-request)

#### Exchange 4 — procurement decision

```lisp
(request
  :sender alice
  :receiver bob
  :content (action bob (decide-procurement television-50in))
  :reply-with q4
  :language fipa-sl
  :ontology warehouse-stock-ontology
  :protocol fipa-request
  :conversation-id conv1)


(inform-done
  :sender bob
  :receiver alice
  :content (done
             (action bob (decide-procurement television-50in))
             (= (procure-decision television-50in) proceed))
  :in-reply-to q4
  :language fipa-sl
  :ontology warehouse-stock-ontology
  :protocol fipa-request
  :conversation-id conv1)
  ```