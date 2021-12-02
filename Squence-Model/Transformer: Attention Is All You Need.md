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

# Pre-Knowledge
* Normal Encoder-Decoder Models (more details in https://github.com/SuperrWu/Deep-Learning/blob/main/Squence-Model/NLP.md)
<div align=center>
<img src="https://github.com/SuperrWu/Deep-Learning/blob/main/figures/encode-decode.PNG?raw=true"/>
</div>

Some important notes:

1. Regardless of the length of the input and output, the length of the "vector c" in the middle is fixed (this is its flaw).

2. Different encoders and decoders can be selected according to different tasks (for example, CNN, RNN, LSTM, GRU, etc).

3. A  istinctive feature of Encoder-Decoder is that it is an end-to-end learning algorithm. (end-to-end: input-raw data, output-classification or regression)

4. **There is a shared vector (vector c in the above figure) between the encoder and the decoder to transmit information, and its length is fixed. This will cause a problem of information loss, that is, the encoder will compress the entire sequence of information into a fixed-length vector. (Another problem in sequece models. e.g., LSTM-the first input will be diluted by the information input later, or overwritten.)**

This is why Attention Encoder-Decoder Models

* Attention Encoder-Decoder Models ()
Reasons: To solve the infomation loss problem in normal Encoder-Decoder Models.



# Transformer Arichitectures
<div align=center>
<img src="https://github.com/SuperrWu/Deep-Learning/blob/main/figures/transformer_model_architecture.PNG?raw=true"/>
</div>

* Encoder
Each layer has two sub-layers:
1. multi-head self-attention mechanism
2. a simple, position-wise fully connected feed-forward network

a residual connection after each layer. That is, the output of each sub-layer is LayerNorm(x + Sublayer(x))
* Decoder



