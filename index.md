---
title: Chemie 11s
layout: page
showinmenu: false
page-last-updated: 2020-11-08
---

## Themen

{% comment %}
=======================
Im Folgenden wird automatisch eine Liste der Themen generiert. Selber Algorithmus wie auf den Tag-Seiten. Möglicherweise komplizierter als notwendig.
=======================
{% endcomment %}

{% assign tag_seite = "thema" %}

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

<ol style="list-style-type: none;">
{% assign pages = site.pages | sort: 'title' %}
{% for page in pages %}
	 {% if page.tags contains tag_seite %}
	 {% assign pagecount = pagecount | plus: 1 %}	
	 <li>
	 	<a href="{{ page.url }}">{{ page.title }}</a>
	 </li>
	 {% endif %}
{% endfor %}
</ol>

## Ablauf und Anforderungen

1. Im laufenden Schuljahr 2020/2021 stehen voraussichtlich in den geraden Wochen 13 Unterrichtstermine zur Verfügung (Stand November 2020).
2. Zusatztermine zum Arbeiten und Fragen stellen: bis auf Weiteres Mittwoch 7. Stunde.
3. Auf jeder Themenseite findet ihr die Lernziele und dazu passende Materialien.
4. 7 Themen - 7 Noten: jeweils 50 % Sachkompetenz und 50 % Arbeitsprozess (Lernverhalten und Beitrag zur Arbeitsatmosphäre).
5. 5 Experimente: 1 zusätzliche Experimentiernote pro Halbjahr für Durchführung, Protokoll, Ordnung und Beachtung der Sicherheitsbestimmungen.










