---
layout: tags
title: Archive
description: "An archive of posts sorted by tag."
permalink: /tags
---
{% capture site_tags %}{% for tag in site.tags %}{{ tag | first }}{% unless forloop.last %},{% endunless %}{% endfor %}{% endcapture %}
{% assign tags_list = site_tags | split:',' | sort %}
<ul style="margin-left:0">
  {% for item in (0..site.tags.size) %}{% unless forloop.last %}
  {% capture this_word %}{{ tags_list[item] | strip_newlines }}{% endcapture %}
    <a href="#{{ this_word }}" class="tag"><span class="term">{{ this_word }}</span><span class="count">{{ site.tags[this_word].size }}</span></a>
  {% endunless %}{% endfor %}
</ul>

{% for item in (0..site.tags.size) %}{% unless forloop.last %}
{% capture this_word %}{{ tags_list[item] | strip_newlines }}{% endcapture %}
<h3 id="{{ this_word }}" class="red-title">{{ this_word }}</h3>
<ul>
  {% for post in site.tags[this_word] %}{% if post.title != null %}
    <li class="entry-title"><a href="{{ post.url }}" title="{{ post.title }}">{{ post.title }}</a></li>
  {% endif %}{% endfor %}
</ul>
{% endunless %}{% endfor %}
