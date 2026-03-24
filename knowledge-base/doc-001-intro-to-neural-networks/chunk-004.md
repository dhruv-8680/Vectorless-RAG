---
id: chunk-004
source: intro-to-neural-networks.md
topic: Convolutional Neural Networks
keywords: [CNN, convolutional layer, pooling, image classification, ResNet, AlexNet]
summary: "Covers CNN architecture with convolutional, pooling, and fully connected layers, plus landmark models from LeNet-5 to ResNet that drove the deep learning revolution in computer vision."
---

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
