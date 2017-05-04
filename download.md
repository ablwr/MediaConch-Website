---
layout: downloads
permalink: download.html
title: "Download MediaConch"
---

# Downloads

## 17.04 Release Notes

### GUI/CLI/Server/Online

Better support of some broken Matroska files (high EBMLMaxSizeLength, padding before start of EBML)  
Was sometimes displaying "Bit depth: Bit0" when bit depth is unknown in Matroska  
FFV1 PixelAspectRatio was an integer, switched to 3-digit rational  
Several small bug fixes and small performance optimizations  

### Historical Release Notes

{% for post in site.releasenotes reversed %}
  [{{ post.date }}]({{ post.url | remove_first:'/'}})
{% endfor %}

### Snapshots

You can test ongoing developments for MediaConch by downloading our [daily builds](/MediaConch/downloads/snapshots.html).
