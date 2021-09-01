---
title: The end is just another beginning
tags: [GSoC 2020-Blog#5, Summary, TextAnalysis, WordTokenizer, GoogleDrive]
style: 
color: 
description: In this blog, I will be summarising my GSoC-2020 journey.
comments: true
---

Hello there,

The extraordinary journey of Google Summer of Code 2020 is coming to end. In this post, I will be summarizing my GSoC journey and the work done so far with Future goals and milestones

{% include elements/figure.html image="https://raw.githubusercontent.com/tejasvaidhyadev/tejasvaidhyadev.github.io/master/_images/gsoc_logo.png" caption="Google Summer of Code logo" %}

Over the past few months, I continued working with the Julia Language in its NLP Ecosystem. Initially, I proposed Writing the ALBERT in my GSoC. Fortunately, extended [my proposal](https://docs.google.com/document/d/1ucxPM_UOytZVFcWIqZ9kS9gneDGDkcOBvkXA7lLwW28/edit?usp=sharing) to Statistical language model or Language model interface.

I worked on the following projects in GSoC


| Packages and PRs             | status              | open source code                                             |
| ---------------------------- | :------------------ | :----------------------------------------------------------- |
| Language Model Interface     | Approved            | [PR#210](https://github.com/JuliaText/TextAnalysis.jl/pull/210) |
| Statistical Tokenizer        | Approved and merged | [PR#51]( https://github.com/JuliaText/WordTokenizers.jl/pull/51) |
| Converting Tf weight to BSON | Released            | [Gist]( https://gist.github.com/tejasvaidhyadev/6c10bdda1f60c3e42472d356ecf3721a) |
| ALBERT                       | completed           | [PR#203]( https://github.com/JuliaText/TextAnalysis.jl/pull/203/files) |
| ALBERT.jl                    | completed           | [Github Repo]( https://github.com/tejasvaidhyadev/ALBERT.jl) |
| GoogleDrive                  | completed           | [Github Repo]( https://github.com/tejasvaidhyadev/GoogleDrive.jl) |

<br>

### 1. **Language Model Interface**

In the first phase of Google Summer of Code, I implemented the [Language Model Interface](https://github.com/JuliaText/TextAnalysis.jl/pull/210). It provides implemented well-known Langauge models and Framework to create your own Language model with high-level APIs,  which is complete and reviewed by my mentors. 
The blog on the same is [here](https://tejasvaidhyadev.github.io/blog/First-Milestone).


### 2. **Statistical Tokenizer** 

`SentencePiece` is a re-implementation of sub-word units, an effective way to alleviate the open vocabulary problems in neural machine translation. SentencePiece supports two segmentation algorithms, byte-pair-encoding (BPE) [Sennrich et al.] and unigram language model.
I have implemented the Sentencepiece Encoder to help Julia users in WordTokenizer. 
The implementation is described in the blog: **[Divergence - Tale of Sentencepiece Library](https://tejasvaidhyadev.github.io/blog/Sentencepiece)** and `code` can be found [**here**](https://github.com/JuliaText/WordTokenizers.jl/pull/51/commits)

### 3. **Converting Tensorflow weight to Desire Julia Format**

We have converted Tensorflow weights release by Google Research to the following BSON files

{% capture list_items %}
base v1,https://drive.google.com/drive/u/1/folders/1HHTlS_jBYRE4cG0elITEH7fAkiNmrEgz
large v1,https://drive.google.com/drive/u/1/folders/1HHTlS_jBYRE4cG0elITEH7fAkiNmrEgz
xlarge v1,https://drive.google.com/drive/u/1/folders/1HHTlS_jBYRE4cG0elITEH7fAkiNmrEgz
xxlarge v1,https://drive.google.com/drive/u/1/folders/1HHTlS_jBYRE4cG0elITEH7fAkiNmrEgz

{% endcapture %}
{% include elements/list.html title="ALBERT Version-1" %}

{% capture list_items %}
base v2,https://drive.google.com/drive/u/1/folders/1DlX_WZacsjt6O8EDaawKJ-x4RWP46Xj-
large v2,https://drive.google.com/drive/u/1/folders/1DlX_WZacsjt6O8EDaawKJ-x4RWP46Xj-
xlarge v2,https://drive.google.com/drive/u/1/folders/1DlX_WZacsjt6O8EDaawKJ-x4RWP46Xj-
xxlarge v2,https://drive.google.com/drive/u/1/folders/1DlX_WZacsjt6O8EDaawKJ-x4RWP46Xj-

{% endcapture %}
{% include elements/list.html title="ALBERT Version-2" %}

In this version, we apply 'no dropout', 'additional training data' and 'long training time' strategies to all models.

The code for conversion can be found [here](https://github.com/tejasvaidhyadev/ALBERT.jl/blob/master/src/tfckpt2bsonforalbert.jl)

### 4. **ALBERT**

`ALBERT` is "A Lite" version of BERT, a popular unsupervised language representation learning algorithm. ALBERT uses parameter-reduction techniques that allow for large-scale configurations, overcome previous memory limitations, and achieve better behavior with respect to model degradation. The Detail of `ALBERT `is describe in my proposal

The code reside in [TextAnalysis PR#203](https://github.com/JuliaText/TextAnalysis.jl/pull/203) and kept on hold until the TextAnalysis is shifted to Zygote-based Flux 

I have written the Blog:  [**First sight of albert, the land of Transformers**](https://tejasvaidhyadev.github.io/blog/Hey-Albert)  and the following tutorial for ALBERT

{% capture list_items %}
a. Fine-tuning,https://github.com/tejasvaidhyadev/ALBERT.jl/blob/master/docs/Training_fine-tunning_%20tutorial.ipynb
b. Pre-training,https://github.com/tejasvaidhyadev/ALBERT.jl/blob/master/docs/Pretraining_Tutorial(ALBERT).ipynb

{% endcapture %}
{% include elements/list.html title="ALBERT Transformer Tutorials" %}
<br>
### **Other Packages and Blogs**

The following packages are made as the part of Google Summer of Code

{% capture list_items %}
1. GoogleDrive,https://github.com/tejasvaidhyadev/GoogleDrive.jl
2. ALBERT.jl,https://github.com/tejasvaidhyadev/ALBERT.jl 
{% endcapture %}
{% include elements/list.html %}

The following blogs are written by me as part of Google Summer of Code
{% capture list_items %}

1.  Hitting the road,https://tejasvaidhyadev.github.io/blog/Hitting-the-road
2. First Milestone,https://tejasvaidhyadev.github.io/blog/First-Milestone
3. Divergence -Tale of Sentencepiece Library,https://tejasvaidhyadev.github.io/blog/Sentencepiece
4. First sight of albert, the land of Transformers,https://tejasvaidhyadev.github.io/blog/Hey-Albert

{% endcapture %}
{% include elements/list.html %}

### **Future Goal**

- Moving TextAnlaysis to Zygote-based-Flux version and Complete the [PR #209](https://github.com/JuliaText/TextAnalysis.jl/pull/209)

- Implementing ROBERTA, With `TextAnalysis.ALBERT` and `Transformers`, we already have everything to cast it

I  would also like to work on other ecosystems of Julia Lang
<br>
### **Acknowledgement**

I would like to thank **Google** and **JuliaLang** for giving me this amazing opportunity to meet the most amazing people of Julia computing and other open source contributors. I am also grateful to my mentor @Aviks (Avik Sengupta) and @Ayushk4 (Ayush Kaushal) for guiding me through my project. 

To sum up, I would like to call it the **summer of learning** , this was the most productive summer in my life. I Learnt how to write good software and better documentation. Looking back, it feels that these past four months passed way too quickly. I still remember anticipating for proposal acceptance results like it was yesterday.


### **References**

- [ALBERT: A Lite BERT for Self-supervised Learning of Language Representations ](https://arxiv.org/abs/1909.11942)- Zhenzhong Lan, Mingda Chen, Sebastian Goodman, Kevin Gimpel, Piyush Sharma, Radu Soricut
- [Subword Regularization: Improving Neural Network Translation Models with Multiple Subword Candidates](https://arxiv.org/abs/1804.10959) - Kudo
- [Transformers](https://github.com/chengchingwen) - Peter Cheng
- [google-research/albert](https://github.com/google-research/albert)
- [Neural Machine Translation of Rare Words with Subword Units
](https://arxiv.org/abs/1508.07909) - Rico Sennrich, Barry Haddow, Alexandra Birch

**Fun fact**- The title indicates I will keep walking on the road, writing software, experimenting with Machine learning Model, .... (and other 1000s of thing), maybe making mistakes sometimes and surely powering to Julia and other open-source Community 
