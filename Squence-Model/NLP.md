# Word Representation

## One-hot representation
* Some examples
1. man(376)-[0,0,0,0,0,0......1,......0]
2. woman(1): [0,1,0,0,0,0........]
* Limitations:

No relations were learnt by models(e.g., models don't indicate anpple juice from orange juice, because models don't know apple and orange are realtively one type of words)
Mainly because inner product of apple one-hot vector and orange one-hot vector are 0.(for every pair of words are 0)

## Futurized representation: word embedding

<div align=center>
<img src="https://github.com/SuperrWu/Deep-Learning/blob/main/figures/word_embedding.PNG?raw=true">
</div>

* properities of word embedding
1. analogies

man -> woman  so king -> ?

e(man) - e(king) = [-2,0,0,0,0,0,0,0..........]
e(woman) - e(queen) = [-2,0,0,0,0,0,0,0.........]

2. cosine similarity

(w.T * V)/(|w||V|)

3、word embedding matrix

![image](https://user-images.githubusercontent.com/94330800/142990546-2e31293d-89a2-416a-8b49-97d650844b86.png)

In order to make the operation easier, one column of the matrix is usually extracted directly, such as keras embedding layer

# Train the word embedding
<div aligh=center>
  <img src="https://github.com/SuperrWu/Deep-Learning/blob/main/figures/Train_embedding.PNG?raw=true">
</div>

The E embedding matrix is randomly weighted or according to different initial strategies. Using backprop to optimize the embedding matrix E.
There are many types of training strategies:
1. last four words   a glass of apple ?
2. last four words on the left and right     a glass of apple ? on the white table
3. last word      apple ?
4. nearby 1 word        glass _ ? (called skip-gram)
More detial is in the graph
![img](https://github.com/SuperrWu/Deep-Learning/blob/main/figures/NLP_word_embeddin_context.PNG?raw=true)

**If you are building a NLP model, then stategy1 is suitable**. 
Howerver, if you want to build a model to learn embedding matrix. Then just try all of them, they all have great results.

**And note that strategy 4 is also called skip-grams**

# Wrod2Vec
## skip-grams
```
skip-grams
I want a glass of orange juice to go alone with my ceral.
context    target (randomly pick with a window size 10 [10 nearby words])
juice      orange
juice      glass
juice      my
```
This is a little bit like self-superviesd learning

Let's start training!
![img](https://github.com/SuperrWu/Deep-Learning/blob/main/figures/word2vec.PNG?raw=true)

As shown in the previous training strategy4, skip-grams is to **give a word C to predict any character T in any window length before or after the text**. Use a very small network to train the embedding matrix.

### limitations of skip-grams
The softmax need to calculate all 10000 words. This is a huge computation.
possible solutions:
* use a **Hierarchical Softmax**. It is a tree model, each node represents a softmax node.
![img](https://github.com/SuperrWu/Deep-Learning/blob/main/figures/problems%20_skip_grams.PNG?raw=true)

More common words, higher tree depths are.
* Negtive sampling, tranfer 10000 classification softmax to 10000 binary classification model (not train at the same time)
![img](https://github.com/SuperrWu/Deep-Learning/blob/main/figures/nlp_negtive_sampling.PNG?raw=true) 
```
I want a glass of orange juice to go alone with my ceral.
context     target     label
orange      juice      1       (Pick target words as skip-gram do, and give the label 1)
orange      king       0       (Pick target words randomly in word list, and give the label 0)
orange      man        0
orange      of         0      (give the label 0, even "of" neaby)
```

# NLP models
## Classification(many to one)
![image](https://user-images.githubusercontent.com/94330800/143184322-73a2b28e-4403-4c5b-acc7-7acf03be3604.png)
reverse the skip-grams
## Seq2Seq(many to many)
Used for translation
### Encoder-Decoder
![image](https://user-images.githubusercontent.com/94330800/143187023-448f4f07-4ae1-460c-98fb-28c23f96a348.png)
* encoder
1. We use h_t=f(x_t,h_{t-1}) to caculate every time step output
2. The easiest way to obtain the semantic vector is to directly use the hidden state of the last input as the semantic vector C
3. Convert variable length input into fixed length semantic vector
* decode
1. output the probablity of each time step according to (y_t-1, C)
### Attention-Model
The normal encoder-decoder reads the input sentence and then translates it. People translation is to read one sentence and then translate one sentence. Because **memorizing a long paragraph of text is very difficult**.

![image](https://user-images.githubusercontent.com/94330800/143191199-b0384cbf-9a1d-47d9-9ae7-8b32870f9e47.png)

The semantic vector C is weighted by the output of different time steps. And the a(the weight of each time point is trained by a simple neural network as followed)

![image](https://user-images.githubusercontent.com/94330800/143191056-3774c889-81ff-49ab-99b6-7cf8f7307425.png)

output the probablity of each time step according to (y_t-1, C_t-1)

