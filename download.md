---
layout: downloads
permalink: download.html
title: "Download MediaConch"
---

# Downloads

## 17.11 Release Notes

### GUI
Formatted MediaInfo display  
Text and EBUCore 1.8 (XML and JSON) reports available for download in MediaInfo display  

### GUI/CLI/Server/Online

Improved Matroska video frame rate detection  
Support of BWF (bext) loudness info  
Support of MOV HDR metadata  
Support of PCM endianess in Matroska files  
Several minor fixes  

### CLI

Text and EBUCore 1.8 (XML and JSON) reports available directly from MediaConch command line  

### Historical Release Notes

{% for post in site.releasenotes reversed %}
  [{{ post.date }}]({{ post.url | remove_first:'/'}})
{% endfor %}

### Snapshots

You can test ongoing developments for MediaConch by downloading our [daily builds](/MediaConch/downloads/snapshots.html).
