---
id: chunk-001
source: Self-Learning Large Language Models.pdf
topic: Abstract and Introduction
keywords: [self-learning LLM, hallucination, Points in the Unknown, PiU, knowledge gap]
summary: "Proposes a self-learning LLM framework where models independently identify unknown knowledge through hallucination self-assessment using Points in the Unknown (PiUs), enabling a continual learning loop that reduces hallucination by focusing exclusively on knowledge gaps."
---

## Abstract

We address the main problem of self-learning LLM: the question of what to learn. We propose a self-learning LLM framework that enables an LLM to independently learn previously unknown knowledge through self-assessment of their own hallucinations. Using the hallucination score, we introduce a new concept of Points in The Unknown (PiUs), along with one extrinsic and three intrinsic methods for automatic PiUs identification. It facilitates the creation of a self-learning loop that focuses exclusively on the knowledge gap in Points in The Unknown, resulting in a reduced hallucination score. We also developed evaluation metrics for gauging an LLM's self-learning capability. Our experiments revealed that 7B-Mistral models that have been finetuned or aligned are capable of self-learning considerably well. Our self-learning concept allows more efficient LLM updates and opens new perspectives for knowledge exchange. It may also increase public trust in AI.

## Introduction

Commonly, Large Language Models (LLMs) are pre-trained on large textual corpora and then finetuned using additional data to be better adjusted to a given policy or domain. Simultaneously, other quasi-learning methods have been developed, which are based on additional knowledge provided to the model directly in prompts, especially Retrieval Augmented Generation (RAG). In this paper, we explore a different concept: Self-learning LLMs, i.e., persistent acquisition of new knowledge by the model without data provision. Such a process requires several steps: (1) identification of what knowledge to learn, (2) meaningfulness filter to validate whether identified knowledge is worth and reasonable to learn, (3) searching for and gathering new relevant data, and (4) continual model training.

The paper introduces Points in the Unknown (PiUs) — a novel concept for identifying unknown knowledge — and places this in a self-learning loop. Contributions include: definition of PiUs using hallucination score; one extrinsic and three intrinsic methods to identify PiUs; introduction of Meaningfulness Filter; metrics to gauge self-learning capability (Curiosity Score, Knowledge-Limit Awareness Score, Self-Learning Capability Score); design and experimental validation of the self-learning LLM.
