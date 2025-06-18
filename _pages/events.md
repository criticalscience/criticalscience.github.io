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

Currently, the sessions of the reading group take place every other Friday at 16:00 at Mila.

By attending the sessions of the reading group, participants are requested to follow the [Berlin Code of Conduct](https://berlincodeofconduct.org/en).

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
The list of past events is still incomplete. In the meantime, you can see the complete list of past sessions on the previous page of the [Against Military AI Reading Group](https://sun-curtain-9a1.notion.site/Against-Military-AI-RG-e25479293a6041c7aabe399842bdf324).
{% assign events = past_events | sort: 'date' | reverse %}
{% for event in events %}
  {% include event.html %}
{% endfor %}
