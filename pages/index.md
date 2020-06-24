---
layout: default
permalink: /
---
<br>

{% include landing.html %}





## **About Me**

Hello, I am Tejas Vaidhya (you can also call me Dev):wave:,<br> I am an Undergrad Researcher, Passionate Opensource developer, and a tech enthusiast. I am currently in my third year of Undergraduate studies, pursuing my major in Bachelor of Architecture and Planning and Minor in Mathematics and Computing at IIT Kharagpur. <br>
My research interest lies in Computer vision and Natural language processing. Currently, I am researching on Probing techniques for Transformer based model.<br>
I love Programming, Designing, and Planning (Afterall I am an architecture major). I also enjoy watching Anime, reading non-fiction, film making, cooking, and interacting with new people. I am a foodie. In my free time, I like to explore food (you can often find me in some of the eateries of KGP). I have always adored technology and am very much fascinated by how it affects the life of people.<br>

<br>
<br>
<br>
<br>
<br>


<div class="row">
{% include about/timeline.html title="Experience" source=site.data.education-timeline %}
</div >
*details of projects can be found* [here](projects/)

<br>
<br>
### Curated Projects      

{% include projects/index.html %}
{% include elements/button.html link="projects/" text="Read More " block=true %}
###### You can check out the other things I do [here](Random/)



<br>
<br>
<br>




<div style="text-align: center;font-size:180%;">
<b> Lets have a chat :mailbox_with_mail:</b>
</div>

<div style="text-align: center;font-size:140%;">
  {% if site.ajaxify_contact_form %}
  <br>
  <br>
    <form class="form-stacked">
      <label>
        Email
        <input type="text" name="email" class="field-light" placeholder="{{ site.text.contact.email | default: "Email Address" }}">
      </label>
        <br>

      <label>
        Content
        <textarea type="text" name="content" rows="5" placeholder="{{ site.text.contact.content | default: "What would you like to say?" }}" style="resize: vertical"></textarea>
      </label>

      <input type="text" name="_gotcha" style="display:none" />

      <button type='submit' class="button button-blue button-big mobile-block">{{ site.text.contact.submit | default: "Say Hello" }}</button>
    </form>
  {% else %}
    <form action="https://formspree.io/myynpjpw" method="POST" class="form-stacked">
      <label >
        Email
        <br>
        <input type="text" name="email" style="field-light" placeholder="{{ site.text.contact.email | default: "Email Address" }}">
      </label>
      <br>
      <label>
        Content
        <br>
        <textarea type="text" name="content" class="field-light" rows="5" placeholder="{{ site.text.contact.content | default: "What would you like to say?" }}" style="resize: vertical"></textarea>
      </label>

      <input type="hidden" name="_next" value="{{ site.baseurl }}/thanks/" />
      <input type="hidden" name="_subject" value="{{ site.text.contact.subject | default: "New submission!" }}" />
      <input type="text" name="_gotcha" style="display:none" />
      <br>
      <input type="submit" class="button button-blue button-big mobile-block" value="{{ site.text.contact.submit | default: "Say Hello" }}">
    </form>
  {% endif %}

 {% if site.ajaxify_contact_form %}
  {% include ajaxify_content_form.html %}
{% endif %}

</div>

<br>
<br>
<div align="center" style="font-size: 80%">
	<i>iamtejasvaidhya@iitkgp.ac.in</i><br>
	<i>+91 9340004079</i>
</div>