---
title: Divergence - Tale of Sentencepiece Library
tags: [GSoC 2020 Blog#3 , Sentencepiece, TextAnalysis, Tokenizer ]
style: 
color: 
description: The blog is about detail explanation of Sentencepiece's unigram language model Algorithm. 
---

{% capture list_items %}
What is SentencePiece?
why Sentencepiece are different from others
An overview of the sentencepiece unigram model
Visualizing the algorithm
Our implementation of Sentencepiece Processor in Julia
References
{% endcapture %}
{% include elements/list.html title="Table of Contents" type="toc" %}
<br>
# What is SentencePiece?
{% include elements/figure.html image="https://raw.githubusercontent.com/tejasvaidhyadev/Portfolio/gh-pages/_images/sentencepiece.jpg" caption="Sentencepiece" %}
SentencePiece is a re-implementation of sub-word units, an effective way to alleviate the open vocabulary problems in neural machine translation. SentencePiece supports two segmentation algorithms, byte-pair-encoding [Sennrich et al.](https://arxiv.org/abs/1508.07909) and unigram language model [Kudo.](https://arxiv.org/abs/1804.10959)
<br>
## why Sentencepiece are different from others
 - It has fixed vocabulary, unlike most unsupervised word segmentation algorithms
 - Trains from raw sentences
 - It treat whitespace as basic symbol which makes it reversibly convertible.

the rest of the detail and original implementation can be found [here](https://github.com/google/sentencepiece)
<br>
# An overview of the sentencepiece unigram model

I believe that familiarity with the implementation in details, benefits and limitations of these algorithms is key to understanding the same for the end-to-end models using these tokenizers. For example - While information on the popular Byte Pair Encoding (BPE) is available with detailed information on the encoding algorithms, I felt working examples (with acceptable real world performance) of the sentence piece unigram encoding algorithm were missing somewhere.

The huge code base and potential lack of familiarity with C++ can make reading the source code a frightening task for the interested data scientist willing to better understand the algorithm.

**Lets begin with overview of Sentencepiece unigram model as mentioned in [kudo et al.,2018](https://arxiv.org/abs/1808.06226)**

It's a probabilist word segmentation algorthim. It decomposed an input(usually sentence) into a sequence of tokens that would have the highest probability to occur in an unigram language model. i.e. the decomposition that maximizes the sum of their log probability

let define it mathematically,

Aim of the tokenization is to identify the subtokens ($$x_1$$, $$x_2$$, ..., $$x_n$$) from the set of segmentation candidates $$S(V)$$ from a input $$X$$ such that

 $$p(X) = \Pi_{i = 1}^{n} p(x_i)$$

<br>
*∀i* $$\space$$ $$x_i \in, \space \sum p(x) = 1$$
<br><br>
the most probable segments $$x^*$$ for input sentence $$X$$
is given by

$$x^* = arg max P(x)$$,$$\space$$ $$x \in S(X) $$
<br>
$$x^*\space$$ is obtained with viterbi algorithm([viterbi,1967](https://ieeexplore.ieee.org/document/1450960))

The algorithm consists of two macro steps: the training on a large corpus and the encoding of sentences at inference time. A detailed description of encoding mechanism is given below.

#### 1. Training
The SentencePiece unigram model aims at maximizing the likelihood of a unigram language model by starting which is pruned iteratively using the Expectation Maximization algorithm.

The SentencePiece tokenization aims at finding the tokenization that maximizes the likelihood of a language model trained using this tokenization. Because these depend on each other, the Expectation Maximization algorithm is used to build this tokenization model with the following steps:

1. Initiate a reasonably large seed vocabulary (generated for example from the (Suffix Array algorithm, Nong et al.) from a training corpus. Define a desired vocabulary size that is smaller than the initial vocabulary (note: this differs from BPE training where the vocabulary grows until it reaches the target size!)
2. Repeat the following Expectation Maximization steps until convergence:
	- Estimate the probability of each vocabulary token using frequency counts in the training corpus
	- Use this probability to tokenize the text using the encoding algirthm described in the following section (Viterbi decoding algorithm).
	- Compute the loss for every vocabulary token, loss being the impact of dropping said token from the vocabulary on the overall likelihood $${L}$$.
	- Prune the vocabulary by keeping the top x%(e.g.80%) tokens with the lowest loss. In order to eliminate the risk of an out-of-vocabulary character item, single characters are usually excluded from this pruning step.

**Thankfully we do not need to train our own model as google shipped pretrained model with ALBERT weights. That means we only have to write sentencepiece Encoder or SentencepieceProcessor**

#### 2. Encoding Algorithm

Encoding (the focus of this article) is used during the training maximization step of EM and at inference in order to encode a new input text. The encoding is done using the Viterbi decoding algorithm consisting of 2 macro steps: a forward step (where the possible sub-tokens are identified) and a backward step (where the most likely decoding sequence is identified).
  - The forward steps identifies the sub-token with the highest probability at each character position of the word. The result at the end of the forward pass is a list of best sub-tokens ending at each character position of the input string.
  - The backward pass takes this list of most likely tokens ending at each position to decode the sequence starting from the end and building its way back to the beginning.
<br>

# Visualizing the algorithm

{% include elements/figure.html image="https://raw.githubusercontent.com/tejasvaidhyadev/Portfolio/gh-pages/_images/forwardpass.png" caption="Forward pass & backward pass used by XLNet tokenizer" %}
<div style="text-align: center;font-size: 12px">
<i>Source:https://myzigyasa.com/post/rust/104/a-rust-sentencepiece-implementation</i>
</div>
<br>
<br>
### Our implementation of Sentencepiece Processor in Julia
<br>
The code can be found [here](https://gist.github.com/tejasvaidhyadev/21a092ff3fe1f2c146a60af44b9519c1).<br>
After proper APIs completion I will creat a PR in `WordTokenizer` <br>
For now the code is kept inside ALBERT PR in TextAnalaysis

```julia
julia> nod = decode_forward(spm,"_all_the_best_for_future") # "_" is special token here, used in place of space 
 24-element Array{Nodes,1}:
 Nodes("_", -Inf32, 1, 1, 1)               
 Nodes("_a", -4.12029f0, 22, 1, 2)         
 Nodes("_al", -8.59771f0, 494, 1, 3)       
 Nodes("_all", -6.58411f0, 66, 1, 4)       
 Nodes("_", -Inf32, 1, 5, 5)               
 Nodes("t", -Inf32, 1, 6, 6)               
 Nodes("th", -7.0317f0, 97, 6, 7)          
 Nodes("_the", -3.07046f0, 15, 5, 8)       
 Nodes("_", -Inf32, 1, 9, 9)               
 Nodes("_b", -8.27204f0, 335, 9, 10)       
 Nodes("_be", -6.03156f0, 45, 9, 11)       
 Nodes("es", -13.69799f0, 161, 11, 12)     
 Nodes("_best", -8.01922f0, 247, 9, 13)    
 Nodes("_", -Inf32, 1, 14, 14)             
 Nodes("_f", -8.39996f0, 399, 14, 15)      
 Nodes("_fo", -10.6494f0, 4311, 14, 16)    
 Nodes("_for", -5.13717f0, 27, 14, 17)     
 Nodes("_", -Inf32, 1, 18, 18)             
 Nodes("_f", -8.39996f0, 399, 18, 19)      
 Nodes("_fu", -10.261f0, 2917, 18, 20)     
 Nodes("ut", -20.14445f0, 1983, 20, 21)    
 Nodes("futu", -21.55436f0, 26920, 19, 22) 
 Nodes("tur", -30.26365f0, 2518, 21, 23)   
 Nodes("_future", -9.25717f0, 1023, 18, 24)

julia>t = Decode_backward1(spm,nod)
julia>reverse(t)
 5-element Array{Any,1}:
 Nodes("_all", -6.58411f0, 66, 1, 4)       
 Nodes("_the", -3.07046f0, 15, 5, 8)       
 Nodes("_best", -8.01922f0, 247, 9, 13)    
 Nodes("_for", -5.13717f0, 27, 14, 17)     
 Nodes("_future", -9.25717f0, 1023, 18, 24)
```
above function is just to show what is happening under the hood our APIs will do all things as shown below.

```julia
julia> spm = load(path)
	Sentencepiecemodel(["<pad>", "<unk>", "[CLS]", "[SEP]", "[MASK]", "(", ")", "\"", "-", "."  …  "_archivist", "_obverse", "error", "_tyrion", "_addictive", "_veneto", "_colloquial", "agog", "_deficiencies", "_eloquent"], [0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0  …  -13.5298, -13.5298, -13.5298, -13.5299, -13.5299, -13.53, -13.5313, -13.5318, -13.5323, -13.5323])

julia> tk = Tokenizer(spm,"the quick brown fox jumps over the lazy dog")
	9-element Array{String,1}:
 "_the"  
 "_quick"
 "_brown"
 "_fox"  
 "_jumps"
 "_over" 
 "_the"  
 "_lazy" 
 "_dog"  

julia> ids_from_tokens(tk) 
	9-element Array{Int64,1}:
    15
  2232
   887
  2386
 17660
    85
    15
 16793
  1953

```
The APIs are not limited to shown above.There are lots of other APIs for Decoding from tokens to Sentence.
As we already completed all the pre-processing component for ALBERT. We can start building our Transformer model :smile:

# References
- [kudo et al.,2018](https://arxiv.org/abs/1808.06226)
- [A rust](https://myzigyasa.com/post/rust/104/a-rust-sentencepiece-implementation)
- [Julia Language](https://julialang.org/)
- [sentencepiece library](https://github.com/google/sentencepiece)
- [Sennrich et al.](https://arxiv.org/abs/1508.07909)  
- [Kudo.](https://arxiv.org/abs/1804.10959)

<br>
**funfact**: All my GSoC blogs are titled as I am walking on the road. yes, you guess it right there will be blog with title "Road Not Taken" at the end
