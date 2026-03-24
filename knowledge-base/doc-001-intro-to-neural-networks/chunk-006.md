---
id: chunk-006
source: intro-to-neural-networks.md
topic: Training Neural Networks
keywords: [SGD, Adam optimizer, dropout, regularization, batch normalization, learning rate]
summary: "Details the practical techniques for training neural networks including SGD and Adam optimizers, regularization methods like dropout and batch normalization, and learning rate scheduling."
---

## Training Neural Networks

Training a neural network involves finding the set of weights that minimizes a loss function over the training data. This is typically done using variants of gradient descent.

**Stochastic Gradient Descent (SGD)**: Instead of computing the gradient over the entire dataset (batch gradient descent), SGD updates weights using a single random sample or a small mini-batch at each step. This is faster and often helps escape local minima.

**Common optimizers**:
- **Momentum**: Accumulates gradients from previous steps to accelerate learning in consistent directions
- **Adam** (Adaptive Moment Estimation): Combines momentum with per-parameter adaptive learning rates. Most widely used optimizer in practice.
- **RMSprop**: Adapts learning rates based on recent gradient magnitudes

**Regularization techniques** to prevent overfitting:
- **Dropout**: Randomly sets a fraction of neuron outputs to zero during training, forcing the network to learn redundant representations
- **L1/L2 regularization**: Adds a penalty term to the loss function based on weight magnitudes
- **Batch normalization**: Normalizes layer inputs, stabilizing training and allowing higher learning rates
- **Early stopping**: Monitors validation loss and stops training when it starts increasing

**Learning rate scheduling**: Starting with a high learning rate and gradually reducing it often leads to better convergence. Common schedules include step decay, cosine annealing, and warm-up strategies.
