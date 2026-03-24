---
id: chunk-009
source: Self-Learning Large Language Models.pdf
topic: Discussion
keywords: [model size effect, DPO vs instruction tuning, intrinsic vs extrinsic, Oracle-Selected effectiveness, temperature sampling]
summary: "Discusses how model size and finetuning affect self-learning: larger models always outperform smaller ones, DPO alignment produces more creative question generation making it best for intrinsic methods, while instruction tuning excels with external prompts; Oracle-Selected is most effective overall due to random topic space exploration, while Open/Induced Generation are limited by topic probability distributions."
---

## Discussion

### Model Size and Finetuning
All larger models always outperformed smaller models with the same method. tiny-llama-chat (1.1B) could not follow instructions properly despite DPO alignment. Among larger models, finetuned ones (mistral-dpo, mistral-instruct) generally outperform non-finetuned (mistral-base).

DPO alignment makes models more creative in proposing different questions because DPO shows models how to respond in different ways. This makes mistral-dpo generally best for intrinsic methods. Instruction Tuning improves instruction understanding but is mediocre at exploring the Unknown — however, with external topic supply (External Prompt), mistral-instruct achieved the highest overall SLC score (0.84).

### Intrinsic vs Extrinsic Methods
Choice depends on use-case: extrinsic methods are best for staying updated with popular/trending topics; intrinsic methods are better for comprehensive PiU discovery without external dependencies.

Open Generation and Induced Generation are less effective because they rely on model-proposed topics, which may be biased by training data probabilities. Increasing temperature during topic generation could help but requires investigation.

Oracle-Selected almost always delivers highest SLC scores due to random point generation in topic embedding space, allowing exploration of low-probability topics. Especially suitable for ensuring broad knowledge coverage including obscure topics.

External Prompt is highly effective when models struggle with self-proposed questions, but limited to trending/popular topics that may not cover all PiUs.
