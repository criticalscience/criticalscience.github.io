---
layout: page
title: Bibliography
permalink: /bibliography
---

Here, we include a bibliography that has served or could serve as inspiration for our discussions. It is sorted by chronological order.

---

{% assign bibliography = site.data.bibliography | sort: 'year' %}
{% for item in bibliography %}
  {% include bibliography-item.html %}
{% endfor %}
