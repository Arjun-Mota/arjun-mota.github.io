---
title: Tags
type: tags
summary: All the tags related to different topics available on this blog.
---

{% comment %}
  'site.tags' looks like a Map, e.g. site.tags.MyTag.[ Post0, Post1, ... ]
  Print the {{ site.tags }} will help you to understand it.
{% endcomment %}
<div id="tags" class="d-flex flex-wrap ml-xl-2 mr-xl-2">
{% assign sorted_tags_by_posts_count = site.tags | sort_tags_by_posts_count %}

{% for t in sorted_tags_by_posts_count %}
  <div>
    <a class="tag" href="{{ site.baseurl }}/tags/{{ t[0] | replace: ' ', '-' | downcase | url_encode }}/">{{ t[0] }}<span class="text-muted">{{ t[1] }}</span></a>
  </div>
{% endfor %}

</div>