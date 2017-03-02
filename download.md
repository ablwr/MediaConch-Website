---
layout: downloads
permalink: download.html
title: "Download MediaConch"
---

# Downloads

## 17.02 Release Notes

### GUI/CLI/Server/Online

New policy example (TN2162)  
Fix incorrect namespaces in schemaLocation (Thanks to kimec)  
Report refactoring  
Several minor FFV1 related bug fixed  
Support of V_FFV1 codec identifier in Matroska  

### GUI

Flipping between pages removed  
Fix Qt 5.7+ webengine support  

### Online

Checker: js refactoring, improve display of results, performance improvements  

### Historical Release Notes

{% for post in site.releasenotes reversed %}
  [{{ post.date }}]({{ post.url | remove_first:'/'}})
{% endfor %}

### Snapshots

You can test ongoing developments for MediaConch by downloading our [daily builds](/MediaConch/downloads/snapshots.html).
