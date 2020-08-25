---
title: The end is just another beginning
tags: [GSoC 2020, Summary, TextAnalysis, WordTokenizer, GoogleDrive]
style: fill
color: secondary
description: GSoC 2020-Blog#5 summarisation my GSoC-2020 journey
comments: true
---

Hello there :wave:,

The extraordinary journey of Google Summer of Code 2020 is coming to end. In this post, I will be summarizing my GSoC journey and the work done so far with Future goals and milestones

{% include elements/figure.html image="https://raw.githubusercontent.com/tejasvaidhyadev/tejasvaidhyadev.github.io/master/_images/gsoc_logo.png" caption="Google Summer of Code logo" %}

Over the past few months, I continued working with the Julia Language in its NLP Ecosystem. Initially, I proposed Writing the ALBERT in my GSoC. Fortunately, extended [my proposal](https://docs.google.com/document/d/1ucxPM_UOytZVFcWIqZ9kS9gneDGDkcOBvkXA7lLwW28/edit?usp=sharing) to Statistical language model or Language model interface.

I worked on the following projects in GSoC
### 1. **Language Model Interface**

In the first phase of Google Summer of Code, I implemented the [Language Model Interface](https://github.com/JuliaText/TextAnalysis.jl/pull/210). It provides implemented well-known Langauge models and Framework to create your own Language model with high-level APIs,  which is complete and reviewed by my mentors. 
The blog on the same can be found [here](https://tejasvaidhyadev.github.io/blog/First-Milestone).

### 2. **Statistical Tokenizer** 

`SentencePiece` is a re-implementation of sub-word units, an effective way to alleviate the open vocabulary problems in neural machine translation. SentencePiece supports two segmentation algorithms, byte-pair-encoding (BPE) [Sennrich et al.] and unigram language model
I have implemented the Sentencepiece Encoder to help Julia users in WordTokenizer. 
The implementation is described in the blog: **[Divergence - Tale of Sentencepiece Library](https://tejasvaidhyadev.github.io/blog/Sentencepiece)** and `code` can be found [**here**](https://github.com/JuliaText/WordTokenizers.jl/pull/51/commits)

### 3. **Converting Tensorflow weight to Desire Julia Format**

We have converted Tensorflow weights release by Google Release to the following BSON files

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

The code is reside in [TextAnalysis PR#203](https://github.com/JuliaText/TextAnalysis.jl/pull/203) and kept on hold until the TextAnalysis is shifted to Zygote based Flux 

I have written the Blogs  [**First sight of albert, the land of Transformers**](https://tejasvaidhyadev.github.io/blog/Hey-Albert)  and the following tutorial for ALBERT

{% capture list_items %}
a. Fine-tuning,https://github.com/tejasvaidhyadev/ALBERT.jl/blob/master/docs/Training_fine-tunning_%20tutorial.ipynb
b. Pre-training,https://github.com/tejasvaidhyadev/ALBERT.jl/blob/master/docs/Pretraining_Tutorial(ALBERT).ipynb

{% endcapture %}
{% include elements/list.html title="ALBERT Transformers Tutorial" %}
<br>
**Other Packages**

The following packages are made as the part of Google summer of code

- [GoogleDrive](https://github.com/tejasvaidhyadev/GoogleDrive.jl)
- [ALBERT.jl](https://github.com/tejasvaidhyadev/ALBERT.jl) 


**List of the Blogs**

{% capture list_items %}

1.  Hitting the road,https://tejasvaidhyadev.github.io/blog/Hitting-the-road
2. First Milestone,https://tejasvaidhyadev.github.io/blog/First-Milestone
3. Divergence -Tale of Sentencepiece Library,https://tejasvaidhyadev.github.io/blog/Sentencepiece
4. First sight of albert, the land of Transformers,https://tejasvaidhyadev.github.io/blog/Hey-Albert

{% endcapture %}describe
{% include elements/list.html title="" %}

**Future Goal :checkered_flag:**

- I will be moving TextAnlaysis to Zygote based Flux version and Complete the [PR #209](https://github.com/JuliaText/TextAnalysis.jl/pull/209)

- ROBERTA, With `TextAnalysis.ALBERT` and `Transformers` we already have everything to cast it

I  would also like to work on other ecosystems of Julia Lang
### **Acknowledgement**

I would like to thank **Google** and **JuliaLang** for giving me this amazing opportunity to meet the amazing people of Julia computing and other open source contributors. I am also grateful to my mentor @Aviks (Avik Sengupta) and @Ayushk4 (Ayush Kaushal) for guiding me through my project. 

To sum up, I would like to call it the** summer of learning**, this was the most productive summer in my life. I Learnt how to write good software and better documentation

**Fun fact**- The Title means I will keep walking on the road, writing software, experimenting with Machine learning Model, .... (and other 1000s of thing), maybe making mistakes something and surely powering to Julia and other open-source Community 