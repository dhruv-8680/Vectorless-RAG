---
id: chunk-006
source: Self-Learning Large Language Models.pdf
topic: Self-Learning LLM Framework
keywords: [self-questioning, meaningfulness filter, knowledge searching, model training, continual learning loop, LoRA, DPO trainer]
summary: "Describes the four components of the Self-Learning LLM framework: Self-Questioning (iterative PiU identification producing questions with/without hallucination), Meaningfulness Filter (removing nonsensical PiUs), Knowledge Searching (querying external sources for answers to hallucinated questions), and Model Training (using LoRA and DPO to absorb new knowledge, converting PiUs to PiKs)."
---

## Self-Learning LLM Framework

Self-Learning is a process where the LLM identifies its own PiUs, searches for knowledge related to these PiUs, and trains itself on collected data. It incorporates Self-Questioning, Knowledge Searching, and Model Training in a continuous loop.

### Self-Questioning
Performed through topic generation (or collection), question generation, and hallucination scoring. Repeated for N iterations. Primary output: a list of questions with hallucination (QH ⊂ Unknown) and questions with no hallucination (QNH ⊂ Known). Uses NLI-based SelfCheckGPT for scoring; a question is categorized into QH if average hallucination score > 0.5.

### Meaningfulness Filter
An optional component before Knowledge Searching. Goals: (1) remove obviously meaningless PiUs like "How fast cats fly on Mars?"; (2) implement goals and policy of self-learning, e.g., consider only PiUs relevant to a given domain; (3) overcome limitations of hallucination score, e.g., when the LLM responds "I do not know" and h(x) ≈ 0.

### Knowledge Searching
Queries an external source to collect knowledge that can answer QH in order to build the training dataset Dtrain. Can be implemented inside Self-Questioning or kept separate for additional processing (document ranking and filtering).

### Model Training
The model is trained on Dtrain to absorb the knowledge for answering QH. Once training is done, PiUs should become PiKs, increasing Known regions and decreasing Unknown regions. The demonstration used LoRA (Hu et al., 2022) and the DPO trainer, training for 10 epochs with learning rate 3e-5. After training, average hallucination score on QH dropped from 0.59 to 0.48.
