---
id: chunk-007
source: intro-to-neural-networks.md
topic: The Transformer Architecture
keywords: [transformer, self-attention, multi-head attention, encoder-decoder, large language model]
summary: "Introduces the Transformer architecture that replaced RNNs by using self-attention to process all sequence positions in parallel, forming the basis for GPT, BERT, and other large language models."
---

## The Transformer Architecture

The Transformer, introduced in the paper "Attention Is All You Need" (Vaswani et al., 2017), has largely replaced RNNs for sequence modeling tasks. Instead of processing sequences step by step, Transformers use self-attention mechanisms to process all positions simultaneously.

**Self-attention** computes relationships between all pairs of positions in a sequence:
1. Each position produces a Query (Q), Key (K), and Value (V) vector
2. Attention scores are computed as the dot product of Q and K
3. Scores are scaled and passed through softmax to get attention weights
4. The output is a weighted sum of V vectors

**Multi-head attention** runs multiple attention operations in parallel, allowing the model to attend to information from different representation subspaces.

The Transformer architecture consists of:
- **Encoder**: Processes the input sequence using self-attention and feedforward layers
- **Decoder**: Generates the output sequence using masked self-attention, cross-attention with the encoder, and feedforward layers

Transformers are the basis for modern large language models like GPT, BERT, and Claude. They scale well with data and compute, which has driven the scaling laws observed in recent AI research.
