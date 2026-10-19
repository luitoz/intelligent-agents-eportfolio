# Unit 4 Reflection

## What

Symbolic agents are AI agents that reason using explicit symbolic representations and logical inference rules rather than learning behaviour solely from data. Rooted in classical AI, they view intelligence as the manipulation of symbols according to formal rules.

However, symbolic AI faces challenges such as knowledge engineering and reasoning in dynamic environments. These limitations motivated the development of reactive architectures, which demonstrated that intelligent behaviour can emerge without explicit symbolic reasoning. While reactive systems are responsive, they often struggle with long-term planning.

Hybrid architectures were introduced to combine the strengths of both approaches. For example, the TouringMachines architecture consists of three layers:

- Reactive layer: immediate responses to the environment.
- Planning layer: goal-directed reasoning and action selection.
- Modelling layer: predicts environmental changes and other agents' behaviour.
 
## So What

Agent architectures are commonly classified as deliberative, reactive, or hybrid. Deliberative architectures emphasise reasoning and planning, reactive architectures prioritise rapid responses, and hybrid architectures combine both capabilities.

A key insight is that architecture design involves balancing planning and responsiveness. Purely deliberative systems may reason effectively but react slowly, whereas reactive systems respond quickly but lack sophisticated planning. Hybrid architectures attempt to address both requirements.

These 	ideas remain relevant today. Modern LLM agents can be viewed as hybrid systems, where the LLM provides deliberative capabilities such as reasoning and planning, while tool use and interactions with external environments provide reactive behaviour.

I initially felt overwhelmed by the variety of agent architectures proposed in the literature. Different authors present distinct classifications, including those of Russell and Norvig, Wooldridge, and Kendall. Although many of these categories overlap and describe similar underlying concepts, each framework introduces its own terminology and emphasis. For example, Wooldridge highlights the BDI (Belief-Desire-Intention) architecture as a representative deliberative approach, while other authors focus more heavily on reactive and hybrid paradigms.

I found the diversity of hybrid architectures particularly challenging to understand. While all hybrid architectures aim to combine reactive and deliberative behaviour, they differ significantly in how they organise layers and coordinate control. For instance, the TouringMachines architecture employs horizontally layered components that operate concurrently and compete for control, whereas the 3T architecture uses a vertically layered structure in which planning, sequencing, and reactive skills are separated into distinct tiers. Understanding these differences required moving beyond memorising architectural diagrams and instead focusing on the design trade-offs each architecture attempts to address.
 
## Now What

I learned that many modern LLM-agent systems are built on concepts that have existed in agent research for decades. Understanding deliberative, reactive, and hybrid architectures provides a useful framework for analysing contemporary agent systems.

I now view intelligent agents from an architectural perspective rather than focusing solely on the LLM. I better appreciate how reasoning, planning, memory, and environmental interaction work together to produce intelligent behaviour.

This understanding will help me analyse and design LLM-based agents using frameworks such as LangGraph. It will also help me evaluate architectural trade-offs and make more informed design decisions when developing agent systems.
