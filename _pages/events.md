---
layout: page
title: Events and sessions
permalink: /events
---
Currently, the sessions of the reading group take place every other Friday at 16:00 at Mila. Occasionally, we also host certain sessions at other time slots.

By attending the sessions of the reading group, participants are requested to follow the [Berlin Code of Conduct](https://berlincodeofconduct.org/en).

{% assign events = site.data.events | sort: 'date' %}

## Coming up

<p id="no-upcoming" hidden>There are not currently any planned events. Stay tuned!</p>
<div id="upcoming-events"></div>

## In the past

The list of past events is still incomplete. In the meantime, you can see the complete list of past sessions on the previous page of the [Against Military AI Reading Group](https://sun-curtain-9a1.notion.site/Against-Military-AI-RG-e25479293a6041c7aabe399842bdf324).
<div id="past-events"></div>

<div id="all-events">
{% for event in events %}
  {% include event.html %}
{% endfor %}
</div>

<script>
// Build the two sections from the visitor's current date, since the site is
// only rebuilt on push and a Liquid split would use the build date. Without
// JavaScript, all events remain in #all-events as a single chronological list.
(function () {
  var today = new Date().toISOString().slice(0, 10);
  var items = Array.prototype.slice.call(document.querySelectorAll('#all-events .content[data-date]'));
  var upcoming = document.getElementById('upcoming-events');
  var past = document.getElementById('past-events');

  items.sort(function (a, b) { return a.dataset.date < b.dataset.date ? -1 : 1; });
  items.forEach(function (el) {
    if (el.dataset.date > today) { upcoming.appendChild(el); }
  });
  items.reverse().forEach(function (el) {
    if (el.dataset.date <= today) { past.appendChild(el); }
  });

  document.getElementById('no-upcoming').hidden = upcoming.children.length > 0;
  document.getElementById('all-events').remove();
})();
</script>
