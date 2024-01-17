---
title: Tags
type: tags
summary: All the tags related to different topics available on this blog.
---

<div id="tags" class="d-flex flex-wrap ml-xl-2 mr-xl-2">

{% capture site_tags %}
  {% for tag in site.tags %}
    {{ tag[1].size | plus:10000 }}#{{ tag | first | downcase }}#{{ tag | first }}{% unless forloop.last %},{% endunless %}
  {% endfor %}
{% endcapture %}

{% assign tag_hashes = site_tags | split:',' | sort | reverse %} 

<div>
{% for hash in tag_hashes %}
  {% assign keyValue = hash | split: '#' %}
  {% capture tag_word %}{{ keyValue[2] | strip_newlines | strip}}{% endcapture %}
    <a class="tag" href="{{ site.baseurl }}/tags/{{ tag_word | replace: ' ', '-' | downcase | url_encode }}/">{{ tag_word }}<span class="text-muted">{{ site.tags[tag_word].size }}</span></a>
{% endfor %}
</div>
</div>