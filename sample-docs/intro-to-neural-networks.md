# Introduction to Neural Networks

## What is a Neural Network?

A neural network is a computational model inspired by the structure of biological neural networks in the human brain. It consists of interconnected nodes (neurons) organized in layers that process information. Neural networks are the foundation of modern deep learning and have revolutionized fields from computer vision to natural language processing.

The basic building block is the artificial neuron, which receives inputs, applies weights to them, sums them up, and passes the result through an activation function. The output of one neuron can serve as input to another, creating complex networks capable of learning intricate patterns.

Neural networks learn by adjusting the weights of connections between neurons based on training data. This process of weight adjustment is what allows the network to improve its performance on a given task over time.

## Perceptrons and Single-Layer Networks

The perceptron, invented by Frank Rosenblatt in 1958, is the simplest form of a neural network. It consists of a single layer of output nodes connected to input nodes through weighted connections. The perceptron can learn to classify linearly separable patterns.

A perceptron works as follows:
1. Each input is multiplied by its corresponding weight
2. The weighted inputs are summed together
3. A bias term is added to the sum
4. The result is passed through an activation function (originally a step function)

The learning rule for perceptrons is straightforward: if the output is correct, do nothing. If the output is wrong, adjust the weights in the direction that would have produced the correct output. This is known as the perceptron learning rule.

However, Minsky and Papert demonstrated in 1969 that single-layer perceptrons cannot solve problems that are not linearly separable, such as the XOR problem. This limitation led to a period known as the "AI winter" where interest in neural networks declined significantly.

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

## Convolutional Neural Networks

Convolutional Neural Networks (CNNs) are specialized architectures designed primarily for processing grid-like data such as images. Inspired by the visual cortex of animals, CNNs use convolutional layers that apply learnable filters to detect local patterns like edges, textures, and shapes.

Key components of CNNs include:
- **Convolutional layers**: Apply filters that slide across the input, producing feature maps. Each filter detects a specific pattern.
- **Pooling layers**: Reduce the spatial dimensions of feature maps, typically using max pooling or average pooling. This provides translation invariance and reduces computation.
- **Fully connected layers**: Traditional neural network layers at the end that combine features for final classification or regression.

Important CNN architectures in history:
- **LeNet-5** (1998): Yann LeCun's pioneering CNN for digit recognition
- **AlexNet** (2012): Won ImageNet competition, sparked the deep learning revolution
- **VGGNet** (2014): Demonstrated that deeper networks with small filters perform better
- **ResNet** (2015): Introduced skip connections to train very deep networks (100+ layers)

CNNs have been extraordinarily successful in tasks like image classification, object detection, facial recognition, and medical image analysis. They exploit the spatial structure of images — nearby pixels are more related than distant ones — making them far more efficient than fully connected networks for visual tasks.

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
