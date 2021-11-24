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
3. lsat word      apple ?
4. nearby 1 word        glass _ ? (called skip-gram)
More detial is in the graph
![img](https://github.com/SuperrWu/Deep-Learning/blob/main/figures/NLP_word_embeddin_context.PNG?raw=true)

