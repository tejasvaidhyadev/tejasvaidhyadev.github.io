---
title: First sight of albert, the land of Transformers
tags: [GSoC 2020-Blog#4, ALBERT, TextAnalysis, Transformers ]
style: 
color: 
description: The blog is about present development of ALBERT model in TextAnlaysis.

---

{% capture list_items %}
ALBERT ?
WHY ALBERT
From BERT to ALBERT
Julia-Flux ALBERT Model
Tokenizer
ALBERT Transformer
Classifiers
References
{% endcapture %}
{% include elements/list.html title="Table of Contents" type="toc" %}
<br>

I assume that you are familiar with the original implementation of BERT, if not please read the [BERT paper](https://arxiv.org/pdf/1810.04805.pdf) before moving forward
## ALBERT ?

{% include elements/figure.html image="https://raw.githubusercontent.com/tejasvaidhyadev/tejasvaidhyadev.github.io/master/_images/Albert.jpeg" caption="ALBERT?" %}
An upgrade to BERT that advances the state-of-the-art performance on 12 NLP tasks

The success of ALBERT demonstrates the importance of identifying the aspects of a model that give rise to powerful contextual representations. By focusing improvement efforts on these aspects of the model architecture, it is possible to greatly improve both the model efficiency and performance on a wide range of NLP tasks

## WHY ALBERT


> An ALBERT configuration similar to BERT-large has 18x fewer parameters and can be trained about 1.7x faster.

ALBERT is a “lite” version of Google’s 2018 NLU pretraining method BERT. It has fewer parameter than BERT.


## From BERT to ALBERT
<br>
##### 1. Factorized Embedding Parameterization 

>ALBERT separated the Embedding matrix $$V$$ x $$H$$ to $$V$$ x $$E$$ and and $$E$$ x $$H$$ :


ALBERT uses a factorization of the embedding parameters, decomposing them into two smaller matrices. Instead of projecting the one-hot vectors directly into the hidden space of size H, we first project them into a lower-dimensional embedding space of size E and then project it to the hidden space. By using this decomposition, we reduce the embedding parameters from $$O$$($$V$$ x $$H$$) to $$O$$($$V$$x$$ E + E$$x$$H$$)

##### 2. Cross-layer parameter sharing

>ALBERT uses cross-layer parameter sharing in Attention and FFN(FeedForward Network) to reduce the number of parameters:

weight-sharing has an effect on stabilizing network parameters. Although there is a drop for both metrics compared to BERT, they nevertheless do not converge to 0 even after 24 layers. This shows that the solution space for ALBERT parameters is very different from the one found by DQE.

##### 3. Inter-sentence coherence loss 

>In Original BERT, creating is-not-next (negative) two sentences with randomly picking, however ALBERT uses negative examples the same two consecutive segments but with their order swapped:


 we use a sentence-order prediction (SOP) loss, which avoids topic prediction and instead focuses on modeling inter-sentence coherence. The SOP loss uses as positive examples the same technique as BERT (two consecutive segments from the same document), and as negative examples the same two consecutive segments but with their order swapped.



## Julia-Flux ALBERT Model

Implemented the ALBERT model in Julia to wrap Pretrained Weight released by google-research and allows fine-tuning.
I have also converted google released weights to BSON (julia friendly formate) 
Our ALBERT model is very easy and similar to any of the other Flux layer in training

let's see how to use it

first we load `TextAnalysis` in julia
```julia 
julia> using TextAnalysis
julia> using TextAnalysis.ALBERT
```

we are going to use DataDeps for handling download of pretrained models of ALBERT {base-v1/v2, largev1/v2, xlargev1/v2, xxlargev1/v2}

- For now we are directly loading

- other converted BSON pretrained Weights can be found [here](https://drive.google.com/drive/u/1/folders/1HHTlS_jBYRE4cG0elITEH7fAkiNmrEgz) (Both Versions)

```julia
julia> using BSON: @save, @load

julia> @load "/home/iamtejas/Downloads/albert_base_v1.bson.tfbson" config weights vocab

julia> transformer = TextAnalysis.ALBERT.load_pretrainedalbert(config, weights)
```
**output**

```julia
3-element Array{Any,1}:
CompositeEmbedding(tok = Embed(128), segment = Embed(128), pe = PositionEmbedding(128, max_len=512), postprocessor = Positionwise(LayerNorm(128), Dropout(0.1)))
 TextAnalysis.ALBERT.albert_transformer(Dense(128, 768), TextAnalysis.ALBERT.ALGroup(Stack(Transformer(head=12, head_size=64, pwffn_size=3072, size=768)), Dropout(0.1)), 12, 1, 1)
(pooler = Dense(768, 768, tanh), masklm = (transform = Chain(Dense(768, 128, gelu), LayerNorm(128)), output_bias = Float32[-5.345022, 2.1769698, -7.144285, -9.102521, -8.083536, 0.56541324, 1.2000155, 1.4699979, 1.5557922, 1.9452884  …  -0.6403663, -0.9401073, -1.0888876, -0.9298268, -0.64744073, -0.47156653, -0.81416136, -0.87479985, -0.8785063, -0.5505797]), nextsentence = Chain(Dense(768, 2), logsoftmax))
```

```julia
julia> using WordTokenizers #we have albert_tokenizer residing in WordTokenizer

julia> sample1 = "God is Great! I won a lottery."

julia> sample2 = "If all their conversations in the three months he had been coming to the diner were put together, it was doubtful that they would make a respectable paragraph."
julia> sample3 = "She had the job she had planned for the last three years."
julia> sample = [sample1,sample2,sample3]
```

**output**

```julia
3-element Array{String,1}:
 "God is Great! I won a lottery."
 "If all their conversations in the three months he had been coming to the diner were put together, it was doubtful that they would make a respectable paragraph."
 "She had the job she had planned for the last three years."
```
## Tokenizer

**loading of tokenizer from WordTokenizer**

Instead of using Wordpiece like BERT, most of new models like XLNET and ALBERT uses `sentencepiece` unigram algorithm for subword tokenisation

From avaliable sentencepiece pretrained unigram models we are going to use albert_base_v1_30k-clean.vocab because we are loading same for transformers 
```julia
julia> spm = load(ALBERT_V1,"albert_base_v1_30k-clean.vocab") # since we are using base_V1
```

**output**

```julia
WordTokenizers.Sentencepiecemodel(["<pad>", "<unk>", "[CLS]", "[SEP]", "[MASK]", "(", ")", "\"", "-", "."  …  "_archivist", "_obverse", "error", "_tyrion", "_addictive", "_veneto", "_colloquial", "agog", "_deficiencies", "_eloquent"], [0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0  …  -13.5298, -13.5298, -13.5298, -13.5299, -13.5299, -13.53, -13.5313, -13.5318, -13.5323, -13.5323])
```


## Preprocessing

As we know Transformers takes both tokens as well as segment indices 
Here, we are only working with model structure we will leave adding [CLS] and [SEP] token parts

I am also working on Preprocessing APIs to make it really easy for user

```julia
julia> s1 = ids_from_tokens(spm, tokenizer(spm,sample[1]))
julia> s2 = ids_from_tokens(spm, tokenizer(spm,sample[2]))
julia> s3 = ids_from_tokens(spm, tokenizer(spm,sample[3]))
julia> E = Flux.batchseq([s1,s2,s3],1)
julia> E = Flux.stack(E,1)
```

**output**

```julia
32×3 Array{Int64,2}:
   14     14    14
    2      2     2
 5649    411   439
   26     66    42
   14     67    15
    2  13528  1206
  100     20    40
  722     15    42
  188    133  2036
   14    819    27
    ⋮         
    1     31     1
    1     60     1
    1     84     1
    1    234     1
    1     22     1
    1  22740     1
    1  20600     1
    1     10     1
```

The indices will be act as keys for loading pretrained embedding for each word or subword tokens


```julia
julia> seg_indices = ones(Int, size(E)...)
```

**output**

```julia
32×3 Array{Int64,2}:
 1  1  1
 1  1  1
 1  1  1
 1  1  1
 1  1  1
 1  1  1
 1  1  1
 1  1  1
 1  1  1
 ⋮     
 1  1  1
 1  1  1
 1  1  1
 1  1  1
 1  1  1
 1  1  1
 1  1  1
 1  1  1
```

We already know input embedding requires both segment and token indices. 

the `embedding` function itself handle position embedding (Thanks to [Transformers](https://github.com/chengchingwen/Transformers.jl) )
so lets get pretrained embedding by using ids and segments as keys
```julia
julia> embedding = transformer[1]
juia> emb = embedding(tok=E, segment=seg_indices)
```

**output**

```julia
128×32×3 Array{Float32,3}:
[:, :, 1] =
  0.215637     0.974126    0.923233   …  -0.953364   -1.23193    -1.45834
  0.382527    -0.440211   -0.493132      -0.450212   -0.497128   -0.664383
 -1.06308     -0.596149    1.38881       -0.893396   -0.817059   -0.753805
  0.0192553   -0.606222   -0.0422194      0.213562    0.366818    0.655723
 -1.73208     -0.217243    0.329404       0.720658    0.467273    0.371431
  1.44428      0.352459   -0.307714   …   0.729       0.681432    0.574053
 -2.87975      1.02795    -1.55634       -0.0406037  -0.331129   -0.634261
  0.888469     2.01966     0.139051      -1.54702    -1.5215     -1.46764
  0.423823     0.10119    -1.7348        -1.40969    -0.998497   -0.439296
  0.519439     0.50028     1.78553        1.24271     0.801729    0.306854
 -2.73993     -2.15839    -0.950032   …  -0.726077   -1.00341    -1.15917
 -0.739749    -0.58749     0.697434       2.10209     1.90288     1.72213
 -2.06217     -1.16219     1.14314        1.72633     1.4998      1.32549
  ⋮                                   ⋱               ⋮          
 -1.02152     -0.617795   -0.584283      -1.21236    -1.60555    -2.02886
  0.590658     0.308233   -2.58624        0.18208    -0.327743   -0.678027
  0.565229     0.311107    1.38155       -0.111639    0.160319    0.460262
  0.545883    -0.199483   -0.870848      -4.24455    -4.20667    -4.14337
  2.15259      0.0522619   1.29933    …  -0.0296104  -0.0392038  -0.0438145
 -0.433061    -0.985746    0.175664       0.368157    0.616549    0.803371
  0.00152145   0.997358    0.50851       -0.440633   -0.85439    -0.964204
  2.71532     -0.906451    1.05152       -1.44782    -1.46486    -1.43477
  1.82701      1.27142    -0.359613       1.04111     0.849804    0.684699
 -2.36265     -1.24984     0.74318    …   1.06401     1.02021     1.00714
 -0.00173678  -1.83543     0.705052      -2.21205    -2.00926    -1.76395
  1.65709     -1.17497     1.70831       -1.07015    -1.11008    -0.99317

[:, :, 2] =
  0.215637     0.974126   -2.42081   …   1.54524    0.237261   -0.911703
  0.382527    -0.440211   -0.86025      -0.914859  -0.779649    0.207117
 -1.06308     -0.596149    2.62228      -1.1039     1.05774    -2.34221
  0.0192553   -0.606222    0.414787     -1.73591   -1.3431     -0.440628
 -1.73208     -0.217243   -0.437847     -0.796834   0.618275    0.38779
  1.44428      0.352459    1.23649   …   0.152725   0.955321    0.123936
 -2.87975      1.02795    -3.16862       1.73907   -2.82513    -0.256108
  0.888469     2.01966    -1.2917       -1.07269   -0.537269    0.075918
  0.423823     0.10119     2.23237      -1.66915   -1.67471     0.012503
  0.519439     0.50028    -0.101554      1.35643    1.18131     0.101195
 -2.73993     -2.15839    -1.61688   …   0.627917   2.14858    -2.00197
 -0.739749    -0.58749    -1.4243        0.880429   1.36264     1.42438
 -2.06217     -1.16219     0.640386      0.935937  -0.365015    2.21704
  ⋮                                  ⋱              ⋮          
 -1.02152     -0.617795   -1.05234      -0.334482  -1.4045      0.210466
  0.590658     0.308233    0.821547      1.21049   -1.18044    -1.63386
  0.565229     0.311107    1.09554       0.619731  -1.56184     0.857222
  0.545883    -0.199483   -0.171578      0.169927   0.552766   -3.30788
  2.15259      0.0522619   0.622951  …   1.77554   -2.0677      1.34322
 -0.433061    -0.985746    0.762181     -1.2847    -0.0238061   0.59986
  0.00152145   0.997358   -0.498533      3.38914   -1.50944    -0.203017
  2.71532     -0.906451    1.66836      -0.822932  -1.21968    -1.71859
  1.82701      1.27142     2.1175        0.95669   -0.652382   -1.59357
 -2.36265     -1.24984     0.510399  …  -1.01326    0.230851   -0.992337
 -0.00173678  -1.83543    -1.33135      -0.863463  -0.460078   -2.36823
  1.65709     -1.17497    -0.91338      -0.729243  -1.3999      1.49278

[:, :, 3] =
  0.215637     0.974126   -0.225817   …  -0.953364   -1.23193    -1.45834
  0.382527    -0.440211   -1.56297       -0.450212   -0.497128   -0.664383
 -1.06308     -0.596149    1.76136       -0.893396   -0.817059   -0.753805
  0.0192553   -0.606222    0.63075        0.213562    0.366818    0.655723
 -1.73208     -0.217243   -0.64694        0.720658    0.467273    0.371431
  1.44428      0.352459   -1.68997    …   0.729       0.681432    0.574053
 -2.87975      1.02795    -1.09577       -0.0406037  -0.331129   -0.634261
  0.888469     2.01966    -1.05314       -1.54702    -1.5215     -1.46764
  0.423823     0.10119    -0.0889101     -1.40969    -0.998497   -0.439296
  0.519439     0.50028     1.43852        1.24271     0.801729    0.306854
 -2.73993     -2.15839    -1.82027    …  -0.726077   -1.00341    -1.15917
 -0.739749    -0.58749    -0.698298       2.10209     1.90288     1.72213
 -2.06217     -1.16219    -1.95819        1.72633     1.4998      1.32549
  ⋮                                   ⋱               ⋮          
 -1.02152     -0.617795    1.02958       -1.21236    -1.60555    -2.02886
  0.590658     0.308233   -1.30594        0.18208    -0.327743   -0.678027
  0.565229     0.311107   -0.594398      -0.111639    0.160319    0.460262
  0.545883    -0.199483    0.514127      -4.24455    -4.20667    -4.14337
  2.15259      0.0522619   0.0675038  …  -0.0296104  -0.0392038  -0.0438145
 -0.433061    -0.985746   -0.513366       0.368157    0.616549    0.803371
  0.00152145   0.997358    1.42222       -0.440633   -0.85439    -0.964204
  2.71532     -0.906451    0.384201      -1.44782    -1.46486    -1.43477
  1.82701      1.27142    -1.15566        1.04111     0.849804    0.684699
 -2.36265     -1.24984    -1.98358    …   1.06401     1.02021     1.00714
 -0.00173678  -1.83543     0.815664      -2.21205    -2.00926    -1.76395
  1.65709     -1.17497     0.843728      -1.07015    -1.11008    -0.99317
```


### ALBERT Transformer
**Above we have embedding corresponding to input indices**

*lets pass the embedding through AlbertTranformer to get contextualised_embedding*

```julia
julia> contextualised_embedding = transformer[2](emb)
```

**voilà we got Contextualised embedding below** 

**output**

```julia
768×32×3 Array{Float32,3}:
[:, :, 1] =
  0.304567    0.405941    0.326642   …   0.527699    0.53062     0.535387
  0.765856    1.05468     0.581975       0.902422    0.923356    0.910047
  0.760675    0.440686    1.81601        0.665885    0.615429    0.596886
 -0.0437517  -0.464514   -0.133041      -0.0119426   0.0575484   0.0867782
  0.438816   -0.0251722   0.686429       0.80559     0.805196    0.780889
  0.0296612  -0.685908    0.21051    …  -0.175856   -0.189034   -0.196193
  0.646657    1.67699     0.259575       0.684573    0.667937    0.646987
  0.267509    1.71205     0.686641       0.999966    1.0456      1.06525
 -0.0601687  -0.354132   -0.886672      -0.617012   -0.610717   -0.594557
 -0.364813   -0.159958   -0.996861      -0.187835   -0.205887   -0.215373
  0.988467    1.11282     1.00583    …   0.78229     0.908326    0.959077
  0.0731863  -0.432719    0.150405       0.585053    0.49542     0.441913
  0.15807    -0.490142   -0.405144       0.355488    0.33691     0.322694
  ⋮                                  ⋱               ⋮          
 -0.61483    -0.321608   -0.396901      -0.836611   -0.853394   -0.865005
 -0.0746915   0.738938    0.832527       0.342028    0.363095    0.365716
 -0.655902   -1.1607     -1.03446       -0.329239   -0.297827   -0.290003
 -0.174335   -0.143617   -0.398854      -0.528827   -0.561043   -0.585855
 -1.07943    -1.33676    -1.64727    …  -0.709648   -0.729482   -0.749425
 -0.26735     0.51161    -0.178264      -0.526058   -0.522488   -0.503441
 -0.0936105   0.775895   -0.531953       0.591429    0.477617    0.428794
 -0.41692    -0.290545   -0.37668       -0.810094   -0.902085   -0.958635
 -1.44747    -0.655274    0.0473042     -1.65663    -1.70124    -1.72883
 -0.451427   -1.83576    -0.306356   …  -1.21235    -1.20466    -1.18371
  0.624991    0.149222    0.725459       0.518492    0.579501    0.592086
 -0.440716    0.428943    0.599384      -0.336462   -0.38008    -0.395833

[:, :, 2] =
 -0.09183    -0.131673   -0.0800453  …   0.173828    0.658507    0.701122
 -0.212849    0.425527    0.468926      -0.0383679  -0.254274   -0.0674611
 -0.341473   -0.734532    0.511896      -0.411946    0.0223538   0.465937
 -0.567055   -0.482274   -0.578492      -1.64395    -0.918566   -1.23404
 -0.0708104  -0.59162     0.669678       0.321576    1.18997     0.353643
 -0.0727395  -0.0380078   0.356677   …   0.726067    0.455232   -0.426506
  1.07172     1.92992     1.11336        0.585416   -1.38213     0.764737
 -0.0939165   1.50271     0.300908      -0.608412   -0.663113    0.571664
  0.934051   -0.303075    0.715795       0.201148    0.378836    0.556202
  1.15065     1.58561     1.01433        0.123385    0.436604    0.416501
  0.385488    0.836604   -0.429251   …   1.30753    -0.948893    0.815243
 -0.262729   -1.29692    -0.795957       0.492651    0.310448   -0.779165
 -0.182217   -0.979907   -0.463309      -0.604354    0.542724   -1.3294
  ⋮                                  ⋱               ⋮          
  0.313161    0.297878    0.238105      -1.24137    -0.959478   -0.116641
 -0.212055    0.738047    0.413007       0.364323   -0.160887   -0.25063
  0.347592    0.115097   -0.10026       -0.299359   -0.711259   -0.252505
  0.0245221  -0.190721    0.824076      -1.36732    -1.30632     0.85736
  0.251426   -0.0943026   0.19253    …   0.456811    0.0460289   0.700604
 -0.792393   -0.963726   -0.707541      -1.5676     -1.30831    -1.06157
 -0.78274    -0.218586   -0.905263      -0.0916421  -0.39057    -0.315191
 -0.255523   -0.509181    0.0483524      0.51547    -0.299128   -0.54637
 -2.5418     -2.05595    -1.71871        0.58241    -0.680839   -3.12875
  0.0385001  -0.665508   -0.385825   …  -0.494911   -0.0957252  -0.558129
  0.511562    0.140494    0.752053      -0.387508   -0.0610264   0.639027
 -0.988561   -0.974358   -0.338162      -0.871169   -1.64719    -1.42307

[:, :, 3] =
 -0.464287    0.444703    0.332893   …   0.674975     0.69247     0.707714
  1.01715     0.517691    0.078989       0.692509     0.75075     0.755857
 -0.149221   -0.315486    0.943656       0.896174     0.823444    0.786195
 -0.775787   -0.575133   -0.768595       0.114394     0.155716    0.157084
 -0.763795    0.167911    0.860362       0.478681     0.448441    0.438333
  0.696022   -1.07504     0.214933   …  -0.923638    -0.924721   -0.921711
  0.553646    1.40984     1.25859        0.903849     0.887553    0.890889
 -0.788586    0.565872   -0.174171       0.592233     0.678486    0.703608
  0.917794   -0.290047    0.270431      -0.577756    -0.557005   -0.531713
  0.0703508   0.718436    0.524612      -0.106808    -0.161638   -0.198985
  1.83724     1.25059     0.441462   …   0.717154     0.842766    0.873928
 -1.00134    -1.23632    -0.182          0.975941     0.873459    0.825883
  0.469249   -0.668738   -0.176839      -0.00468119  -0.0277034  -0.0290249
  ⋮                                  ⋱                ⋮          
 -1.23669    -0.380987   -1.42546       -1.55032     -1.53026    -1.51031
  0.208317    0.0787398   0.419125       0.865003     0.916697    0.938971
 -0.626502   -0.560398   -0.64055       -0.569054    -0.532433   -0.525647
  0.374139   -0.852387    0.234086      -0.76758     -0.827931   -0.849001
 -0.499433   -0.115525   -1.0104     …  -0.357703    -0.374017   -0.408415
 -0.930513   -0.615282   -1.221         -0.550265    -0.580068   -0.5931
  0.812305   -0.594478   -1.84857        0.303941     0.145331    0.0992277
  0.103422   -0.172053    0.0998552     -0.925473    -1.03992    -1.10758
 -1.46715    -1.21069    -0.278395      -1.86522     -1.91097    -1.96085
 -0.464279   -1.01199     0.0595983  …  -1.23196     -1.19695    -1.17389
 -0.463837   -0.709276    1.26165       -0.606749    -0.481565   -0.447495
 -0.407867    0.342045    0.423647      -0.871686    -0.89004    -0.880378
```

### Classifiers

we also have loaded weight of MLM classifier and SOP classifier used for pretraining

**MLM layer with loaded pretrained weights**
```julia
julia> cls = transformer[3][1] #for mlm  tasked and transformer[3][2] is pooler layer
```

**output** 

```julia
(transform = Chain(Dense(768, 128, gelu), LayerNorm(128)), output_bias = Float32[-5.345022, 2.1769698, -7.144285, -9.102521, -8.083536, 0.56541324, 1.2000155, 1.4699979, 1.5557922, 1.9452884  …  -0.6403663, -0.9401073, -1.0888876, -0.9298268, -0.64744073, -0.47156653, -0.81416136, -0.87479985, -0.8785063, -0.5505797])
```

**Sentence Order Prediction loaded layer**

```julia
julia> cls = transformer[3][3] #for Sentence order prediction
```

**output**

```julia
Chain(Dense(768, 2), logsoftmax)
```

You can also get code in IPYNB [Here](https://github.com/tejasvaidhyadev/ALBERT.jl/blob/master/docs/Transformer%20_layer.ipynb)



## References 

[Transformer.jl](https://github.com/chengchingwen/Transformers.jl)

[Huggingface.jl](https://huggingface.co/)

[WordTokenizer.jl](https://github.com/JuliaText/WordTokenizers.jl/tree/master/src/words)

[ALBERT](https://arxiv.org/pdf/1909.11942.pdf)
