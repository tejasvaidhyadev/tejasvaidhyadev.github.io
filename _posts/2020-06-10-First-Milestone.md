---
title: First Milestone
tags: [GSoC 2020-Blog#2, Language Models, TextAnalysis ]
style: 
color: 
description: Introduction of Statistical Language model of TextAnalysis.jl.
---




The coding period for GSoC commenced from 1 june 2020

I started by reading about SentencePiece's Unigram for ALBERT. Apart from that I was actively working on Statistical Language model, which is completed and reviewed by my mentors.

## Types of Language Models

- **Statistical Language Models**: These models use traditional statistical techniques like N-grams, Hidden Markov Models (HMM) and certain linguistic rules to learn the probability distribution of words.

- **Neural Language Models**: These are relatively new Methods in the NLP town and have surpassed the statistical language models in their effectiveness. They use different kinds of Neural Networks to model language. We will be discussing about it in next bolg.


## Implementation of Statistical Language Model

I am proud :smiley: to announce our [Statistical Language Model Framework](https://github.com/JuliaText/TextAnalysis.jl/pull/210) in TextAnalysis.jl inspired from [NLTK.lm](https://www.nltk.org/api/nltk.lm.html).
It provides implemented well known Langauge models and Frame work to creat your own Language model with high level APIs 

**TextAnalysis** provide following different Language Models 

- **MLE** - Base Ngram model.
- **Lidstone** - Base Ngram model with Lidstone smoothing.
- **Laplace** - Base Ngram language model with Laplace smoothing.
- **WittenBellInterpolated** - Interpolated Version of witten-Bell algorithm.
- **KneserNeyInterpolated** - Interpolated  version of Kneser -Ney smoothing.

## APIs

To use the API, we first *Instantiate* desired model and then load it with train set

```julia
MLE(word::Vector{T}, unk_cutoff=1, unk_label="<unk>") where { T <: AbstractString}
        
Lidstone(word::Vector{T}, gamma:: Float64, unk_cutoff=1, unk_label="<unk>") where { T <: AbstractString}
        
Laplace(word::Vector{T}, unk_cutoff=1, unk_label="<unk>") where { T <: AbstractString}
        
WittenBellInterpolated(word::Vector{T}, unk_cutoff=1, unk_label="<unk>") where { T <: AbstractString}
        
KneserNeyInterpolated(word::Vector{T}, discount:: Float64=0.1, unk_cutoff=1, unk_label="<unk>") where { T <: AbstractString}
        
(lm::<Languagemodel>)(text, min::Integer, max::Integer)
```
Arguments:

 * `word` : Array of  strings to store vocabulary.

 * `unk_cutoff`: Tokens with counts greater than or equal to the cutoff value will be considered part of the vocabulary.

 * `unk_label`: token for unkown labels 

 *  `gamma`: smoothing arugment gamma 

 * `discount`:  discounting factor for `KneserNeyInterpolated`

   for more information see docstrings of vocabulary

```julia
julia> voc = ["my","name","is","salman","khan","and","he","is","shahrukh","Khan"]

julia> train = ["khan","is","my","good", "friend","and","He","is","my","brother"]
# voc and train are used to train vocabulary and model respectively

julia> model = MLE(voc)
MLE(Vocabulary(Dict("khan"=>1,"name"=>1,"<unk>"=>1,"salman"=>1,"is"=>2,"Khan"=>1,"my"=>1,"he"=>1,"shahrukh"=>1,"and"=>1…), 1, "<unk
        >", ["my", "name", "is", "salman", "khan", "and", "he", "is", "shahrukh", "Khan", "<unk>"]))
julia> print(voc)
11-element Array{String,1}:
 "my"      
 "name"    
 "is"      
 "salman"  
 "khan"    
 "and"     
 "he"      
 "is"      
 "shahrukh"
 "Khan"    
 "<unk>"   
# you can see "<unk>" token is added to voc 
julia> fit = model(train,2,2) #considering only bigrams
julia> unmaskedscore = score(model, fit, "is" ,"<unk>") #score output P(word | context) without replacing context word with "<unk>"
0.3333333333333333
julia> masked_score = maskedscore(model,fit,"is","alien")
0.3333333333333333
#as expected maskedscore is equivalent to unmaskedscore with context replaced with "<unk>"

```

!!! NOTE

    When you call `MLE(voc)` for the first time, It will update your vocabulary set as well. 

## Evaluation Method

we Provide following Evaluation Method to work with Statistical Language Models.

#### `score`

 	used to evaluate the probability of word given context, *P(word | context)* 

```julia
score(m::gammamodel, temp_lm::DefaultDict, word::AbstractString, context::AbstractString)
```

Arguments:                                                        

1. `m` : Instance of `Langmodel` struct.
2. `temp_lm`: output of function call of instance of `Langmodel`.
3. `word`: string of word 
4. `context`: context of given word

		In case of Lidstone and Laplace it apply smoothing and, 

		In Interpolated language model, provide Kneserney and WittenBell smoothing  

#### `maskedscore` 

  It is used to evaluate *score* with masks out of vocabulary words

  The arguments are the same as for score

#### `logscore` 

  Evaluate the log score of this word in this context.

  The arguments are the same as for score and maskedscore

#### `entropy`
```julia
entropy(m::Langmodel,lm::DefaultDict,text_ngram::word::Vector{T}) where { T <: AbstractString}
```

  Calculate cross-entropy of model for given evaluation text.

  Input text must be Array of ngram of same lengths

#### `perplexity`  

  Calculates the perplexity of the given text.

  This is simply 2 ** cross-entropy(`entropy`) for the text, so the arguments are the same as `entropy`.

##  Preprocessing

 For Preprocessing following functions:

1. `everygram`: Return all possible ngrams generated from sequence of items, as an Array{String,1}

2. `padding_ngrams`: padding _ngram is used to pad both left and right of sentence and out putting ngrmas of order n
	It also pad the original input Array of string 

{% include elements/button.html link="https://github.com/JuliaText/TextAnalysis.jl/pull/210" text="Code" block=true %}

## Future Mile stones :checkered_flag:

I will be working on the following for coming weeks 

- AlbertTokenizer based on [Sentencepiece](https://github.com/google/sentencepiece). we will also be providing wordpiece of [BERT](https://arxiv.org/abs/1810.04805S) for our model to give it more tokenization option to researchers.

- Pretrained weights in BSON (converted from google released Pretrained models)

- ALBERT Transformer 

- APIs for loading Pretrained weights to ALBERT tokenizer.

