# Previous work:
* Previous models
1. Recurrent neural networks
2. long short-term memory

These are state of the art approaches in sequence modeling to slove transduction problems such as 
1. language modeling
2. machine translation.
* Some Limitations & Reason for building Transformer\
LSTM generate a sequence of hidden states ht, as a function of the previous hidden state ht−1 and the input for position t. This inherently sequential nature **precludes parallelization** within training examples, which becomes critical at longer sequence lengths, as memory constraints limit batching across examples.

Transformer is the first transduction model relying entirely on self-attention to compute representations of its input and output **without using sequence aligned RNNs or convolution**.

# Transformer Arichitectures\
https://github.com/SuperrWu/Deep-Learning/blob/main/figures/transformer_model_architecture.PNG?raw=true
* Encoder
* Decoder



