---
layout: page
title: Events and sessions
permalink: /events
---
{% assign today = 'now' | date: "%Y-%m-%d" %}
{% assign future_events = "" | split: "," %}
{% assign past_events = "" | split: "," %}

{% for event in site.data.events %}
  {% assign event_date = event.date | date: "%Y-%m-%d" %}
  {% if event_date > today %}
      {% assign future_events = future_events | push: event %}
  {% else %}
      {% assign past_events = past_events | push: event %}
  {% endif %}
{% endfor %}

## Coming up
{% assign events = future_events | sort: 'date' %}
{% if events.size == 0 %}
There are not currently any planned events. Stay tuned!
{% else %}
  {% for event in events %}
  {% include event.html %}
  {% endfor %}
{% endif %}

## In the past
{% assign events = past_events | sort: 'date' | reverse %}
{% for event in events %}
  {% include event.html %}
{% endfor %}
