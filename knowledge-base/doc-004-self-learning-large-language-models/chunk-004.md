---
id: chunk-004
source: Self-Learning Large Language Models.pdf
topic: The Known, The Unknown, and PiU
keywords: [Point in the Unknown, PiU, PiK, hallucination score, SelfCheckGPT, knowledge space, LIMIT threshold]
summary: "Formally defines The Known and The Unknown as regions in human knowledge space where an LLM does or does not hallucinate, using SelfCheckGPT's hallucination score h(x) with a threshold of 0.5 — points scoring below are Points in the Known (PiKs), above are Points in the Unknown (PiUs) representing knowledge gaps to fill."
---

## The Concepts of The Known and The Unknown, Point in the Unknown (PiU)

Human knowledge is an abstract space formed by vectorial knowledge representations; each point in the space represents an atomic piece of knowledge. The Known refers to an area in the human knowledge space where our LLM does not hallucinate, i.e., it possesses the knowledge related to this region. Each point in such an area is a Point in the Known (PiK). The Unknown refers to an area where our LLM hallucinates; each point is called Point in the Unknown (PiU) — knowledge that the LLM lacks, which we want the model to identify and acquire.

Finding the boundaries between The Known and The Unknown is non-trivial, but hallucination detection methods offer practical scoring systems. The paper uses SelfCheckGPT (Manakul et al., 2023), a sampling-based hallucination detection method that checks consistency (variance) of multiple generated responses to a given prompt. It outputs a hallucination score h(x) ∈ [0, 1], where h(x) = 1 indicates entirely hallucinated and h(x) = 0 means no hallucination.

Using LIMIT = 0.5 as the threshold:
- Known = {x : h(x) < LIMIT ; x ∈ HKS}
- Unknown = {x : h(x) ≥ LIMIT ; x ∈ HKS}

where HKS is the human knowledge space. Known ∩ Unknown = ∅ and Known ∪ Unknown = HKS.
