---
layout: page
title: About me
permalink: /about/
weight: 3
---

# **About Me**

Hi I am **Tejas Vaidhya** (you can call me Dev) :wave:,<br>
I am a Passionate Opensource developer currently in my third-year of undergraduation in the Department of Architecture and Regional Planning at IIT Kharagpur. I love Programming, Designing & Planning (after all i'm an architecture major), watching Anime, reading non-fiction, cooking, and finding new & interesting people.<br>
<br>
I have really enjoy my stay at IIT Kharagpur. I am fond of film making and Eating. In my free time I like to eat(you can find me in one of eateries of KGP). An enthusiast of Technologies and fascinate by how it affects life of people.


<div class="row">
{% include about/timeline.html title="Experience" source=site.data.education-timeline %}
</div >
*details of projects can be found* [here]()

#### Lets have a chat :mailbox_with_mail:
<div style="text-align: left;">
  {% if site.ajaxify_contact_form %}
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
