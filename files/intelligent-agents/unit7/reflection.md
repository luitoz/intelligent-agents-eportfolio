# Unit 7 Reflection

## what

The unit presents the evolution of NLP through symbolic, statistical, and neural approaches. Statistical NLP uses probabilistic methods to learn language patterns from data. One common task is predicting the next word in a sequence based on the words that precede it.

An important milestone in the transition toward neural NLP was Google's Word2Vec model, which uses neural networks to learn vector representations of words from large text corpora. These representations capture semantic similarities and relationships between words and are useful for tasks such as vocabulary expansion, document classification, and semantic analysis.

However, NLP involves more than learning word associations. Systems must also understand the grammatical rules of language (syntax) and, ultimately, the meanings conveyed by words and sentences (semantics). To analyze sentence structure, NLP systems often represent sentences as trees that encode grammatical relationships. Two common representations are constituency trees, which show how a sentence is organized into phrases, and dependency trees, which show how words grammatically depend on one another. These structures provide useful foundations for more advanced tasks such as information extraction, argument mining, and semantic interpretation.

## So What

This unit showed that NLP has evolved from manually crafted linguistic rules to data-driven statistical methods and, more recently, neural approaches that learn rich language representations from large datasets. Although the availability of large-scale training data and deep learning models has reduced the reliance on purely rule-based systems, symbolic techniques remain relevant in many NLP applications. Their low data requirements, interpretability, and ease of debugging make them particularly valuable in domains where transparency and reliability are important.

Consequently, hybrid approaches that combine symbolic and neural NLP often provide an effective compromise. In such systems, machine learning or large language models can assist in generating, refining, or applying rules, while the symbolic components contribute transparency, controllability, and explainability. By leveraging the strengths of both paradigms, hybrid NLP systems can achieve greater robustness and practical usefulness than either approach alone in many real-world scenarios (Panchendrarajan, 2024).

I found this topic particularly interesting because it illustrates the progression of NLP from simple statistical techniques to more sophisticated neural models. Learning how vector representations can capture semantic similarities between words helped me appreciate the foundations of modern language models. At the same time, studying syntactic structures reinforced the complexity of human language and the challenges involved in enabling computers to understand it accurately.
 
## Now What

From this unit, I learned that statistical and neural methods can discover meaningful linguistic patterns from large corpora, while syntactic representations provide structured information that supports deeper language understanding. I also learned that tasks such as information extraction and semantic analysis rely not only on word meanings but also on grammatical relationships between words.

This knowledge has changed my perception of NLP systems. Previously, I viewed language processing mainly as a task of recognizing words and patterns. I now understand that successful NLP applications depend on integrating multiple levels of analysis, including semantics and syntax, to correctly interpret language and context.

In the future, I can apply these concepts when studying or developing AI systems that process natural language. Understanding word embeddings, syntactic parsing, and semantic analysis will help me evaluate modern language models and design solutions for tasks such as document classification, information extraction, question answering, and intelligent agents that interact with users through natural language.
