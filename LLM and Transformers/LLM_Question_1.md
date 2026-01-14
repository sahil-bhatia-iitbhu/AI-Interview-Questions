Authored by Sahil Bhatia. You can follow him on [LinkedIn](www.linkedin.com/in/sahilbhatiaiitbhu) for the latest LLM, RAG and Agent updates

## Relevance of Positional Embedding in Transformers

𝐐𝐮𝐞𝐬𝐭𝐢𝐨𝐧: "Let’s talk architecture. CNNs and RNNs don't require explicit positional embeddings to understand the order of data. Why did the Transformer suddenly make them a requirement?"

𝐂𝐨𝐦𝐦𝐨𝐧 𝐀𝐧𝐬𝐰𝐞𝐫: "Well, RNNs process data sequentially, one step at a time, so they inherently know the order. CNNs use filters that slide over local patches, so they capture spatial relationships. Transformers, however, use Self-Attention, which processes all tokens in a sequence simultaneously. Without embeddings, the model would treat the sentence 'The dog bit the man' exactly the same as 'The man bit the dog.' It would just be a 'bag of words.'"

𝐅𝐨𝐥𝐥𝐨𝐰-𝐔𝐩 𝐐𝐮𝐞𝐬𝐭𝐢𝐨𝐧: "That’s a solid start. You’ve identified that Self-Attention is *permutation invariant*. But let's dig deeper. If I removed the positional embeddings from a Transformer, would the 'Attention' mechanism still work technically?"

𝐀𝐧𝐬𝐰𝐞𝐫: "Technically, yes, the math still checks out—you’d still get an output. But you lose the 'topology' of the data. In an RNN, the hidden state at t=5 is physically dependent on t=4. There is a *structural bias* for order.

In a Transformer, the 'energy' or attention score between two tokens is calculated using the dot product of their Query and Key vectors:

$$Score = Q \cdot K^T$$

Notice there is no index i or j in that formula. If you swap the positions of two words, their dot product remains identical. We use positional embeddings to inject that 'index' back into the word vector so the model can distinguish between a word at the start of a sentence versus the end."

𝐅𝐨𝐥𝐥𝐨𝐰-𝐔𝐩 𝐐𝐮𝐞𝐬𝐭𝐢𝐨𝐧: "Great point on the dot product. Now, follow-up: why don't we just concatenate the position (1, 2, 3...) to the word vector? Why do we use complex sine and cosine functions or learned embeddings?"

𝐘𝐨𝐮: "Simple integers don't scale well. If you train on sequences of length 50 and then encounter a sequence of length 500, the integers get huge, potentially overpowering the semantic values in the embedding.

By using periodic functions like Sine and Cosine, we achieve two things:
- Bounded Range: The values stay between -1 and 1.
- Relative Relationships: Because of trigonometric identities, the model can learn that the relationship between position (x) and (x + k) is a linear function. This allows the model to generalize to sequence lengths it hasn't even seen during training."