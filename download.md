---
layout: downloads
permalink: download.html
title: "Download MediaConch"
---

# Downloads

## 16.09 Release Notes

### GUI/CLI/Server/Online

New policy format to allow complex policies  
Update example policies and displays  
New policy editor to build complex policies  
Policy rules can use MediaTrace  
Handling of FFV1 16-bit bitdepth (YUV and RGB)  
Support of Matroska FieldOrder, MatrixCoefficients, BitsPerChannel, Range, TransferCharacteristics, Primaries new elements  
Stream count policy test (in General section)  


### CLI

Compare files (technology preview)  


### Online

Guest mode, no need to register to use MediaConchOnline  

### Server

New API version to handle new policy format  


### Migrate old policies (GUI and Server)

If you already have policies created before MediaConch 16.09 release and want them back, follow this procedure.  
First, go to your local folder:  
  
On Windows: go to %APPDATA% (most of the time, it will be C:\Users\$USER\AppData\Roaming\).  
  
On Mac OS: go to your $HOME/Library/Application Support/ directory (most of the time, $HOME will be /Users/$USER).  
  
On Linux: go to your $HOME/.local/share/ directory (most of the time, $HOME will be /home/$USER).  
  
Then, go to MediaConch/policies (or MediaConch\policies on Windows) directory, create if not existing a directory named "-1" and move the XSL files to this directory.  
  
Launch the GUI or Server and policies will be loaded.  
  
Contact us if you created complex policies and would like us to move them to the new format  

### Historical Release Notes

{% for post in site.releasenotes reversed %}
  [{{ post.date }}]({{ post.url | remove_first:'/'}})
{% endfor %}

### Snapshots

You can test ongoing developments for MediaConch by downloading our [daily builds](/MediaConch/downloads/snapshots.html).
