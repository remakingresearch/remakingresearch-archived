---
layout: page
title: Organizers
---

<!-- choose random first organizer and have that set the order -->
{% assign min = 1 %}
{% assign max = site.data.organizers.size %}
{% assign diff = max | minus: min %}
{% assign random_number = "now" | date: "%s" | modulo: diff | plus: min %}

{% assign organizers = site.data.organizers %}
{% assign sorted_organizers = '' | split: '' %}
{% assign organizer_count = random_number %}

{% for counter in (min..max) %}
  {% assign array_end = organizer_count | modulo: 3 %}
  {% if array_end == 0 %}
    {% if organizer_count == 0 %}
      {% assign organizer_count = organizer_count | plus: 1 %}
    {% else %}
      {% assign organizer_count = organizer_count | minus: 3 %}
    {% endif %}
  {% else %}
    {% assign organizer_count = organizer_count | plus: 1 %}
  {% endif %}
  {% assign sorted_organizers = sorted_organizers | push: organizers[organizer_count] %}
{% endfor %}

<div class="section section-updates">
  <div class="container grid-lg">
      <div class="column col-6">
      {% for organizer in sorted_organizers %}
        {% include organizer-card.html %}
      {% endfor %}
      </div>
  </div>
</div> 
