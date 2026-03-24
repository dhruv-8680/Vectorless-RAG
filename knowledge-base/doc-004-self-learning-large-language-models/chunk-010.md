---
id: chunk-010
source: Self-Learning Large Language Models.pdf
topic: Applications and Extensions
keywords: [knowledge exchange, LLM-to-LLM learning, Direct Awareness Optimization, efficient training, AGI, multiple points of view]
summary: "Describes five applications of self-learning: efficient training by filtering known knowledge, knowledge exchange between LLMs where models teach each other only unknown knowledge, Direct Awareness Optimization to make models say 'I don't know' instead of hallucinating, learning multiple points of view via adapted DPO, and potential paths toward AGI and decision-making systems."
---

## Applications and Extensions

### Efficient Training
Using hallucination score h(x) to filter training data, focusing on more valuable content that the model does not yet know.

### Knowledge Exchanging LLMs
Two or more LLMs exchange knowledge without external engagement. Model M1 identifies PiUs (h1(x) > LIMIT), Model M2 checks h2(x) < LIMIT. If so, M2 provides learning cases related to x for M1's self-learning loop. Models exchange only unknown knowledge — efficient knowledge sharing.

### Direct Awareness Optimization
Using model hidden states to detect hallucinations, then adapting DPO to make the model answer "I don't know" instead of hallucinating. The goal is making the model aware of its own hidden states as triggers for admitting ignorance rather than associating specific concepts with "I don't know."

### Learning Multiple Points of View
By adapting DPO, the model can learn different perspectives on a topic. Training data constructed so a prompt has multiple responses with similar preferability scores, with prompt context associated with particular stances.

### Decision Making and AGI
Self-learning models that automatically learn about latest trends are useful for decision-making systems (business, trading). Self-Learning is a step towards AGI. Making a model aware of what it knows may lead toward sentient, conscious AI.

### Possible Issues
- Knowledge source selection (search engines, wikis, document databases, human experts, other LLMs)
- Bias/incorrectness in retrieved documents — solvable with a Curator (classifier + scorer models)
- Catastrophic forgetting risk in multiple training cycles — existing solutions offer promising starting points
