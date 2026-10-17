# Reflection on XAI

## What

The [Multi-Agent Academic Investigator](https://github.com/luitoz/multi-agent-academic-investigator) uses LangGraph, which explicitly defines state, nodes, edges, and tools, making the agent workflow transparent.

The evidence analysis agent uses a deterministic screening process for retrieved papers. Only the aggregate verdict (reliable, questionable, or unreliable) is kept in the graph state; the individual check results and per-paper scores are written to the log file only.

LLM outputs (objectives, search dimensions, synthesis, and briefing) are included in the graph state, but the system does not capture a rationale or show how alternative objectives, queries, or interpretations were considered.

LLM is instructed to generate claims only from gathered papers, but there is no explicit mapping from each claim to source-paper excerpts that can be verified.

## So what

As a result, a user or evaluator cannot currently see why a paper was rejected, reproduce a search, or verify that a reported claim follows from the papers cited.

The most important improvement to explainability is to map each generated claim to its source paper ID and the specific excerpt that supports it. A verification step would then check that each excerpt supports its claim; this reduces, but does not eliminate, the risk of LLM hallucinations, so it should combine deterministic checks (e.g., the cited paper and excerpt exist in the retrieved set) with an LLM-based check.

The lack of detailed check results in the final research briefing is a deliberate decision to keep the output user-friendly. It can be addressed without compromising that goal by keeping the main briefing concise and offering an optional audit appendix or detailed mode with per-paper check results, search queries, and retry outcomes.

Rather than logging hidden LLM reasoning, the system should record concise decision records: the objectives and search dimensions chosen, the criteria applied, and the evidence supporting each conclusion. The level of verbosity should be carefully decided to avoid harming the system's response time.

## Now what

### Learning

Making the workflow visible is not the same as making its decisions explainable. LangGraph and deterministic screening show what the system did, but they do not show why an LLM chose particular objectives or queries, or whether a claim is supported by its cited source. Explainability also has to be designed for a specific audience: detailed logs help developers, while end users need concise, verifiable explanations in the output itself.


### Future application

In future multi-agent or LLM-based systems, I will define the explanation requirements for each audience at the design stage rather than adding them afterwards. I will prefer deterministic, auditable logic wherever it is sufficient, and keep source-level provenance for every generated claim. I will also treat verification of LLM output as a separate, testable step, and weigh the cost of explanation detail against response time.

