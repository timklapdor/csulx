---

layout: archive
title: All Strategies
permalink: /strategy/archive.html
tag:
header: h-gradient-purple

---

The full list of strategies are included below:

{% comment %}map, flatten and sort{% endcomment %}
{% assign tags =  site.strategies | map: 'tags' | join: ','  | split: ',' | sort %}
{% assign previousTag = "" %}
{% assign counter = 0 %}

<div id="tag-list">

<!-- List of all tags -->

<ul class="tags">
{% for currentTag in tags %}

  {% comment %}first loop : initializing previousTag{% endcomment %}
  {% if previousTag == "" %}
    {% assign previousTag = currentTag %}
  {% endif %}

  {% if currentTag == previousTag %}
    {% assign counter = counter | plus: 1 %}
  {% else %}
    <li><h6><a href="#{{ previousTag | slugify: 'pretty' }}" class="tag">{{ previousTag }}  <span>({{ counter }})</span></a></h6></li>
    {% assign counter = 1 %}
  {% endif %}

  {% comment %}last loop : flushing what's left to print{% endcomment %}
  {% if forloop.last %}
    <li><h6><a href="#{{ currentTag | slugify: 'pretty'}}" class="tag"><span>{{ currentTag }} ({{ counter }})</span></a></h6></li>
  {% endif %}

  {% assign previousTag = currentTag %}

{% endfor %}
</ul>

</div>

<!-- Posts by Tag -->


{% assign collection_tags =  site.strategies | map: 'tags' | join: ','  | split: ',' | uniq | sort %}

{% for tag in collection_tags %}
  <h4 id="{{ tag | slugify: 'pretty' }}">{{ tag }}</h4>
  <ul>
  {% for strategies in site.strategies %}
    {% if strategies.tags contains tag %}
    <li><a href="{{ site.baseurl }}{{ strategies.url }}">{{ strategies.title }}</a></li>
    {% endif %}
  {% endfor %}
  </ul>
{% endfor %}
