---

layout: page
header: h-gradient-pink
title: Applications of the Online Learning Model
permalink: /applications/

---

The Online Learning Model can be implemented in a variety of different ways. It's flexibility means that it can be applied to any subject, regardless of discipline or the size and shape of the student cohort. Each of the [strategies]({{site.baseurl}}/strategies) can be fitted together with others to form profiles that are tailored to suit the nature of the learning and teaching required for that subject. This area will provide an insight into how that can be achieved by providing more in-depth information about how the OLM has been utilised and applied.

The case studies shared here offer an expanded view of how the Online Learning Model has been adopted and incorporated into a subject. It is important to understand the elements as not working towards isolated objectives, but working together to provide a learning infrastructure across the entire subject. Each case study shares at least two elements that have been integrated into learning and teaching objectives to support engagement of students and teachers. Putting a stronger lens on subjects provides more meaningful understanding of the dynamics within a subject and encouragement to others to adopt OLM elements.


### Case Studies

{% assign application-list =  site.applications | map: 'category' | join: ','  | split: ',' | uniq | sort %}
<div class="box-container-rows extra-padding">
  {% for item in application-list %}
    {% if item.size >0 %}
      <a href="{{ site.baseurl }}/applications/{{ item | slugify }}/">
        <div class="box gradient-purple white">{{ item }}</div>
      </a>
    {% endif %}
  {% endfor %}
</div>
