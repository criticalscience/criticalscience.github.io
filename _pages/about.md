---
layout: page
title: About us
permalink: /about
---
We are a group of students, postdocs, professors and research scientists at Mila interested in educating ourselves and the wider community at our organisation about the interconnection between science, technology and society.

These are some of the folks co-organising the reading group, in random order:

{% assign people = site.data.team | sample: site.data.team.size %}
{% for person in people %}
  {% assign side = forloop.index0 | modulo: 2 %}
    {% if side == 0 %}
      {% include team-card.html %}
    {% else %}
      {% include team-card.html %}
    {% endif %}
{% endfor %}
