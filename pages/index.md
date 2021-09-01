---
layout: default
permalink: /
---




<div class="row  align-items-left p-2">
  <div class="col-lg-4  p-5">
    <br>
    <!-- Fine Circle Responsive Image -->
    <div id="container" class="my-2">
      <div id="dummy"></div>
      <div id="element">
        <img src="{{ site.author.image }}" alt="{{ site.title }}" class="circle-image wow animated zoomIn" data-wow-delay=".1s">
      </div>
    </div>

    <p class="text-muted wow animated slideInUp" data-wow-delay=".15s">{{ site.description }}</p>

  </div>
  <div class="col-lg-8 p-4">
  
  
   <p style="font-size:30px"> <b>About me</b></p> 
    Hi, I'm Tejas Vaidhya 👋 <br>  
     I am currently in my senior year of Undergraduate studies at <a href="http://www.iitkgp.ac.in/"> Indian Institute of Technology, Kharagpur</a>. <br> 
    
    My research interests include Natural Language processing, Computer vision and Causal Inference. I am also highly interested to work on causality, explainability and Transformer based Language models. The goal of my research is to develop useful systems that work for the right reasons!  <br>
    
    I love Programming, Designing, and Planning. I also enjoy watching Anime, reading non-fiction, film making, cooking, and interacting with new people. I am a foodie. In my free time, I like to explore food (you can often find me in some of the eateries of KGP). I have always adored technology and am very much fascinated by how it affects the life of people.  
    
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/jpswalsh/academicons/css/academicons.min.css">     
    <br> <br> 
   <pre><a href="https://scholar.google.com/citations?user=dGedZKoAAAAJ&hl=en"> <i class="ai ai-google-scholar ai-2x"></i> </a>  <a href="https://twitter.com/imtejas13"> <i class="fab fa-2x fa-twitter"></i></a>   <a href="https://www.linkedin.com/in/tejas-vaidhya-0245b5157"> <i class="fab fa-2x fa-linkedin" href="url"></i> </a></pre>

  </div>
</div>

