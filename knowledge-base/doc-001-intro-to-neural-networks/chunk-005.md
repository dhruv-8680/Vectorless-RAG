---
id: chunk-005
source: intro-to-neural-networks.md
topic: Recurrent Neural Networks
keywords: [RNN, LSTM, GRU, vanishing gradient, sequential data, hidden state]
summary: "Explains how RNNs process sequential data using hidden state as memory, and how LSTM and GRU gating mechanisms solve the vanishing gradient problem for long-range dependencies."
---

## Recurrent Neural Networks

Recurrent Neural Networks (RNNs) are designed for sequential data where the order of inputs matters. Unlike feedforward networks, RNNs have connections that form cycles, allowing them to maintain a hidden state that acts as a form of memory.

At each time step, an RNN:
1. Takes the current input and the previous hidden state
2. Produces a new hidden state and an output
3. The hidden state carries information from previous time steps

This makes RNNs suitable for tasks like language modeling, speech recognition, time series prediction, and machine translation.

However, vanilla RNNs suffer from the vanishing gradient problem: during backpropagation through time, gradients can shrink exponentially, making it difficult to learn long-range dependencies. If a relevant piece of information appeared many time steps ago, the RNN may fail to use it.

**Long Short-Term Memory (LSTM)** networks, introduced by Hochreiter and Schmidhuber in 1997, solve this problem using a gating mechanism. LSTMs have three gates:
- **Forget gate**: Decides what information to discard from the cell state
- **Input gate**: Decides what new information to store in the cell state
- **Output gate**: Decides what to output based on the cell state

**Gated Recurrent Units (GRUs)**, proposed by Cho et al. in 2014, are a simplified variant with only two gates (reset and update), offering similar performance with fewer parameters.
