---
layout: page
title: Tags
showinmenu: true
page-last-updated: automatisch generiert
---

{% comment %}
--------------------------------------------------------------------
--- DEBUG list all pages and posts
<h2>site.pages</h2>
<ul>
{% for page in site.pages %}
	<li>{{ page.title }}</li>
{% endfor %}
</ul>

<h2>site.posts</h2>
<ul>
{% for post in site.posts %}
        <li>{{ post.title }}</li>
{% endfor %}
</ul>
---------------------------------------------------------------------
{% endcomment %}
	
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
			{% assign tags = tag | split:'|' | sort %}
		{% endif %}
		{% unless tags contains tag %}
			{% assign tags = tags | join:'|' | append:'|' | append:tag | split:'|' | sort %}
		{% endunless %}
	{% endif %}
{% endfor %}

{% comment %}
=======================
The purpose of this snippet is to list all the tags you have in your site.
=======================
{% endcomment %}
<ul>
{% for tag in tags %}
	<li><a class="tag" href="{{ tag | slugify }}">{{ tag }}</a></li>
{% endfor %}
</ul>

