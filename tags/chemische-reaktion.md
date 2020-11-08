---
title: Chemische Reaktion
layout: page
showinmenu: false
page-last-updated: automatisch generiert
---
{% assign tag_seite = "chemische-reaktion" %}

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

Also, count the number of results.
=======================
{% endcomment %}

{% assign pagecount = 0 %}
{% assign pages = site.pages | sort: 'title' %}
{% for page in pages %}
	 {% if page.tags contains tag_seite %}
	 	{% assign pagecount = pagecount | plus: 1 %}
	{% endif %}
{% endfor %}

<ul class="tags">
	<li>{{ pagecount }} Ergebnisse für <span class="tag">{{ tag_seite }}</span></li>
</ul>
<ul>
{% assign pages = site.pages | sort: 'title' %}
{% for page in pages %}
	 {% if page.tags contains tag_seite %}
	 {% assign pagecount = pagecount | plus: 1 %}	
	 <li>
	 <a href="{{ page.url }}">{{ page.title }}</a>
	 {% for tag in page.tags %}
		 <a class="tag" href="/tags/{{ tag | slugify }}">{{ tag }}</a>
	 {% endfor %}
	 </li>
	 {% endif %}
{% endfor %}
</ul>
