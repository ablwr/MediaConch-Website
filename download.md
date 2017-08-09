---
layout: downloads
permalink: download.html
title: "Download MediaConch"
---

# Downloads

## 17.07 Release Notes

### GUI/CLI/Server/Online

Add EBML-MINVER-COHERANT and EBML-MAXVER-COHERANT tests  
MediaConch is now directly integrated in Fedora repository  

### CLI

CLI was sometimes not responding with -f option  

### Historical Release Notes

{% for post in site.releasenotes reversed %}
  [{{ post.date }}]({{ post.url | remove_first:'/'}})
{% endfor %}

### Snapshots

You can test ongoing developments for MediaConch by downloading our [daily builds](/MediaConch/downloads/snapshots.html).
