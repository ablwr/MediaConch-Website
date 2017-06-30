---
layout: downloads
permalink: download.html
title: "Download MediaConch"
---

# Downloads

## 17.06 Release Notes

### GUI/CLI/Server/Online

Ubuntu 17.04 packages  
More Matroska checks  
More detailed FFV1 errors  
See [the list of tests](https://github.com/MediaArea/groundtruth/blob/master/matroska/README.md) for more information  

### GUI

"Full parsing" option  
Internal database viewer  
Policy column in checker was sometimes displaying "fail" even if test was passing  

### Historical Release Notes

{% for post in site.releasenotes reversed %}
  [{{ post.date }}]({{ post.url | remove_first:'/'}})
{% endfor %}

### Snapshots

You can test ongoing developments for MediaConch by downloading our [daily builds](/MediaConch/downloads/snapshots.html).
