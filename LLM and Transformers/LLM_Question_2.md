Authored by Sahil Bhatia. You can follow him on [LinkedIn](www.linkedin.com/in/sahilbhatiaiitbhu) for the latest LLM, RAG and Agent updates
Repo: https://github.com/sahil-bhatia-iitbhu/AI-Interview-Questions

### 🚀 INTERVIEW - How LLMs Actually Process Your Queries

**Interviewer:** Let's dive into something that happens every time we interact with an LLM—inference. Walk me through the mechanics. What actually happens when you hit send?

**Candidate:** It's essentially a four-stage pipeline. First is **tokenization**: the input text is broken into tokens, and each token is mapped to an ID in the model’s vocabulary.

**Interviewer:** So "hello world" becomes a sequence of numbers the model understands?

**Candidate:** Exactly. Then comes the **prefill phase**. The embedding layer converts those token IDs into dense vectors, and the decoder layers process all these embeddings in parallel to compute keys and values, building the context for generation.

**Interviewer:** Parallel context building—so that’s where efficiency starts to kick in.

**Candidate:** Right. Once context is set, we move to the **decoding phase**. The model now generates output tokens one at a time, autoregressively, using previously generated tokens and cached states, until a stopping condition is met.

**Interviewer:** And that final piece?

**Candidate:** **Detokenization**. The generated token IDs are converted back into human-readable text, which is what you finally see as the model’s response.

**Interviewer:** So in summary: tokenize, prefill, decode, detokenize.

**Candidate:** Yes, and understanding this pipeline explains why batching helps, why context length is critical, and why inference latency is usually dominated by the decoding phase.

**#LLM #AI #MachineLearning #LargeLanguageModels #Inference #DeepLearning #AIEngineering #TechInterview #NeuralNetworks #ArtificialIntelligence**