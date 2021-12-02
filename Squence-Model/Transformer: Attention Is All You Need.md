# paper link

https://dl.acm.org/doi/pdf/10.5555/3295222.3295349

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
Reasons: To solve the infomation loss problem in normal Encoder-Decoder Models.

* Self-Atention and Muti-head Attentions (more detials in https://github.com/SuperrWu/Deep-Learning/blob/main/Squence-Model/Self-Attention.md)


# Transformer Arichitectures
![image](https://user-images.githubusercontent.com/94330800/144349743-159083ef-77d8-431c-91f2-8b66ee28141a.png)

* Encoder

Each layer has two sub-layers:
1. multi-head self-attention mechanism
2. a simple, position-wise fully connected feed-forward network (later)
3. a residual connection after each layer. That is, the output of each sub-layer is LayerNorm(x + Sublayer(x))

![image](https://user-images.githubusercontent.com/94330800/144351621-5bed7f19-d370-40cb-885e-f096467ecb6a.png)


* Decoder
1. Masked Multi-Head Attention
![image](https://user-images.githubusercontent.com/94330800/144352915-e9bc3b1b-2511-4534-a58a-ff310e31ccd7.png)

why masked? Becuse decoder generates words **one by one**.

2.cross attention

![image](https://user-images.githubusercontent.com/94330800/144368262-9e7c2725-8ef3-487f-a215-cbfb88981bb4.png)

Cross attention is first published in Seq2Seq in speech recoginazation in https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=7472621.

![image](https://user-images.githubusercontent.com/94330800/144369211-e94d52f5-a5b2-4550-a496-b2e4a574577d.png)

## Positional encoding
Reason why: Since our model contains no recurrence and no convolution, in order for the model to make use of the
order of the sequence, we must inject some information about the relative or absolute position of the
tokens in the sequence. 


