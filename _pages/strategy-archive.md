---
layout: archive
title: All Strategies
permalink: /strategy/archive.html
tag: 
---

The full list of strategies are included below:

<!-- Get the tag name for every tag on the site and set them to the `site_tags` variable. -->
{% capture site_tags %}{% for tag in site.tags %}{{ tag | first }}{% unless forloop.last %},{% endunless %}{% endfor %}{% endcapture %}

<!-- `tag_words` is a sorted array of the tag names. -->
{% assign tag_words = site_tags | split:',' | sort %}

<!-- List of all tags -->
<ul class="tags">
  {% for item in (0..site.tags.size) %}{% unless forloop.last %}
    {% capture this_word %}{{ tag_words[item] }}{% endcapture %}
    <li>
      <a href="#{{ this_word | cgi_escape }}" class="tag">{{ this_word }}
        <span>({{ site.tags[this_word].size }})</span>
      </a>
    </li>
  {% endunless %}{% endfor %}
</ul>

<div class="post-content">

<!-- Posts by Tag -->

{% for item in (0..site.tags.size) %}{% unless forloop.last %}
{% capture this_word %}{{ tag_words[item] }}{% endcapture %}
<h4 id="{{ this_word | cgi_escape }}">{{ this_word }}</h4>
    <ul>
{% assign elements = site.tags[this_word] | sort:"title"  %}    
{% for post in elements %}{% if post.title != null %}
<li>
<a href="{{ site.baseurl }}/{{ post.url }}">{{ post.title }}</a> - {{ post.description }}
</li>
{% endif %}{% endfor %}
</ul>
{% endunless %}{% endfor %}
</div>