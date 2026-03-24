---
id: chunk-008
source: Self-Learning Large Language Models.pdf
topic: Experiments and Results
keywords: [Mistral-7B, TinyLlama, DPO alignment, instruction tuning, experimental setup, SLC scores]
summary: "Experiments on four models (mistral-dpo, mistral-instruct, mistral-base, tiny-llama-chat) show that 7B finetuned/aligned Mistral models achieve strong self-learning capability, with Oracle-Selected achieving the highest SLC scores (0.75 for mistral-dpo) while the smaller 1.1B TinyLlama struggled to follow instructions effectively."
---

## Experiments and Results

### Setup
Python 3.9 on Ubuntu 20.04 with 8 CPU cores, 45GB RAM, and one NVIDIA RTX A6000 48GB GPU.

### Models Tested
| Model | Size | Finetuning |
|-------|------|------------|
| mistral-dpo (Intel/neural-chat-7b-v3-3) | 7B | DPO aligned |
| mistral-instruct (Mistral-7B-Instruct-v0.2) | 7B | Instruction tuned |
| mistral-base (Mistral-7B-v0.1) | 7B | None |
| tiny-llama-chat (TinyLlama-1.1B-Chat-v1.0) | 1.1B | Vanilla + DPO |

### Data Configuration
- Open Generation: N=100, 100 questions
- Induced Generation: N=20, 120 questions (6 per iteration)
- Oracle-Selected: N=20, 20 questions
- External Prompt: N=2, 37 questions (variable API response length)

### Key Results (SLC Scores)
- mistral-dpo: Open=0.57, Induced=0.59, Oracle=0.75, External=0.74
- mistral-instruct: Open=0.35, Induced=0.25, Oracle=0.65, External=0.84
- mistral-base: Open=0.31, Induced=0.33, Oracle=0.43, External=0.37
- tiny-llama-chat: Open=0.08, Induced=0.17, Oracle=0.36, External=0.22
