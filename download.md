---
layout: downloads
permalink: download.html
title: "Download MediaConch"
---

# Downloads

## 17.01 Release Notes

### GUI/CLI/Server/Online

Support of newest version of DPFManager (TIFF plugin) and VeraPDF (PDF plugin)  
Store implementation report in database (no need to run it again at relaunch)  
Several small bug fixes  

### GUI

Less verbose output by default (use " -ft" for old behavior)  
New display templates "Simple" and "CSV"  
Policy editor: option for creating policy from a file  
Policy editor: split between Profile and Level  
Checker page: jump to the page containing the file to analyze  
Checker page: scroll to the top of the results when page is changed  
Checker page: add reload analyze button (force analyze)  
Checker page: reduce font size of jstree MediaInfo and MediaTrace  

### CLI

Less verbose output by default (use " -ft" for old behavior)  
New display templates "Simple" and "CSV"  

### Online

Checker page: jump to the page containing the file to analyze  
Checker page: scroll to the top of the results when page is changed  
Checker page: add reload analyze button (force analyze)  
Checker page: reduce font size of jstree MediaInfo and MediaTrace  

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
