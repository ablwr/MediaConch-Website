---
layout: downloads
permalink: download.html
title: "Download MediaConch"
---

# Downloads

## 16.08 Release Notes

### GUI

Policy Editor : close message when user change of policy/rule  
Checker : remove a node is not saved  
Checker : fix handling of files with special chars  
Add ctrl-q shortcut to quit  
Better handling of user path  

### CLI

Checker : fix handling of files with special chars  
Better handling of user path  

### Online

Policy Editor : close message when user change of policy/rule  

### Historical Release Notes

{% for post in site.releasenotes reversed %}
  [{{ post.date }}]({{ post.url | remove_first:'/'}})
{% endfor %}

### Snapshots

You can test ongoing developments for MediaConch by downloading our [daily builds](/MediaConch/downloads/snapshots.html).
