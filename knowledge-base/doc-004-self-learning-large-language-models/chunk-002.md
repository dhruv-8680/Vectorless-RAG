---
id: chunk-002
source: Self-Learning Large Language Models.pdf
topic: Related Work
keywords: [hallucination detection, SelfCheckGPT, continual learning, catastrophic forgetting, RAG]
summary: "Reviews prior work on hallucination causes and detection methods (SelfCheckGPT, SAPLMA, FactScore), RAG as an alternative that avoids hallucination without updating model knowledge, and continual learning approaches that address catastrophic forgetting when sequentially training on domain-specific datasets."
---

## Related Work

Hallucination in the context of LLM is the problem of nonsensical or unfaithful information produced by a generative model. Some works have studied the causes of hallucination (Kandpal et al., 2023; Lee et al., 2022; Onoe et al., 2022), as well as the detection methods (Lin et al., 2022; Min et al., 2023; Azaria and Mitchell, 2023; Manakul et al., 2023; Cao et al., 2023; Yin et al., 2023). Some solutions for overcoming hallucination are proposed in (Ji et al., 2023b; Luo et al., 2023; Li et al., 2023; Ji et al., 2023a; Liu and Sajda, 2023; Liang et al., 2024; Tian et al., 2024). Meanwhile, in Retrieval Augmented Generation (RAG) (Lewis et al., 2020), hallucination is avoided by supplying the prompt with some context retrieved from an outside source, allowing more factual generation without updating the model's knowledge.

Continual Learning is a training paradigm where the model is subjected to various tasks sequentially; in the context of LLM, the tasks typically comprise domain-specific datasets (Jang et al., 2022; Jin et al., 2022; Ke et al., 2023). One challenge is preventing catastrophic forgetting, in which the model loses knowledge from previous tasks (McCloskey and Cohen, 1989; Ratcliff, 1990). Solutions for adding or editing knowledge while avoiding catastrophic forgetting have been proposed (Kirkpatrick et al., 2017; Zhu et al., 2020; Sinitsin et al., 2020; Ke et al., 2021; Mitchell et al., 2022).
