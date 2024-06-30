---
layout: page
title: Blog
permalink: /blog
---

##### See my latest post...

{% assign post = site.posts.first %}
{% if post.title %}
[{{ post.title }}]({{ site.url }}{{ post.url }} "Internal link to my blog post: {{ post.title }}") posted on <span class="entry-date"><time datetime="{{ post.date | date_to_xmlschema }}" itemprop="datePublished"><strong>{{ post.date | date: "%A %e %B %Y" }}</strong></time></span>
{% endif %}

---

## Categories
<ul>
{% assign categories_list = site.categories %}
{% if categories_list.first[0] == null %}
  {% for category in categories_list %}
  <li><a href="#{{ category }}">{{ category | capitalize }} ({{ site.tags[category].size }})</a></li>
  {% endfor %}
{% else %}
  {% for category in categories_list %}
  <li><a href="#{{ category[0] }}">{{ category[0] | capitalize }} ({{ category[1].size }})</a></li>
  {% endfor %}
{% endif %}
{% assign categories_list = nil %}
</ul>

---

{% for tag in site.categories %}
## {{ tag[0] | capitalize }}
<ul>
  {% assign pages_list = tag[1] %}
  {% for post in pages_list %}
    {% if post.title != null %}
    {% if group == null or group == post.group %}
    <li> <span class="entry-date"><time datetime="{{ post.date | date_to_xmlschema }}" itemprop="datePublished">{{ post.date | date: "%A %e %B %Y" }}</time></span> - <a href="{{ site.url }}{{ post.url }}">{{ post.title }}</a></li>
    {% endif %}
    {% endif %}
  {% endfor %}
  {% assign pages_list = nil %}
  {% assign group = nil %}
</ul>
{% endfor %}


