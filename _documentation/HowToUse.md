---
layout: default
permalink: documentation/HowToUse.html
title: "Documentation: How To Use"
---

# Table of Contents

* [Overview](#overview)
* [Using MediaConchOnline and MediaConch GUI](#using-mediaconchonline-and-mediaconch-gui)
* [Using MediaConch CLI](#using-mediaconch-cli)

# Overview

## Installation Guide

MediaConch is available for use as a command line interface (CLI), a graphical user interface (GUI), a web user interface (WebUI) and server. See [our installation guide](https://mediaarea.net/MediaConch/installation.html) on how to install with the interface of your choosing.

## How to use MediaConch

MediaConch works with virtually any audiovisual file format, but is created to work specifically with Matroska-wrapped FFV1 and LPCM encoded video files. For these files, validation is performed according to the specifications of each of these formats. If, for example, an AVI-wrapped FFV1 and LPCM encoded video file is used, thorough file validation will be performed on the FFV1 and LPCM portions and the AVI file will be minimally checked for validation and approved if these validations pass. MediaConch works with sister projects [veraPDF](http://verapdf.org/) and [DPF Manager](http://dpfmanager.org/) to perform thorough validation on PDF and TIFF file formats.

\*Sponsorship is available for validation-checking for other file formats, when applicable.

## Checking files

Files from various sources can be checked with MediaConch, regardless of the chosen interface. A preservationist may check local files, online files, or local folders. "Check local file" allows you to select a file or files from a local computer. "Check online file" allows you to select a file using a URL path. Please note that this feature supports the following application protocols: HTTP/HTTPS/FTP/FTPS. "Check local folder" allows you to select a folder of files from a local computer or volume. For any of these selections, a preservationist may choose from either an existing policy and display in MediaConch or from an imported XSL policy file.

In addition to checking files for complex or simple validation, MediaConch also can check files against policies created by memory institutions identifying exactly what specifications a file should require (for example, does this file conform to NTSC or PAL standards?). Please see the next section on policies to learn more.

## MediaConch Policies

In MediaConch, users can develop their own policies specific to the needs of their memory institutions. Policies can also be shared between memory institutions, as they can be easily exported and imported between instances or frameworks. CLI, GUI, or WebUI all support the same policy structure.

In the "Policies" section of the GUI or WebUI software, a preservationist can create customized policy tests to check for conformance to a specific set of standards that your collection must adhere to. You can also import previously generated policy sets in XSL format.

Video files are broken down into different "streams", which a preservationist can select depending on the section of the video they are looking to create a policy for. These streams include General, Video, Audio, Image, Text, Menu, or Other. For example: if you are testing the dimensions in pixels, you’d want to choose "Video" because the Video stream represents all visual components of the overall video structure, including amount or size of pixels. since Video/Audio/General is the most common. It may seem that the Image stream is an appropriate place to analyze the visual aspects of a video stream, but Image refers to still images attached to the video file only, such as an appended thumbnail. Image/Text/Menu/Other are most likely going to be used in edge cases only.

Policy sets consist of individual rules and assertions. A policy may contain one or more rules, and rules may consist of one or more asserts. Rules and assertions typically contain a metadata field (e.g., "Format"), that field’s associated metadata stream type (e.g., "General), a validator (e.g., "is_equal), and a desired value (e.g., "Matroska"). In brief, a preservationist would select a type, a field, a validator, and a value. Rules and assertions are automatically saved during creation, but you may duplicate or delete it using the associated buttons on each rule/assertion window.

For example, the following rule/assertion would ensure that all reported files must contain a frame rate associated with the NTSC broadcast standard:
Type: General
Field: FrameRate
Validator: Equal
Value: 29.970

## Reading the reports

MediaConch can produce four reports: Implementation, Policy, MediaInfo, and MediaTrace.

In addition to level of reports, reports can also be displayed or downloaded in the following formats: HTML, Text, Text with Unicode support, and XML. In the command line interface, reports can also be viewed using the "Simple" or "CSV" flags. The simple flag will create 	a display with "pass" or "fail" for each report segment. The CSV flag, intended specifically for use with policies, will generate a table of results in CSV format.

In the GUI and WebUI, reports can be downloaded by either clicking on the down arrow (↓) found directly to the right of each report, or by clicking on the "Download" button located at the bottom right of each report in View Mode. All formats can be exported and stored as sidecar metadata, PREMIS object, or however a preservationist may choose to store their preservation materials.

For more information on the XML formats used in reporting, please see the [Data Format page](https://mediaarea.net/MediaConch/documentation/DataFormat.html).  

#### Implementation

An implementation report will, if possible, validate the file against its specification (currently available for Matroska, FFV1, LPCM, PDF, and TIF). An implementation report will declare whether a particular file is either VALID or NOT VALID. If a file corresponds to one of the standards and is not valid, reason for failure is provided.

#### Policy

A policy report will compare the file against the assigned policy. Additionally, Mediainfo (high-level overview of the contents of the file) and MediaTrace (binary analysis of the file) will be produced. A policy report will declare whether a particular file is either wholly VALID or NOT VALID according to the prescribed policy tests. This policy test can either incorporate one of the pre-packaged templates available within MediaConch, or it can be tailored to fit the desired standards of the respective institution. One such alternative policy test would be to check that all video files conform to the same dimensions (1080p HD, 480p SD, etc.) as opposed to merely checking if the video file is free of digital decay. Ultimately, these reports can be as simplistic or elaborate as the needs of the institution in question.

#### MediaInfo

[MediaInfo](https://mediaarea.net/en/MediaInfo) displays technical information about media files, as well as tag information for many audio and video files. The MediaInfo data display includes the container, video, audio, text, and chapters streams. The container contains format, profile, commercial name of the format, duration, overall bit rate, writing application and library, title, author, director, album, track number, date, duration information. The video stream contains format, codec id, aspect, frame rate, bit rate, color space, chroma subsampling, bit depth, scan type, and scan order information. The audio stream contains format, codec id, sample rate, channels, bit depth, language, and bit rate information. The text stream contains format, codec id, language of subtitle information. The chapter stream contains count and lists of chapters. Files can have multiple streams.

#### MediaTrace

[MediaTrace](https://mediaarea.net/MediaTrace/) is a technical report that expresses the binary architecture of a file, reporting primarily on audiovisual formats. Many audiovisual formats are based on chunk-based storage where a block of data will either contain a data payload or other blocks. Each chunk, or segment, of data is defined as a <block>, and contents of blocks are called <data>. MediaTrace is helpful when a preservationist requires an in-depth analysis of a file to diagnose the problem. MediaTrace was developed by MediaArea in collaboration with the Museum of Modern Art (New York, USA).

## Fixing Files

MediaConch includes features for checking and implementing fixity within video files, including some methods to correct small fixity errors, with a focus on Matroska files. Matroska can also support CRC protection per Cluster (often a block containing a video GOP and the corresponding audio, which can be a single video frame if the GOP is 1, as expected in memory institutions).

For example, some files have an incorrect Matroska Segment element size (e.g. set to 0 instead of the actual size). As a result, a file with this problem is playable on some video player software that support corrections of this bug, but not on some other players (e.g. VLC can play the file but Windows 10 Media Player cannot play the file). This is an example of an interoperability issue resulting in inconsistent playback of a file. The fixer feature in MediaConch is able to resolve this issue.

MediaConch can also check for "bit flipping" and correct these if found, saving the file from damage caused by an unintentional state switch between 0 and 1, a problem which can occur to bits stored for a long period of time. This can be especially helpful and time-saving when video streams are encoded with FFV1 and each FFV1 frame/slice is "protected" with a CRC checksum. For more information, see our [Fixity feature announcement](https://mediaarea.net/MediaConch/fixity.html).

## Using MediaConchOnline and MediaConch GUI

MediaConch GUI and MediaConchOnline are built with the same interface. Here are instructions for using either. If using MediaConchOnline, you will first need to register an account by creating a username/password, which will be emailed to you with instructions. Then log in.

**MediaConch consists of three main sections: "Checker," "Policies," and "Display."**

### Checker

![MediaConch Checker](../images/HowTo_Checker.png)

By default, MediaConch opens in in the Checker section. In this, files are checked for specification validation and for conformance using policies defined by you. You may choose from either an existing policy in MediaConch, from an imported XSL policy file, or you can create your own within the application. MediaConch comes preloaded with several policies.

After selecting file, policy, display, and verbosity and clicking "Check files", reports are generated below, in the Results section. MediaConch will then produce four reports: Implementation, Policy, MediaInfo, and MediaTrace.

Please see the Reading the Results section above for more information on understanding the reports.

Implementation and Policy will give a high-level pass/fail view. If you hover over these results, a "see more" and "download" buttons will appear, just like the MediaInfo/MediaTrace reports.

![MediaConch Checker Results](../images/HowTo_Results.png)

![MediaConch Checker Results](../images/HowTo_ResultsHover.png)


Implementation and Policy reports will be displayed in the method selected in the above drop-down menu. This can be changed at any time to see the reports in a different view. For MediaInfo and MediaTrace reports, you may navigate through an interactive directory tree structure representing the file created from the reports. Scroll to the bottom of the page to export any of these reports.

For MediaInfo reports, there is an additional button: "Create policy from MediaInfo report". This can be used to create a policy based on an existing file and will be added to your policies.

\* Note: When opening MediaTrace in View Mode, offsets will be addressed in hexadecimal, or "hex" notation. This differs from the MediaTrace XML output, which addresses offset in decimal notation.

### Exporting Reports

Reports can be downloaded by either clicking on the down arrow (↓) found directly to the right of each report, or by clicking on the "Download" button located at the bottom right of each report in View Mode.

## Policies

![MediaConch Policies](../images/HowTo_Policy.png)


In the Policies section, you can create customized policy tests to check for conformance to a specific set of standards that your collection must adhere to. You can also import previously generated policy sets in XSL format.

Policy sets consist of individual rules and assertions. A policy may contain one or more rules, and rules may consist of one or more asserts. Rules and asserts typically contain a metadata field (e.g., "Format"), that field’s associated metadata stream type (e.g., "General), a validator (e.g., "is_equal), and a desired value (e.g., "Matroska"). Rules and asserts are automatically saved during creation, but you may duplicate or delete it using the associated buttons on each rule/assertion window.

For example, the following rule/assertion would ensure that all reported files must contain a frame rate associated with the NTSC broadcast standard:

- Type: General
- Field: FrameRate
- Validator: Equal
- Value: 29.970

### Create a Policy

#### 1. Choose Type

Allows you to select from a list of available metadata stream types. Video files are broken down into different "streams", which you will select depending on the section of the video you are looking to create a policy for. These streams include General, Video, Audio, Image, Text, Menu, or Other. For example: if you are testing the dimensions in pixels, you’d want to choose "Video" because the Video stream represents all visual components of the overall video structure, including amount or size of pixels. since Video/Audio/General is the  most common. It may seem that the Image stream is an appropriate place to analyze the visual aspects of a video stream, but Image refers to still images attached to the video file only, such as an appended thumbnail.Image/text/menu/other are most likely going to be used in  edge cases only.

Example: *General*

#### 2. Choose Field

Allows you to select from a list of associated fields. Fields vary according to what type of metadata stream is selected.

Example: *General/UniqueID*

#### 3. Select Occurence

Allows you to select whether a rule occurs more than once in reportage.  

Example: *Occurrence: 1*

#### 4. Choose Validator

Validators for MediaConch include **is_equal**, **is_not_equal**, **is_greater than**, **is_less_than**, **is_greater_or_equal_than**, **is_less_or_equal_than**, **exists**, **does_not_exist**, and **contains_string**.

| Validator | Definition | Example |
|-----------|------------|---------|
| is_equal                 | Requires the reported field value to be the same as the associated policy value. |  General/Format is_equal to Matroska |
| is_not_equal             | Requires the reported field value to be different as the associated policy value. |  General/Format is_not_equal to MPEG-4 |
| is_greater than          | Requires the reported field value to be greater than the associated policy value. |  General/Duration is_greater_than 1 mn |
| is_less_than             | Requires the reported field value to be less than the associated policy value. | Audio/Channels is_less_than 2 Channels |
| is_greater_or_equal_than | Requires the reported field value to be greater or equal than the associated policy value. | Video/FrameCount is_greater_or_equal_than 1 |
| is_less_or_equal_than    | Requires the reported field value to be less or equal than the associated policy value. | Video/FrameRate is_less_or_equal_than 29.970 |
| exists                   | Requires the reported field value to exist. | Video/Width_Original exists |
| does_not_exist           | Requires the reported field value to not exist. | Video/Width_CleanAperture does_not_exist |
| contains_string          | Requires the reported field value to contain an associated string. | General/CompleteName contains_string ffv1 |

#### 5.Value

This function allows you to select a desired value. When creating a value, do not include any associated strings (e.g., "pixels").

#### 6. Advanced: Free Text mode

In addition to the Editor, policies may also be edited in Free Text mode. Free Text uses the XML Path Language (XPath). The following is an example of a MediaConch XPath expression in Free Text mode:
*track[@type='General']/FileExtension = 'mkv'*

Working within Free Text mode necessitates a high degree of skill within XPath and is only recommended for use by advanced users.

### Display

The Display section will allow you to apply various display XSLs for use with policy and implementation check reports in the checker section. MediaConch has provided example HTML, XML and Text displays. Once a display XSL is imported, it can be instantly used by selecting the display in the "Choose a Display" dropdown menu when checking your files in the Checker section.

**Import display set**: Allows you to import a display XSL file to the display set.  
**Export display set**: Allows you to export a display XSL file to the display set.  
**Delete selected display file**: Allows you to delete a display XSL file from the display set.  

## Using MediaConch CLI

Running `mediaconch -h` in your terminal window will display the primary options available for the command line tool. `mediaconch -ah` will display only advanced options.

Simply, mediaconch can be run by following this pattern: `mediaconch [-Options...] FilePath1 [FilePath2...]`

Here are a few handy commands and an explanation of what they do:

`mediaconch [FilePath]`
- This is the most simple command, and it will test and return the validation results on screen.

`mediaconch [FilePath] > output.txt`
- The above output can be very verbose, possibly too verbose for your terminal window, so this command will send the output to a text file called output.txt.

`mediaconch -fs [FilePath]`
- This will export a simple pass/fail output for each test performed on the file.

`mediaconch -p my_policy.xml [FilePath]`
- This will test your file against your local policy. Policies must be created via MediaConchOnline or the MediaConch GUI and can be exported to use anywhere.


### Scaling MediaConch

With the command line tool, MediaConch can be used on thousands of files at once, alleviating the need for individual attention by the preservationist for healthy files.

For example, this simple bash script, `for file in *.mkv; do mediaconch "$file"; done`, loops through all Matroska files in a folder and checks them against the specification, printing results to the screen.
