---
id: chunk-002
source: intro-to-neural-networks.md
topic: Perceptrons and Single-Layer Networks
keywords: [perceptron, Rosenblatt, linear separability, XOR problem, AI winter]
summary: "Describes the perceptron as the simplest neural network, its learning rule, and the linear separability limitation that caused the AI winter."
---

## Perceptrons and Single-Layer Networks

The perceptron, invented by Frank Rosenblatt in 1958, is the simplest form of a neural network. It consists of a single layer of output nodes connected to input nodes through weighted connections. The perceptron can learn to classify linearly separable patterns.

A perceptron works as follows:
1. Each input is multiplied by its corresponding weight
2. The weighted inputs are summed together
3. A bias term is added to the sum
4. The result is passed through an activation function (originally a step function)

The learning rule for perceptrons is straightforward: if the output is correct, do nothing. If the output is wrong, adjust the weights in the direction that would have produced the correct output. This is known as the perceptron learning rule.

However, Minsky and Papert demonstrated in 1969 that single-layer perceptrons cannot solve problems that are not linearly separable, such as the XOR problem. This limitation led to a period known as the "AI winter" where interest in neural networks declined significantly.
