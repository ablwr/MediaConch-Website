---
layout: downloads
permalink: download.html
title: "Download MediaConch"
---

# Downloads

## 16.07 Release Notes

### GUI, Online

New policy editor  
Minor fixes  

### Historical Release Notes

{% for post in site.releasenotes reversed %}
  [{{ post.date }}]({{ post.url | remove_first:'/'}})
{% endfor %}

### Snapshots

You can test ongoing developments for MediaConch by downloading our [daily builds](/MediaConch/downloads/snapshots.html).
