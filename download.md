---
layout: downloads
permalink: download.html
title: "Download MediaConch"
---

# Downloads

## 17.12 Release Notes

### GUI/CLI/Server/Online

Endianness and Sign report for PCM Matroska tracks  
Support of external time code tracks (.qtc) in MOV  
Support of file names >64 chars long or non ASCII for referenced files in MOV  
JPEG 2000: Support of IMF profiles  
Fixed wrong color range info Matroska  
I630, "Input is not proper UTF-8" message with some MOV files  

### Historical Release Notes

{% for post in site.releasenotes reversed %}
  [{{ post.date }}]({{ post.url | remove_first:'/'}})
{% endfor %}

### Snapshots

You can test ongoing developments for MediaConch by downloading our [daily builds](/MediaConch/downloads/snapshots.html).
