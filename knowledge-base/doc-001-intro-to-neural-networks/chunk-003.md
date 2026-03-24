---
id: chunk-003
source: intro-to-neural-networks.md
topic: Multi-Layer Perceptrons and Backpropagation
keywords: [backpropagation, multi-layer perceptron, gradient descent, activation function, ReLU, sigmoid]
summary: "Explains how multi-layer perceptrons and the backpropagation algorithm overcome single-layer limitations by using hidden layers and the chain rule to train deep networks."
---

## Multi-Layer Perceptrons and Backpropagation

The limitations of single-layer perceptrons were overcome with the development of multi-layer perceptrons (MLPs) and the backpropagation algorithm. An MLP has one or more hidden layers between the input and output layers, allowing it to learn non-linear decision boundaries.

Backpropagation, popularized by Rumelhart, Hinton, and Williams in 1986, is the algorithm used to train MLPs. It works by:
1. Performing a forward pass: input data flows through the network to produce an output
2. Computing the error between the predicted output and the actual target
3. Propagating the error backward through the network
4. Updating weights using gradient descent to minimize the error

The key insight of backpropagation is the chain rule of calculus, which allows the gradient of the error to be computed with respect to each weight in the network, regardless of how many layers deep it is. This made training deep networks feasible.

Common activation functions used in MLPs include:
- **Sigmoid**: Maps values to (0, 1), useful for probability outputs
- **Tanh**: Maps values to (-1, 1), zero-centered which helps with convergence
- **ReLU** (Rectified Linear Unit): max(0, x), computationally efficient and avoids vanishing gradient problem
