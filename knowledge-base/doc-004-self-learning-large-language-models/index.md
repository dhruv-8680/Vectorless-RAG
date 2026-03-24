# Self-Learning Large Language Models — Index

## Abstract and Introduction
- **chunk-001.md** | Keywords: self-learning LLM, hallucination, Points in the Unknown, PiU, knowledge gap | "Proposes a self-learning LLM framework where models independently identify unknown knowledge through hallucination self-assessment using Points in the Unknown (PiUs), enabling a continual learning loop that reduces hallucination by focusing exclusively on knowledge gaps."

## Related Work
- **chunk-002.md** | Keywords: hallucination detection, SelfCheckGPT, continual learning, catastrophic forgetting, RAG | "Reviews prior work on hallucination causes and detection methods, RAG as an alternative, and continual learning approaches that address catastrophic forgetting."

## Why Self-Learning is Needed
- **chunk-003.md** | Keywords: hallucination problem, finetuning inefficiency, knowledge gaps, unknown knowledge identification | "Argues that traditional finetuning is inefficient because it often retrains knowledge the model already knows, wasting computing resources."

## The Known, The Unknown, and PiU
- **chunk-004.md** | Keywords: Point in the Unknown, PiU, PiK, hallucination score, SelfCheckGPT, knowledge space, LIMIT threshold | "Formally defines The Known and The Unknown as regions in human knowledge space using SelfCheckGPT's hallucination score h(x) with a threshold of 0.5."

## Methods for PiU Identification
- **chunk-005.md** | Keywords: External Prompt, Open Generation, Induced Generation, Oracle-Selected, extrinsic method, intrinsic method, 5W1H | "Describes four methods for identifying PiUs: one extrinsic (External Prompt) and three intrinsic (Open Generation, Induced Generation, Oracle-Selected)."

## Self-Learning LLM Framework
- **chunk-006.md** | Keywords: self-questioning, meaningfulness filter, knowledge searching, model training, continual learning loop, LoRA, DPO trainer | "Describes the four components of the Self-Learning LLM framework: Self-Questioning, Meaningfulness Filter, Knowledge Searching, and Model Training using LoRA and DPO."

## Self-Learning Evaluation Metrics
- **chunk-007.md** | Keywords: Curiosity Score, Knowledge-Limit Awareness, SLC Score, brevity coefficient, HDBSCAN | "Introduces three metrics: Curiosity Score (question diversity), Knowledge-Limit Awareness Score (hallucination ratio), and SLC Score (average of both)."

## Experiments and Results
- **chunk-008.md** | Keywords: Mistral-7B, TinyLlama, DPO alignment, instruction tuning, experimental setup, SLC scores | "Experiments on four models show 7B finetuned Mistral models achieve strong self-learning, with Oracle-Selected achieving highest SLC (0.75 for mistral-dpo)."

## Discussion
- **chunk-009.md** | Keywords: model size effect, DPO vs instruction tuning, intrinsic vs extrinsic, Oracle-Selected effectiveness, temperature sampling | "Discusses how model size, finetuning method, and PiU identification method affect self-learning capability."

## Applications and Extensions
- **chunk-010.md** | Keywords: knowledge exchange, LLM-to-LLM learning, Direct Awareness Optimization, efficient training, AGI, multiple points of view | "Describes five applications: efficient training, LLM knowledge exchange, Direct Awareness Optimization, learning multiple PoVs, and paths toward AGI."

## Conclusion and Limitations
- **chunk-011.md** | Keywords: conclusion, limitations, confident incorrect knowledge, long-term self-learning, data poisoning | "Concludes Oracle-Selected and External Prompt are most effective; identifies limitations around data poisoning confidence and long-term catastrophic forgetting."
