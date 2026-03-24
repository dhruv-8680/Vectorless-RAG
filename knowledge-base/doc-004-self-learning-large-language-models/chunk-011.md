---
id: chunk-011
source: Self-Learning Large Language Models.pdf
topic: Conclusion and Limitations
keywords: [conclusion, limitations, confident incorrect knowledge, long-term self-learning, data poisoning]
summary: "Concludes that Oracle-Selected and External Prompt are most effective for self-learning, finetuned 7B models succeed while small/non-finetuned models struggle, and identifies two key limitations: models may be confidently wrong about poisoned/repeated incorrect training data, and long-term multi-cycle self-learning with catastrophic forgetting prevention needs further study."
---

## Conclusion

The concepts of The Known and The Unknown can identify knowledge an LLM already knows (PiKs) and does not know yet (PiUs). One extrinsic and three intrinsic methods for PiU identification enable Self-Learning LLMs. The Self-Learning Capability (SLC) Score gauges aptitude for self-learning.

Key findings:
- Oracle-Selected and External Prompt are especially effective for self-learning
- Small models and non-finetuned models struggle to learn independently
- Finetuning and alignment improve Self-Learning Capability by enabling instruction understanding and creative question generation

## Limitations

1. **Model's confidence on incorrect knowledge**: The paper assumes pretrained models were subjected to correct knowledge, so response consistency correlates with factuality. However, if incorrect knowledge was repeated in training data (accidentally or through deliberate poisoning), models may become confidently consistent in producing incorrect information. Future direction: integrating a reference-based truthfulness checker like FactScore in the self-learning loop for self-correction.

2. **Long-term Self-Learning**: The paper proves effectiveness of PiU identification methods and feasibility of Self-Learning. A deeper study into extensive cycles of Self-Learning is needed, especially to find the best method for preventing catastrophic forgetting.
