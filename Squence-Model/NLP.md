# Word Representation

## One-hot representation
* Some examples
1. man(376)-[0,0,0,0,0,0......1,......0]
2. woman(1): [0,1,0,0,0,0........]
* Limitations:

No relations were learnt by models(e.g., models don't indicate anpple juice from orange juice, because models don't know apple and orange are realtively one type of words)
Mainly because inner product of apple one-hot vector and orange one-hot vector are 0.(for every pair of words are 0)

## futurized representation: word embedding

![word_embedding](https://github.com/SuperrWu/Deep-Learning/blob/main/figures/word_embedding.PNG?raw=true)
