---
id: chunk-007
source: Self-Learning Large Language Models.pdf
topic: Self-Learning Evaluation Metrics
keywords: [Curiosity Score, Knowledge-Limit Awareness, SLC Score, brevity coefficient, HDBSCAN]
summary: "Introduces three metrics for evaluating self-learning capability: Curiosity Score (measures diversity of generated questions using HDBSCAN clustering), Knowledge-Limit Awareness Score (ratio of questions the model cannot answer without hallucinating), and Self-Learning Capability (SLC) Score (average of the two), all penalized by a brevity coefficient for instruction-following quality."
---

## Metrics for Self-Learning Capability

Self-Learning requires a pretrained model with sufficient language understanding and instruction-following ability. Three metrics evaluate self-learning capability:

### Brevity Coefficient
Penalizes evaluation when the brevity constraint is violated (e.g., model fails to formulate one concise question). Uses ideal_len = 100 characters; decreases linearly when average text length deviates beyond [50, 150].

### Curiosity Score
Measures how likely a model explores different questions. High score = model tends to ask unique, different questions across Self-Questioning iterations, exploring more Unknown regions.
- Cur = brev × (#Qunique / #Q)
- #Qunique determined by HDBSCAN clustering on question embeddings (counting clusters + outliers)
- Question embeddings from all-MiniLM-L12-v2 (Sentence Transformers)

### Knowledge-Limit Awareness Score
Indicates how likely a model generates questions it cannot answer without hallucination — awareness of its own knowledge limitation.
- Kaw = #QH / #Q

### Self-Learning Capability (SLC) Score
Simple average: SLC = (Cur + Kaw) / 2
