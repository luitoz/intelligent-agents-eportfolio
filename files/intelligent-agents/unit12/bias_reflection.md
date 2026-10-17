# Bias Reflection

## What

The [Multi-Agent Academic Investigator](https://github.com/luitoz/multi-agent-academic-investigator) includes a specialized component, the Evidence Analysis Agent, which evaluates the reliability of retrieved evidence. This agent is intentionally designed as a deterministic, rule-based agent that assesses reliability using only bibliometric indicators, such as publication recency and citation/reference counts. 

Currently, the retrieval agent gathers academic literature exclusively from a single source, the Semantic Scholar API. 

## So what

Although the simple Evidence Analysis Agent was useful for achieving an MVP, its reliance on bibliometric indicators introduces potential bias in the evaluation of evidence.

At the paper level, a publication may score highly on metrics such as citation count or recency while still containing methodological weaknesses, conflicts of interest, or unsupported conclusions. As a result, bibliometric quality does not necessarily imply scientific reliability.

At the evidence-set level, bias may arise from the collection of papers retrieved. The retrieved literature may be disproportionately associated with a particular author, institution, country, or research community. Similarly, the evidence set may overrepresent a specific viewpoint while underrepresenting competing perspectives, leading to an unbalanced assessment of an academic claim.

An additional source of bias stems from the use of a single academic database, the Semantic Scholar API. Because research output is not evenly distributed across countries, institutions, languages, or disciplines, papers from well-funded universities, English-language venues, and popular research areas are often more visible than work from underrepresented communities. Consequently, the retrieval agent may overlook relevant but less visible evidence.

## Now what

This reflection helped me recognize that assessing evidence quality requires more than evaluating bibliometric indicators. I learned that bias can emerge from individual papers, the overall evidence set, and even the academic databases used for retrieval.

As a result, I would improve the system by incorporating additional reliability measures, such as assessing research methodology, identifying potential conflicts of interest, and evaluating the diversity of perspectives represented in the evidence set. I would also reduce dependence on a single source by retrieving papers from multiple academic databases.

In future applications, I will pay greater attention to how evidence is selected and evaluated, ensuring that AI systems consider not only the quality of individual sources but also the representativeness and balance of the overall body of evidence. This would help produce more robust, transparent, and less biased conclusions.