## **News** 
- **7 July 2021**: Attending [Eastern European Machine Learning Summer School, 2021](https://www.eeml.eu/home)  
- **1 May 2021**: Mentoring two project in [Google Summer of Code, 2021](https://github.com/AdarshKumar712/PPLM.jl) and [Julia Summer of Code, 2021](https://github.com/SambhawDrag/XLNet.jl).
- **1 March 2021**: Starting Research internship at [Mrinmaya's Lab, ETH Zürich](http://www.mrinmaya.io/)
- **14 Jan 2021**: Starting internship at [Uniworks Designs, Hyderabad](https://uniworksdesigns.com/) 
- **7 Jan 2021**: Paper accepted to the [CONSTRAINT](https://constraint-shared-task-2021.github.io/) workshop, collocated with AAAI 2021
- **6 October 2020**: paper accepted to EMNLP 2020, Workshop on [Noisy User-generated Text](http://noisy-text.github.io/2020/).
- **1 October 2020**: paper accepted to EMNLP 2020, Workshop on [Noisy User-generated Text](http://noisy-text.github.io/2020/).
- **12 September 2020**: Ranked 1st at the leaderboard for EMNLP 2020, W-NUT workshop Shared Task 3.  
<a style="float:right; color:#3491fe;" data-toggle="collapse" data-target="#news1"><u>More</u> </a>

<div id="news1" class="collapse" style="margin:20px">
<ul>
    <li> <b>12 September 2020</b>: Ranked 1st at the leaderboard for EMNLP 2020, W-NUT workshop Shared Task 3.  </li>
    <li> <b>31 August 2020</b>: Completed wonderful summer at <a href="https://summerofcode.withgoogle.com/archive/2020/projects/4810193256316928/"> Google Summer of Code</a></li>
    <li> <b>30 Jun 2020</b>: completed my research intern at <a href="https://home.cern"> CERN</a></li> 
</ul>     
 
</div>

<br>

___

  

  



## **Publications**

<ul>

<li><a target="_blank" href="https://www.aclweb.org/anthology/2020.wnut-1.79.pdf">
          "Leveraging Event Specific and Chunk Span features to Extract COVID Events from tweets"</a>, <br> <i>Ayush Kaushal and Tejas Vaidhya</i> <br>
          <b><u>Oral Presentation</u></b> at the 6th Workshop on Noisy User-generated Text (W-NUT) at the 2020 Conference on Emperical Methods in Natural Language Processing (EMNLP) <u><b>Shared Task Winners</b></u> <br>
          {% include elements/button.html link="https://github.com/Ayushk4/extract_covid_entity" text="<b>Code</b>" style="outline-dark" size="sm" %} {% include elements/button.html link="https://www.aclweb.org/anthology/2020.wnut-1.79.pdf" text="<b>Pdf</b>"  style="outline-dark" size="sm" %} {% include elements/button.html link="https://www.aclweb.org/anthology/2020.wnut-1.79.bib" text="<b>Cite</b>"   style="outline-dark" size="sm" %} {% include elements/button.html link="https://docs.google.com/presentation/d/13DDY6VSmrVPBddTjWb3rThYRFlRDE_9fi4iyBrhJev4/edit?usp=sharing" text="<b>Slides</b>"   style="outline-dark" size="sm"%} {% include elements/button.html link="https://github.com/noisy-text/noisy-text.github.io/blob/master/2020/posters/WNUT2020_91_poster%20-%20Tejas%20vaidhya.pdf" text="<b>Poster</b>"   style="outline-dark" size="sm" %} 
          <a style="float:right; color:#3491fe;" data-toggle="collapse" data-target="#covid"><u>More</u> </a>
  </li>
    <div id="covid" class="collapse" style="font-size:15px;margin:50px">Twitter has acted as an important source of information during disasters and pandemic, especially during the times of COVID-19. In this paper, we describe our system entry for <i>WNUT 2020 Shared Task-3</i>. The task was aimed at automating the extraction of a variety of COVID-19 related events from Twitter, such as individuals who recently contracted the virus, someone with symptoms who were denied testing and believed remedies against the infection. The system consists of separate multi-task models for slot-filling subtasks and sentence-classification subtasks while leveraging the useful sentence-level information for the corresponding event. The system uses COVID-Twitter-Bert with attention-weighted pooling of candidate slot-chunk features to capture the useful information chunks. The system ranks <b>1st at the leader-board</b> with F1 of 0.6598, without using any ensembles or additional datasets. <br> 
  </div>
    <br>



<li><a target="_blank" href="https://www.aclweb.org/anthology/2020.wnut-1.34.pdf">
          "Domain specific BERT representation for Named Entity Recognition of lab protocol."</a>, <br> <i>Tejas Vaidhya and Ayush Kaushal</i> <br>
           Proceedings of the 6th Workshop on Noisy User-generated Text (W-NUT) at the 2020 Conference on Emperical Methods in Natural Language Processing (EMNLP)  <br>

           {% include elements/button.html link="https://github.com/tejasvaidhyadev/W-NUT_2020" text="<b>Code</b>" style="outline-dark" size="sm" %} {% include elements/button.html link="https://www.aclweb.org/anthology/2020.wnut-1.34.pdf" text="<b>Pdf</b>"  style="outline-dark" size="sm" %} {% include elements/button.html link="https://www.aclweb.org/anthology/2020.wnut-1.34.bib" text="<b>Cite</b>"   style="outline-dark" size="sm" %} {% include elements/button.html link="https://github.com/noisy-text/noisy-text.github.io/blob/master/2020/posters/WNUT2020_92_poster%20-%20Tejas%20vaidhya.pdf" text="<b>Poster</b>"   style="outline-dark" size="sm" %}
 
  <a style="float:right;color:#3491fe" data-toggle="collapse" data-target="#wetlab"><u>More</u></a>
           

  </li>
    <div id="wetlab" class="collapse" style="font-size:15px;margin:50px">
    <!-- <br>
    <div align="center">
        <img id="mobile-img" src="../images/Bio-BERT.png" width="50%" border="0" height="50%" alt=""><br>
        </div> -->
        Supervised models trained to predict properties from representations, have been achieving high accuracy on a variety of tasks. For instance, the BERT family seems to work exceptionally well on the downstream task from NER tagging to the range of other linguistic tasks. But the vocabulary used in the medical field contains a lot of different tokens used only in the medical industry such as the name of different diseases, devices, organisms, medicines, etc. that makes it difficult for traditional BERT model to create contextualized embedding. In this paper, we are going to illustrate the System for Named Entity Tagging based on Bio-Bert. Experimental results show that our model gives substantial improvements over the baseline and stood the fourth runner up in terms of F1 score, and first runner up in terms of Recall among 13 teams with just 2.21 F1 score behind the best one.
        <br> <br>
    </div>
    <br>



<li><a target="_blank" href="https://arxiv.org/pdf/2101.05494.pdf">
          "Hostility Detection in Hindi leveraging Pre-Trained Language Models"</a>, <br> <i> Ojasv Kamal, Adarsh Kumar, and Tejas Vaidhya</i> <br>
           <b><u>Oral Presentation</u></b> at the Constraint workshop at Advancement Of Artificial Intelligence <br> {% include elements/button.html link="https://github.com/kamalojasv181/Hostility-Detection-in-Hindi-Posts" text="<b>Code</b>" style="outline-dark" size="sm" %} {% include elements/button.html link="https://arxiv.org/pdf/2101.05494.pdf" text="<b>Pdf</b>"  style="outline-dark" size="sm" %} {% include elements/button.html link="" text="<b>Cite</b>"   style="outline-dark" size="sm" %} {% include elements/button.html link="" text="<b>Slides</b>"   style="outline-dark" size="sm" %} 
           <a style="float:right; color:#3491fe;" data-toggle="collapse" data-target="#fakenews"><u>More</u> </a>
           
  </li>
    <div id="fakenews" class="collapse" style="font-size:15px;margin:50px">Hostile content on social platforms is ever increasing. This
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
F1 Score1. <br> 
  </div>
    <br>

<li><a target="_blank" href="https://github.com/jharkawat/meddoprof_shared_task">
          "Spanish Pre-Trained Language Models for HealthCare Industry"</a>, <br> <i>Tejas Vaidhya and Jalaj Harkawat</i><br>
           <b><u>Oral Presentation</u></b> at Proceedings of the Iberian Languages Evaluation Forum  <br> {% include elements/button.html link="https://github.com/jharkawat/meddoprof_shared_task" text="<b>Code</b>" style="outline-dark" size="sm" %} {% include elements/button.html link="" text="<b>Pdf</b>"  style="outline-dark" size="sm" %} {% include elements/button.html link="" text="<b>Cite</b>"   style="outline-dark" size="sm" %} {% include elements/button.html link="" text="<b>Slides</b>"   style="outline-dark" size="sm" %} 
           <a style="float:right; color:#3491fe;" data-toggle="collapse" data-target="#beto"><u>More</u> </a>
 

  </li>
    <div id="beto" class="collapse" style="font-size:15px;margin:50px">Currently transformer based model have shown high accuracy and good prediction on downstream tasks like Named Entity Recognition, Sentiment analysis etc. But the terminologies used in Healthcare sector such as names of different diseases, medicines and departments makes it difficult to predict with high accuracy. In this paper we are going to show a system for Named Entity tagging based on BETO (SpanishBERT). Experimental results have shown that our model gives better results than the current baseline of MEDDOPROF Shared task. <br> 
      
  </div>
    <br>

<li><a target="_blank" href="https://drive.google.com/file/d/1UDGujYmKUzDRFgLbvF355URmxiEyoMXv/view">
          "Causal Direction in Data Matters: Implications of Causal and Anticausal Learning in NLP"</a>, <br> <i>Zhijing Jin, Julius von KÃgelgenâ, Jingwei Ni, Tejas Vaidhya, Ayush Kaushal, Mrinmaya Sachan and Bernhard Schoelkopf</i><br>
          <b><u>Long Paper</u></b> at the 2021 Conference on Emperical Methods in Natural Language Processing (EMNLP)<br>   {% include elements/button.html link="" text="<b>Code</b>" style="outline-dark" size="sm" %} {% include elements/button.html link="https://drive.google.com/file/d/1UDGujYmKUzDRFgLbvF355URmxiEyoMXv/view" text="<b>Pdf</b>"  style="outline-dark" size="sm" %} {% include elements/button.html link="" text="<b>Cite</b>"   style="outline-dark" size="sm" %} {% include elements/button.html link="" text="<b>Slides</b>"   style="outline-dark" size="sm" %}
          <a style="float:right; color:#3491fe;" data-toggle="collapse" data-target="#emnlp"><u>More</u> </a>
  </li>
    <div id="emnlp" class="collapse" style="font-size:15px;margin:50px">descriptionThe principle of independent causal mechanisms (ICM) states that generative processes of real-world data consist of independent modules which do not influence or inform each other. While this idea has led to fruitful developments in the field of causal inference, it is not widely known in the NLP community. In this work, we argue that the causal direction of the data collection process bears non trivial implications that can explain a number of published NLP findings, such as differences in semi-supervised learning (SSL) and domain adaptation (DA) performance across different settings. We categorize common NLP tasks according to their causal direction and empirically assay the validity of the ICM principle for text data using minimum description length. We conduct an extensive meta-analysis of over 100 (SSL) and 30 (DA) published studies, and find that the results are consistent with our expectations based on causal insights. This work presents the first attempt to analyze the ICM principle in NLP, and provides constructive suggestions for future modelling choices
. <br> 
      
 </div>
    <br>

<li><a target="_blank" href="https://drive.google.com/file/d/12-hJeIqjMx-GnfjXf3E6vcVYlamN5yoR/view?usp=sharing">
          "Mining the Cause of Political Decision-Making from Social Media: A Case Study of COVID-19 Policies across the US States"</a>, <br> <i> Zhijing Jin, Zeyu Peng, Tejas Vaidhya, Bernhard Schoelkopf and Rada Mihalcea</i><br>
          <b><u>Findings of EMNLP</u></b> at the 2021 Conference on Emperical Methods in Natural Language Processing (EMNLP) <br>
             {% include elements/button.html link="" text="<b>Code</b>" style="outline-dark" size="sm" %} {% include elements/button.html link="https://drive.google.com/file/d/12-hJeIqjMx-GnfjXf3E6vcVYlamN5yoR/view?usp=sharing" text="<b>Pdf</b>"  style="outline-dark" size="sm" %} {% include elements/button.html link="" text="<b>Cite</b>"   style="outline-dark" size="sm" %} {% include elements/button.html link="" text="<b>Slides</b>"   style="outline-dark" size="sm" %} 
             <a style="float:right; color:#3491fe;" data-toggle="collapse" data-target="#emnlp21"><u>More</u> </a>

  </li>
    <div id="emnlp21" class="collapse" style="font-size:15px;margin:50px">Mining the causes of political decision making is an active research area in the field of political science. In the past, most studies have focused on long-term policies that are collected over several decades of time, and have primarily relied on surveys as the main source of predictors. However, the recent COVID 19 pandemic has given rise to a new political phenomenon, where political decision-making consists of frequent short-term decisions, all on the same controlled topic—the pandemic. In this paper, we focus on the question of how public opinion influences policy decisions while controlling for covariates such as COVID-19 case increases or unemployment rates. Using a dataset consisting of Twitter data from the 50 US states, we classify the sentiments toward governors of each state, and conduct controlled studies and comparisons. Based on the compiled samples of sentiments, policies, and covariates, we conduct causal inference to discover trends in political decision making across different states


. <br> 
  </div>

<br>

<li><a target="_blank" href="https://drive.google.com/file/d/1ZczptNNnywiKzt_1tex6fbo-_7oEgZLT/view">
          "ArP-Gen:Architectural Plan Generator"</a>, <br> <i> Tejas Vaidhya and Shubham Kumar Pandey </i><br>
           <b><u>Work in Progress</u></b>   <br>
  {% include elements/button.html link="https://github.com/tejasvaidhyadev/ArP-GAN" text="<b>Code</b>" style="outline-dark" size="sm" %}  {% include elements/button.html link="https://drive.google.com/file/d/1ZczptNNnywiKzt_1tex6fbo-_7oEgZLT/view" text="<b>Pdf</b>"  style="outline-dark" size="sm" %} {% include elements/button.html link="" text="<b>Cite</b>"   style="outline-dark" size="sm" %} {% include elements/button.html link="https://indusfloorplan.web.app/home" text="<b>Demo</b>"   style="outline-dark" size="sm" %} <a style="float:right; color:#3491fe;" data-toggle="collapse" data-target="#pandu"><u>More</u> </a>

  </li>
    <div id="pandu" class="collapse" style="font-size:15px;margin:50px">In architecture, planning is a unique problem where the
goal is to generate mapping from the inputs, namely given site boundary, required building foot print and fundamental spatial program requirements. A lot of study has been already done in the area of generative algorithm in order to create spatial floor plan layouts with the help of iterative process. In this paper, we attempt to propose first end-to-end Architectural plan generation model called ArP-Gen: Architectural Plan Generator, that create architectural plan from basic user inputs like site boundary, entrance point, and room programming and new Spatial Mapping Task (SMT), which maps spatial or semantically segmented floor plans to detail architectural plan, learning detailing and room semantics. Our other contribution also include creation of precisely annotated and colour coded image data set for the purpose of mapping spatial plan to detailed architectural floor plan layout. Experiments and evaluation of output by architects demonstrate the potential of ArP-Gen framework to generate feasible Architectural solutions.

. <br> 
      
</div>
    <br>
    
</ul>
___



## **Experience**
<div class="row">
{% include about/timeline.html title="" source=site.data.education-timeline %}
</div >
*details of projects can be found* [**here**](projects/)  

___
<br>

## **Selected Projects**      

{% include projects/index.html %}
{% include elements/button.html link="projects/" text="**Read More**" block=true %}

___

You can check out the other things I do [**here**](Random/)

___

<br>
<div align="center" style="font-size: 80%">

	<i>iamtejasvaidhya@iitkgp.ac.in</i><br>
	<i>+91 9340004079</i>
</div>

