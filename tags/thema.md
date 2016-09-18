---
title: Themen
layout: page
showinmenu: true
---

{% comment %}
=======================
The following part extracts all the tags from your posts and sort tags, so that you do not need to manually collect your tags to a place.
=======================
{% endcomment %}
{% assign rawtags = "" %}
{% for page in site.pages %}
	{% assign ttags = page.tags | join:'|' | append:'|' %}
	{% assign rawtags = rawtags | append:ttags %}
{% endfor %}
{% assign rawtags = rawtags | split:'|' | sort %}

{% comment %}
=======================
The following part removes duplicated tags and invalid tags like blank tag.
=======================
{% endcomment %}
{% assign tags = "" %}
{% for tag in rawtags %}
	{% if tag != "" %}
		{% if tags == "" %}
			{% assign tags = tag | split:'|' %}
		{% endif %}
		{% unless tags contains tag %}
			{% assign tags = tags | join:'|' | append:'|' | append:tag | split:'|' %}
		{% endunless %}
	{% endif %}
{% endfor %}


{% comment %}
=======================
The purpose of this snippet is to list all your posts posted with a certain tag.
=======================
{% endcomment %}
{% assign tag = "thema" %}
<ul class="tags">
	<li style="float: left; margin-right: 1em;">Seiten getaggt mit</li>
	<li class="tag">{{ tag }}</li>
</ul>
<ul>
{% assign pages = site.pages | sort: 'title' %}
{% for page in site.pages | sort: 'title' %}
	 {% if page.tags contains tag %}
	 <li>
	 <a href="{{ page.url }}">{{ page.title }}</a>
	 {% for tag in page.tags %}
		 <a class="tag" href="/tags/{{ tag | slugify }}">{{ tag }}</a>
	 {% endfor %}
	 </li>
	 {% endif %}
{% endfor %}
</ul>
