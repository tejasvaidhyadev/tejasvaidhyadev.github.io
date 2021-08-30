---
layout: default
permalink: /
---
{% include landing.html %}

## **About Me**

Hello, I'm Tejas Vaidhya,  
I am currently in my senior year of Undergraduate studies at [Indian Institute of Technology, Kharagpur](http://iitkgp.ac.in/).

My research interests include Natural Language processing, Computer vision and Causal Inference. I am also highly interested to work on causality, explainability and Transformer based Language models. The goal of my research is to develop useful systems that work for the right reasons!

I love Programming, Designing, and Planning. I also enjoy watching Anime, reading non-fiction, film making, cooking, and interacting with new people. I am a foodie. In my free time, I like to explore food (you can often find me in some of the eateries of KGP). I have always adored technology and am very much fascinated by how it affects the life of people.  

{% include elements/button.html link="https://scholar.google.com/citations?user=dGedZKoAAAAJ&hl=en)" text="**Google Scholar**" style="outline-dark" size="sm" %}  | {% include elements/button.html link="https://twitter.com/imtejas13" text="**Twitter Handle**" style="outline-dark" size="sm" %} 


___

  

  

## **News** 
- **7 July 2021**: Attending [Eastern European Machine Learning Summer School, 2021](https://www.eeml.eu/home)  
- **1 May 2021**: Mentoring two project in [Google Summer of Code, 2021](https://github.com/AdarshKumar712/PPLM.jl) and [Julia Summer of Code, 2021](https://github.com/SambhawDrag/XLNet.jl).
- **1 March 2021**: Starting Research internship at [Mrinmaya's Lab, ETH Zürich](http://www.mrinmaya.io/)
- **14 Jan 2021**: Starting internship at [Uniworks Designs, Hyderabad](https://uniworksdesigns.com/) 
- **7 Jan 2021**: Paper accepted to the [CONSTRAINT](https://constraint-shared-task-2021.github.io/) workshop, collocated with AAAI 2021
- **6 October 2020**: paper accepted to EMNLP 2020, Workshop on [Noisy User-generated Text](http://noisy-text.github.io/2020/).
- **1 October 2020**: paper accepted to EMNLP 2020, Workshop on [Noisy User-generated Text](http://noisy-text.github.io/2020/).
- **12 September 2020**: Ranked 1st at the leaderboard for EMNLP 2020, W-NUT workshop Shared Task 3.
- **31 August 2020**: Completed wonderful summer at [Google Summer of Code](https://summerofcode.withgoogle.com/archive/2020/projects/4810193256316928/)
- **31 Jun 2020**: completed my research intern at [CERN](https://home.cern/)     


___

  

  



## **Publications**

<ul>

<li><a target="_blank" href="https://www.aclweb.org/anthology/2020.wnut-1.79.pdf">
          "Leveraging Event Specific and Chunk Span features to Extract COVID Events from tweets"</a>, Ayush Kaushal and Tejas Vaidhya <br>
          <b><u>Oral Presentation</u></b> at the 6th Workshop on Noisy User-generated Text (W-NUT) at the 2020 Conference on Emperical Methods in Natural Language Processing (EMNLP) <u><b>Shared Task Winners</b></u> <br>
          {% include elements/button.html link="https://github.com/Ayushk4/extract_covid_entity" text="Code" %} {% include elements/button.html link="https://www.aclweb.org/anthology/2020.wnut-1.79.pdf" text="Pdf" %} {% include elements/button.html link="https://www.aclweb.org/anthology/2020.wnut-1.79.bib" text="Cite" %} {% include elements/button.html link="https://docs.google.com/presentation/d/13DDY6VSmrVPBddTjWb3rThYRFlRDE_9fi4iyBrhJev4/edit?usp=sharing" text="Slides" %} {% include elements/button.html link="https://github.com/noisy-text/noisy-text.github.io/blob/master/2020/posters/WNUT2020_91_poster%20-%20Tejas%20vaidhya.pdf" text="Poster" %} 
          <a style="float:right; color:#3491fe;" data-toggle="collapse" data-target="#covid"><u>More</u> </a>
  </li>
    <div id="covid" class="collapse" style="font-size:15px;margin:50px">Twitter has acted as an important source of information during disasters and pandemic, especially during the times of COVID-19. In this paper, we describe our system entry for <i>WNUT 2020 Shared Task-3</i>. The task was aimed at automating the extraction of a variety of COVID-19 related events from Twitter, such as individuals who recently contracted the virus, someone with symptoms who were denied testing and believed remedies against the infection. The system consists of separate multi-task models for slot-filling subtasks and sentence-classification subtasks while leveraging the useful sentence-level information for the corresponding event. The system uses COVID-Twitter-Bert with attention-weighted pooling of candidate slot-chunk features to capture the useful information chunks. The system ranks <b>1st at the leader-board</b> with F1 of 0.6598, without using any ensembles or additional datasets. <br> <br>
  </div>
    <br>

<li><a target="_blank" href="https://www.aclweb.org/anthology/2020.wnut-1.34.pdf">
          "Domain specific BERT representation for Named Entity Recognition of lab protocol."</a>, Tejas Vaidhya and Ayush Kaushal <br>
           Proceedings of the 6th Workshop on Noisy User-generated Text (W-NUT) at the 2020 Conference on Emperical Methods in Natural Language Processing (EMNLP)  <a style="float:right;color:#3491fe" data-toggle="collapse" data-target="#wetlab"><u>More</u></a>
  </li>
    <div id="wetlab" class="collapse" style="font-size:15px;margin:50px">
    <!-- <br>
    <div align="center">
        <img id="mobile-img" src="../images/Bio-BERT.png" width="50%" border="0" height="50%" alt=""><br>
        </div> -->
        Supervised models trained to predict properties from representations, have been achieving high accuracy on a variety of tasks. For instance, the BERT family seems to work exceptionally well on the downstream task from NER tagging to the range of other linguistic tasks. But the vocabulary used in the medical field contains a lot of different tokens used only in the medical industry such as the name of different diseases, devices, organisms, medicines, etc. that makes it difficult for traditional BERT model to create contextualized embedding. In this paper, we are going to illustrate the System for Named Entity Tagging based on Bio-Bert. Experimental results show that our model gives substantial improvements over the baseline and stood the fourth runner up in terms of F1 score, and first runner up in terms of Recall among 13 teams with just 2.21 F1 score behind the best one.
        <br> <br>
        {% include elements/button.html link="https://github.com/tejasvaidhyadev/W-NUT_2020" text="Code" %} {% include elements/button.html link="https://www.aclweb.org/anthology/2020.wnut-1.34.pdf" text="Pdf" %} {% include elements/button.html link="https://www.aclweb.org/anthology/2020.wnut-1.34.bib" text="Cite" %} {% include elements/button.html link="https://github.com/noisy-text/noisy-text.github.io/blob/master/2020/posters/WNUT2020_92_poster%20-%20Tejas%20vaidhya.pdf" text="Poster" %}
    </div>
    <br>

<li><a target="_blank" href="https://arxiv.org/pdf/2101.05494.pdf">
          "Hostility Detection in Hindi leveraging Pre-Trained Language Models"</a>, Ojasv Kamal, Adarsh Kumar, and Tejas Vaidhya <br>
           <b><u>Oral Presentation</u></b> at the Constraint workshop at Advancement Of Artificial Intelligence <a style="float:right; color:#3491fe;" data-toggle="collapse" data-target="#fakenews"><u>More</u> </a>
  </li>
    <div id="fakenews" class="collapse" style="font-size:15px;margin:50px">Hostile content on social platforms is ever increasing. ThisCONSTRAINT workshop at AAAI
has led to the need for proper detection of hostile posts so that appropriate action can be taken to tackle them. Though a lot of work has been
done recently in the English Language to solve the problem of hostile
content online, similar works in Indian Languages are quite hard to find.
This paper presents a transfer learning based approach to classify social
media (i.e Twitter, Facebook, etc.) posts in Hindi Devanagari script as
Hostile or Non-Hostile. Hostile posts are further analyzed to determine
if they are Hateful, Fake, Defamation, and Offensive. This paper harnesses attention based pre-trained models fine-tuned on Hindi data with
Hostile-Non hostile task as Auxiliary and fusing its features for further
sub-tasks classification. Through this approach, we establish a robust and
consistent model without any ensembling or complex pre-processing. We
have presented the results from our approach in CONSTRAINT-2021
Shared Task[21] on hostile post detection where our model performs extremely well with 3rd runner up in terms of Weighted Fine-Grained
F1 Score1. <br> <br>
      {% include elements/button.html link="https://github.com/kamalojasv181/Hostility-Detection-in-Hindi-Posts" text="Code" %} {% include elements/button.html link="https://arxiv.org/pdf/2101.05494.pdf" text="Pdf" %} {% include elements/button.html link="" text="Cite" %} {% include elements/button.html link="" text="Slides" %} 
  </div>
    <br>

<li><a target="_blank" href="https://github.com/jharkawat/meddoprof_shared_task">
          "Spanish Pre-Trained Language Models for HealthCare Industry"</a>, Tejas Vaidhya and Jalaj Harkawat<br>
           <b><u>Oral Presentation</u></b> at Proceedings of the Iberian Languages Evaluation Forum <a style="float:right; color:#3491fe;" data-toggle="collapse" data-target="#beto"><u>More</u> </a>
  </li>
    <div id="beto" class="collapse" style="font-size:15px;margin:50px">Currently transformer based model have shown high accuracy and good prediction on downstream tasks like Named Entity Recognition, Sentiment analysis etc. But the terminologies used in Healthcare sector such as names of different diseases, medicines and departments makes it difficult to predict with high accuracy. In this paper we are going to show a system for Named Entity tagging based on BETO (SpanishBERT). Experimental results have shown that our model gives better results than the current baseline of MEDDOPROF Shared task. <br> <br>
      {% include elements/button.html link="https://github.com/jharkawat/meddoprof_shared_task" text="Code" %} {% include elements/button.html link="" text="Pdf" %} {% include elements/button.html link="" text="Cite" %} {% include elements/button.html link="" text="Slides" %} 
  </div>
    <br>

<li><a target="_blank" href="https://drive.google.com/file/d/1UDGujYmKUzDRFgLbvF355URmxiEyoMXv/view">
          "Causal Direction in Data Matters: Implications of Causal and Anticausal Learning in NLP"</a>, Zhijing Jin, Julius von KÃgelgenâ, Jingwei Ni, Tejas Vaidhya, Ayush Kaushal, Mrinmaya Sachan and Bernhard Schoelkopf<br>
          <b><u>Long Paper</u></b> at the 2021 Conference on Emperical Methods in Natural Language Processing (EMNLP) <a style="float:right; color:#3491fe;" data-toggle="collapse" data-target="#emnlp"><u>More</u> </a>
  </li>
    <div id="emnlp" class="collapse" style="font-size:15px;margin:50px">descriptionThe principle of independent causal mechanisms (ICM) states that generative processes of real-world data consist of independent modules which do not influence or inform each other. While this idea has led to fruitful developments in the field of causal inference, it is not widely known in the NLP community. In this work, we argue that the causal direction of the data collection process bears non trivial implications that can explain a number of published NLP findings, such as differences in semi-supervised learning (SSL) and domain adaptation (DA) performance across different settings. We categorize common NLP tasks according to their causal direction and empirically assay the validity of the ICM principle for text data using minimum description length. We conduct an extensive meta-analysis of over 100 (SSL) and 30 (DA) published studies, and find that the results are consistent with our expectations based on causal insights. This work presents the first attempt to analyze the ICM principle in NLP, and provides constructive suggestions for future modelling choices
. <br> <br>
      {% include elements/button.html link="" text="Code" %} {% include elements/button.html link="https://drive.google.com/file/d/1UDGujYmKUzDRFgLbvF355URmxiEyoMXv/view" text="Pdf" %} {% include elements/button.html link="" text="Cite" %} {% include elements/button.html link="" text="Slides" %}
 </div>
    <br>

<li><a target="_blank" href="https://drive.google.com/file/d/12-hJeIqjMx-GnfjXf3E6vcVYlamN5yoR/view?usp=sharing">
          "Mining the Cause of Political Decision-Making from Social Media: A Case Study of COVID-19 Policies across the US States"</a>, Zhijing Jin, Zeyu Peng, Tejas Vaidhya, Bernhard Schoelkopf and Rada Mihalcea<br>
          <b><u>Findings of EMNLP</u></b> at the 2021 Conference on Emperical Methods in Natural Language Processing (EMNLP) <a style="float:right; color:#3491fe;" data-toggle="collapse" data-target="#emnlp21"><u>More</u> </a>
  </li>
    <div id="emnlp21" class="collapse" style="font-size:15px;margin:50px">Mining the causes of political decision making is an active research area in the field of political science. In the past, most studies have focused on long-term policies that are collected over several decades of time, and have primarily relied on surveys as the main source of predictors. However, the recent COVID 19 pandemic has given rise to a new political phenomenon, where political decision-making consists of frequent short-term decisions, all on the same controlled topic—the pandemic. In this paper, we focus on the question of how public opinion influences policy decisions while controlling for covariates such as COVID-19 case increases or unemployment rates. Using a dataset consisting of Twitter data from the 50 US states, we classify the sentiments toward governors of each state, and conduct controlled studies and comparisons. Based on the compiled samples of sentiments, policies, and covariates, we conduct causal inference to discover trends in political decision making across different states


. <br> <br>
      {% include elements/button.html link="" text="Code" %} {% include elements/button.html link="https://drive.google.com/file/d/12-hJeIqjMx-GnfjXf3E6vcVYlamN5yoR/view?usp=sharing" text="Pdf" %} {% include elements/button.html link="" text="Cite" %} {% include elements/button.html link="" text="Slides" %}
  </div>
    <br>

<li><a target="_blank" href="https://drive.google.com/file/d/1ZczptNNnywiKzt_1tex6fbo-_7oEgZLT/view">
          "ArP-Gen:Architectural Plan Generator"</a>, Tejas Vaidhya and Shubham Kumar Pandey <br>
           <b><u>Work in Progress</u></b>   <a style="float:right; color:#3491fe;" data-toggle="collapse" data-target="#pandu"><u>More</u> </a>
  </li>
    <div id="pandu" class="collapse" style="font-size:15px;margin:50px">In architecture, planning is a unique problem where the
goal is to generate mapping from the inputs, namely given site boundary, required building foot print and fundamental spatial program requirements. A lot of study has been already done in the area of generative algorithm in order to create spatial floor plan layouts with the help of iterative process. In this paper, we attempt to propose first end-to-end Architectural plan generation model called ArP-Gen: Architectural Plan Generator, that create architectural plan from basic user inputs like site boundary, entrance point, and room programming and new Spatial Mapping Task (SMT), which maps spatial or semantically segmented floor plans to detail architectural plan, learning detailing and room semantics. Our other contribution also include creation of precisely annotated and colour coded image data set for the purpose of mapping spatial plan to detailed architectural floor plan layout. Experiments and evaluation of output by architects demonstrate the potential of ArP-Gen framework to generate feasible Architectural solutions.

. <br> <br>
      {% include elements/button.html link="https://github.com/tejasvaidhyadev/ArP-GAN" text="Code" %} {% include elements/button.html link="https://drive.google.com/file/d/1ZczptNNnywiKzt_1tex6fbo-_7oEgZLT/view" text="Pdf" %} {% include elements/button.html link="" text="Cite" %} {% include elements/button.html link="https://indusfloorplan.web.app/home" text="Demo" %} {% include elements/button.html link="https://docs.google.com/document/d/1LK3FL8nfoGaVJ3TgtspceqNw1gqplbWoLUu6wKhWWPQ/edit" text="Motivation" %} 
  </div>
    <br>
    
</ul>
___


## **Experience**
<div class="row">
{% include about/timeline.html title="" source=site.data.education-timeline %}
</div >
*details of projects can be found* [here](projects/)  

___
<br>

## **Selected Projects**      

{% include projects/index.html %}
{% include elements/button.html link="projects/" text="Read More " block=true %}

___

You can check out the other things I do [here](Random/)

___

<br>
<div align="center" style="font-size: 80%">

	<i>iamtejasvaidhya@iitkgp.ac.in</i><br>
	<i>+91 9340004079</i>
</div>

