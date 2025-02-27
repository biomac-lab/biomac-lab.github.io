---
title: "Publications"
layout: gridlay
excerpt: "BIOMAC - Publications"
sitemap: false
permalink: publications/
lang: en
inheader_order: 3
---

# Publications

For a full list see [below](#full-list) 
<!-- [<i class="ai ai-researchgate"></i>  Research Gate](http://www.researchgate.net/profile/{{ site.resgate_username }}),
[<i class="ai ai-orcid"></i> Orcid](http://orcid.org/{{ site.orcid_username }}) <br>
Pre-prints are [here](#preprints) or on
[<i class="ai ai-arxiv"></i>  Arxiv](https://arxiv.org/a/{{ site.arxiv_username }}) and
[<i class="ai ai-biorxiv"></i>  Biorxiv](http://www.biorxiv.org/search/author1%3A{{ site.biorxiv_username }}) -->

## Highlights

{% assign number_printed = 0 %}
{% for publi in site.data.highlights %}

{% assign even_odd = number_printed | modulo: 2 %}

{% if even_odd == 0 %}
<div class="row">
{% endif %}

<div class="col-sm-6 clearfix">
 <div class="well">
  <pubtit>{{ publi.title }}</pubtit>
  <img src="{{ site.url }}{{ site.baseurl }}/images/pubpic/{{ publi.image }}" class="img-responsive" width="33%" style="float: left" />
  <p align = "justify"><em>{{ publi.description }}</em></p>
  <p>{{ publi.author }}<br /><strong><a target="_blank" href="http://doi.org/{{ publi.doi }}">{{ publi.journal }}{% if publi.volume != nil %} {{publi.volume}}{% endif %}{% if publi.number != nil %}({{publi.number}}){% endif %}{% if publi.pages != nil %}, {{publi.pages}}{% endif %} ({{publi.year}})</a> </strong></p>
  {% if publi.news %}<p><strong><em>News:</em></strong> {{ publi.news }}</p>{% endif %} 
  <div data-badge-popover="right" data-badge-type="bar" data-doi="{{ publi.doi }}" data-hide-no-mentions="true" class="altmetric-embed"></div>
 </div>
</div>

{% assign number_printed = number_printed | plus: 1 %}

{% if even_odd == 1 %}
</div>
{% endif %}

{% endfor %}

{% assign even_odd = number_printed | modulo: 2 %}
{% if even_odd == 1 %}
</div>
{% endif %}

{% assign total_pub = 0 %}

{% for publi in site.data.publist %}

{% if publi.preprint == 0 %}

{% assign total_pub = total_pub | plus: 1 %}

{% endif %}

{% endfor %}

<a name="full-list"></a>
## Full publications list

{% assign sorted_publist = site.data.publist | sort: "year" | reverse %}
{% assign current_year = 0 %}
{% for publi in sorted_publist %}
{% if publi.ENTRYTYPE == "article" %}
  {% if publi.year != current_year %}
  <h3>{{ publi.year }}</h3>
    {% assign current_year = publi.year %}
  {% endif %}
  <b>{{ publi.title }}</b> <br />
  {{ publi.author }}<br />
  <a target="_blank" href="http://doi.org/{{ publi.doi }}">{{ publi.journal }}{% if publi.volume != nil %} {{publi.volume}}{% endif %}{% if publi.number != nil %}({{publi.number}}){% endif %}{% if publi.pages != nil %}, {{publi.pages}}{% endif %} ({{publi.year}})</a> <br />
  <span style="display:inline;" class="__dimensions_badge_embed__" data-doi="{{ publi.doi }}" data-style="small_rectangle"></span><script async src="https://badge.dimensions.ai/badge.js" charset="utf-8"></script>
{% endif %}
{% endfor %}
