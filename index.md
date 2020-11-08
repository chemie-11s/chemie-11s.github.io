---
title: Chemie 11s
layout: page
showinmenu: false
page-last-updated: 2020-11-08
---

## Themen

{% comment %}
1. Atommodelle, Redoxreaktionen, Elektrochemie
	- [1.1 Atommodelle](themen/atommodelle) <a class="tag" href="/tags/atommodelle">atommodelle</a>
	- [1.2 Redoxreaktionen](themen/redoxreaktionen) <a class="tag" href="/tags/redoxreaktionen">redoxreaktionen</a>
	- 1.3 Elektrochemie 
		- [1.3.1 Galvanische Elemente](themen/galvanische-elemente) <a class="tag" href="/tags/galvanische-elemente">galvanische-elemente</a>
		- [1.3.2 Korrosion](themen/korrosion) <a class="tag" href="/tags/korrosion">korrosion</a>
		- [1.3.3 Elektrolyse](themen/elektrolyse) <a class="tag" href="/tags/elektrolyse">elektrolyse</a>
		- [1.3.4 Stromquellen](themen/stromquellen) <a class="tag" href="/tags/stromquellen">stromquellen</a>
2. Chemische Bindung, Organische Chemie
	- [2.1 Chemische Bindung](themen/chemische-bindung) <a class="tag" href="/tags/chemische-bindung">chemische-bindung</a>
	- [2.2 Organische Chemie](themen/organische-chemie) <a class="tag" href="/tags/organische-chemie">organische-chemie</a>
	- [2.3 Fette und Tenside](themen/fette-und-tenside) <a class="tag" href="/tags/fette-und-tenside">fette-und-tenside</a>
3. Chemische Gleichgewichte
	- [3.1 Reaktionsverlauf und Reaktionsgeschwindigkeit](themen/reaktionsverlauf-und-reaktionsgeschwindigkeit) <a class="tag" href="/tags/reaktionsverlauf-und-reaktionsgeschwindigkeit">reaktionsverlauf-und-reaktionsgeschwindigkeit</a>
	- [3.2 Chemisches Gleichgewicht](themen/chemisches-gleichgewicht) <a class="tag" href="/tags/chemisches-gleichgewicht">chemisches-gleichgewicht</a>
	- [3.3 Säure-Base-Gleichgewichte](themen/säure-base-gleichgewichte) <a class="tag" href="/tags/säure-base-gleichgewichte">säure-base-gleichgewichte</a>
	- [3.4 Titrationen](themen/titrationen) <a class="tag" href="/tags/titrationen">titrationen</a>
4. [4a Thermochemie](themen/thermochemie) <a class="tag" href="/tags/thermochemie">thermochemie</a>  
   [4b Komplexchemie und Qualitative Analyse](themen/komplexchemie-und-qualitative-analyse) <a class="tag" href="/tags/komplexchemie">komplexchemie</a>
{ %endcomment% }

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

<ol>
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
</ol>

## Anforderungen

1. Im gA-Kurs müsst ihr von 5 Themenkomplexen insgesamt 4 bearbeiten. Von den Bereichen **Thermochemie** und **Komplexchemie und Qualitative Analyse** 
muss einer zur Bearbeitung gewählt werden.<br />

2. Aufgaben pro Halbjahr
	- 11/I: 4 Experimente + 1 LK + Vollständigkeit der Unterlagen (ca. 18 Wochen)
	- 11/II: 4 Experimente + 1 LK + Vollständigkeit der Unterlagen (ca. 15 Wochen)
	- 12/I: 4 Experimente + 1 LK + Vollständigkeit der Unterlagen (ca. 15 Wochen)
	- 12/II: 3 Experimente + 1 LK + Vollständigkeit der Unterlagen (ca. 12 Wochen)<br /><br />  
	- Summe: **15 Experimente** + 1 LK pro Halbjahr + 4 Noten für die Unterlagen (ca. 60 Wochen)<br />

3. <a class="tag" href="/tags/pflichtexperiment">Pflichtexperimente</a> sind zuerst zu bearbeiten.

4. Einmalig muss ein <a class="tag" href="/tags/wahlexperiment">Wahlexperiment</a> vorbereitet, im Chemiekurs vorgestellt und ausgewertet werden. Diese Note zählt als Experiment. <br />

4. Bei Interesse kann __nach Rücksprache__ ein Pflichtexperiment durch ein Wahlexperiment zu einem verwandten Thema bearbeitet werden.

5. Der Termin für die LK wird zu Beginn eines Halbjahres bekanntgegeben. Die Aufgaben beziehen sich auf die von euch in diesem Halbjahr bis zu diesem Termin bearbeiteten Themen bzw. Experimente.

6. Insgesamt stehen euch ca. 60 Doppelstunden (bzw. Wochen) zur Verfügung. Je nach Thema und euren Vorkenntnissen kann es 
allerdings sein, dass ihr mehr oder auch weniger Zeit benötigt. Das ist gewollt. Wichtig ist, dass ihr **nicht wesentlich** länger braucht.<br />
	Die 60 Doppelstunden verteilen sich **ungefähr** wie folgt:

	1. Atommodelle, Redoxreaktionen, Elektrochemie (**22 Doppelstunden**)
	2. Chemische Bindung, Organische Chemie (**18 Doppelstunden**)
	3. Chemische Gleichgewichte (**15 Doppelstunden**)
	4. Thermochemie/Komplexchemie (**5 Doppelstunden**)

## Bearbeitung eines Themas - Vollständigkeit der Unterlagen

1. Thema erfassen: Lest die Themenseite und macht euch mit Lernzielen, Materialien und den zugehörigen Experimenten vertraut
2. Planung: __Arbeitsplan__ erstellen und im Formular eintragen
3. Arbeit am Thema
4. __Lerntagebuch__: jede Stunde, Lernerfolg einschätzen, Aufgaben und Fragen für die Folgewoche notieren
5. Rückblick: __Selbsteinschätzung__ 

**Vollständige Unterlagen**
- Lerntagebuch
- Arbeitsplan und Selbsteinschätzung pro Thema
- Aufzeichnungen, Übungen, Arbeitsblätter








