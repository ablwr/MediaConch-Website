---
layout: downloads
permalink: download.html
title: "Download MediaConch"
---

# Downloads

## 17.08 Release Notes

### GUI/CLI/Server/Online

FFV1: fix false positive about FFV1 slice_x error when slice_w>slice_h  
Clarifcation about license of some third party library

### Historical Release Notes

{% for post in site.releasenotes reversed %}
  [{{ post.date }}]({{ post.url | remove_first:'/'}})
{% endfor %}

### Snapshots

You can test ongoing developments for MediaConch by downloading our [daily builds](/MediaConch/downloads/snapshots.html).
