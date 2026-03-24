---
id: chunk-005
source: Self-Learning Large Language Models.pdf
topic: Methods for PiU Identification
keywords: [External Prompt, Open Generation, Induced Generation, Oracle-Selected, extrinsic method, intrinsic method, 5W1H]
summary: "Describes four methods for identifying Points in the Unknown: one extrinsic (External Prompt using trending topic APIs) and three intrinsic (Open Generation where the model proposes its own topics, Induced Generation using 5W+1H question words, and Oracle-Selected using random sampling in topic embedding space)."
---

## Methods for Identification of PiUs

Identification of PiUs is done by evaluating the model's hallucination scores h(x) on questions-prompts x. Questions can come from outside (extrinsic) or be generated internally (intrinsic) in a bicameral-mind manner.

### External Prompt (extrinsic)
Utilizes an external API to collect trending topics as inspiration for formulating concrete questions. Every item returned by the API is a list of related phrases treated as a single topic. The model generates specific questions relevant to each topic, then answers them for hallucination evaluation. Unlike prior approaches requiring manual curation, this allows continuous self-learning as long as the external API is available, though the tested space is limited to trending topics.

### Open Generation (intrinsic)
The oracle asks the model to propose some topics to learn about, then asks the model to formulate one question to which it believes it does not know the answer. The model then answers the question for hallucination evaluation. No external entity is required.

### Induced Generation (intrinsic)
Based on Five Ws and How (what, who, why, where, when, how). The oracle asks the model to propose topics, then formulates six questions per topic using each question word. This results in broader coverage of the topic space. No external inspiration needed.

### Oracle-Selected (intrinsic)
Constructs a topic embedding space containing all candidate topics in vectorial form. The oracle randomly selects a point in the embedding space and samples nearest neighbors to get oracle-selected topics. The model then formulates and answers questions based on these topics. The randomness allows exploring topics that would normally have low probability of being proposed by the model itself.
