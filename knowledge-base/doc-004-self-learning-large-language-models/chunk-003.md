---
id: chunk-003
source: Self-Learning Large Language Models.pdf
topic: Why Self-Learning is Needed
keywords: [hallucination problem, finetuning inefficiency, knowledge gaps, unknown knowledge identification]
summary: "Argues that traditional finetuning is inefficient because it often retrains knowledge the model already knows, wasting computing resources, and that identifying what the model knows vs. does not know is essential to focus finetuning only on unknown knowledge."
---

## Why Self-Learning is Needed

Hallucination is a serious problem that hinders many LLM applications. One of its main reasons is the model's lack of knowledge on a given topic. This problem is typically overcome by finetuning, i.e., additional learning using new data. Simultaneously, determining what the model already knows and what it does not know yet is very difficult, especially if there is limited information on the model's past training data. Because of this, finetuning is often a very inefficient process. If finetuning focuses on knowledge already acquired by the model, it does not solve the hallucination problem. Then, we needlessly waste a lot of computing resources by merely repeating known knowledge. Therefore, it is essential to identify the knowledge known and unknown to the model and, in the finetuning process, concentrate only on the unknown.
