---
layout: downloads
permalink: download.html
title: "Download MediaConch"
---

# Downloads

## 17.05 Release Notes

### GUI

Add MediaConch to Mac App Store  
Use OS native dialogs instead of those from Qt  
Display login status in settings page and allow to logout  
Fixed broken XML output display  

### CLI

Add a --list command to the CLI for listing files in the database  

### GUI/CLI/Server/Online

add FFV1-VALID-VERSION, EBML-ELEMENT-VALID-RANGE, NO-JUNK-IN-FIXEDSIZE-MATROSKA, EBML-ELEM-UNKNOWN-SIZE tests  
deprecate MKV-VALID-BOOLEANS test  
fixes to MKV-NUMERICAL-TAG test  

### Historical Release Notes

{% for post in site.releasenotes reversed %}
  [{{ post.date }}]({{ post.url | remove_first:'/'}})
{% endfor %}

### Snapshots

You can test ongoing developments for MediaConch by downloading our [daily builds](/MediaConch/downloads/snapshots.html).
