# Attention and Transformers

https://jalammar.github.io/illustrated-transformer/ 

https://towardsdatascience.com/transformers-explained-visually-not-just-how-but-why-they-work-so-well-d840bd61a9d3 

https://towardsdatascience.com/transformers-explained-visually-part-2-how-it-works-step-by-step-b49fa4a64f34 

## Tutorial 1 - Learn how to work with Transformers


Think! 1: Application of attention

Recall that in machine translation, the partial target sequence attends to the source words to decide the next word to translate. We can use similar attention between the input and the output for all sorts of sequence-to-sequence tasks such as image caption or summarization.

Can you think of other applications of the attention mechanism? Be creative!

Map different object/actions in an image to different ROIs activations in fMRI.

Find the relation to between frames in a video. Possibly a way to shortten the video.

---
Select content (referenced by a key) relevant to a query.

Keys are projections of values
Query / Values: sentence or word embeddings.

Weights: how likely is the query matched to a key.

In the encoder-decoder attention, the queries are the decoder state and the value/key are the encoder embeddings.

Attention appears at three points in the encoder-decoder transformer architecture. First, the self-attention among words in the input sequence. Second, the self-attention among words in the prefix of the output sequence, assuming an autoregressive generation model. Third, the attention between input words and output prefix words.

Query: The query is a representation of the current word used to score against all the other words (using their keys). Possibly the target word at the decoder side? We only care about the query of the token we’re currently processing.

Key: Key vectors are like labels for all the words in the segment. They’re what we match against in our search for relevant words.

Value: Value vectors are actual word representations, once we’ve scored how relevant each word is, these are the values we add up to represent the current word. 

One powerful idea in Transformer is multi-head attention, which is used to capture different aspects of the dependence among words (e.g., syntactical vs semantic).

In the sinusoidal encoding, the frequency is how much the bits change

w1 w2 w3  so, w3 > w2 > w1
0  0  0
0  0  1
0  1  0
0  1  1
1  0  0
1  0  1
1  1  0
1  1  1

