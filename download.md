---
layout: downloads
permalink: download.html
title: "Download MediaConch"
---

# Downloads

## 17.03 Release Notes

### GUI/CLI/Server/Online

Analyze attachments in Matroska files  
Reduce size of Matroska trace  
Few small FFV1 parsing improvements  
Several small bug fixes  

### GUI

Checker: js refactoring, improve display of results, performance improvements  

### Online

Checker: js refactoring, improve display of results, performance improvements  

### Historical Release Notes

{% for post in site.releasenotes reversed %}
  [{{ post.date }}]({{ post.url | remove_first:'/'}})
{% endfor %}

### Snapshots

You can test ongoing developments for MediaConch by downloading our [daily builds](/MediaConch/downloads/snapshots.html).
