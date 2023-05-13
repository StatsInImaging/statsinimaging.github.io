---
layout: page
title: "Officers"
permalink: /officers/
---

{% assign position_list = "Chair|Past-Chair|Chair-Elect|Secretary|Treasurer|Program Chair|Program Chair-Elect|Publications Officer|Statistics in Imaging Section Representative|Council of Sections Governing Board Vice Chair|Staff Liaison" | split: "|" %}

## Current Section Officers

{% assign requested_year = 2023 %}
{% assign yearly_officer_list = site.data.officers | where_exp:"item", "item.Years contains requested_year" %}
<table>
{% for position in position_list %}
  {% for officer in yearly_officer_list %}
    {% for service_year in officer.Years %}
      {% if service_year == requested_year %}
        {% assign index = forloop.index0 %}
        {% assign position_title = officer.Positions[index] %}
        {% if position_title == position %}
            <tr>
            <th>
            <b>{{position}}</b>
            </th>
            <th>
            {{ officer.Firstname }} {{ officer.Lastname }}
            </th>
            </tr>
        {% endif %}
      {% endif %}
    {% endfor %}
  {% endfor %}
{% endfor %}
</table>











