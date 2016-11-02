---
layout: default
permalink: /fixity.html
title:  "Fixity Feature for MediaConch"
---

# Fixity feature for MediaConch

In the October release of MediaConch, [available here](https://mediaarea.net/MediaConch/download.html), we have introduced some new features for checking and implementing fixity within video files, including some methods to correct small fixity errors.

## Segment sizes in Matroska

Some files have a wrong Matroska Segment element size (it is set to 0 instead of the actual size). As a result, a file with this problem is playable on some players that support corrections of this bug but not on some other players (e.g. VLC can play the file but Windows 10 Media Player cannot play the file). This is an example of interoperability issue.
The new fixer feature in MediaConch is able to resolve this issue.

Try this new feature out for yourself with the below demo:

Download [this file on archive.org](http://www.archive.org/download/vip.videobaran1.com/The.Simpsons/06/The.Simpsons.S06.E05.www.VideoBaran.net.mkv). This file is not playable using Windows 10 Media Player.

1. Click on "Enable fixer" in the MediaConch GUI checker page
1. Select the file
1. Click on “Check files"

Alternatively, if using the command line, add the option "--TryToFix --Force".

A file with the same name + ".fixed" is created with the correct Segment size and is now playable by Windows 10 Media Player.

## FFV1 "bit flip" correction

MediaConch can now check for "bit flipping" and correct these if found, saving the file from damage caused by an unintentional state switch between 0 and 1 which can occur to bits stored for a long time, in the case FFV1 slice are “protected” with a CRC checksum. This is the default in FFmpeg for streams in 720x480 definition or higher.

Demo below:

Download [this file](https://mediaarea.net/MediaConch/files/FFV1+PCM_WithChecksum_VideoBitFlip.mkv). This is a file created by FFmpeg with handmade flipped bit.

The 9th bit (most significant bit of 2nd byte) of the FFV1 1st slice of the 1st video frame is flipped. Also, the 17th bit (less significant bit of 3rd byte) of the FFV1 4th slice of the 1st video frame is flipped. Why these bits? Because it creates nice display of bugs during decoding. Touching some other bits just make FFmpeg decoder create a black image and displaying a black image is not interesting!

The resulting decoded frame (e.g. with FFmpeg "ffmpeg -i FFV1+PCM_WithChecksum_VideoBitFlip.mkv Decoded_Error.png") is:

<img src="/MediaConch/images/video_bitflip_detected.png" alt="video_bitflip_detected">

Obviously the first (top left) and fourth (bottom right) slices are scrambled.

1. Click on "Enable fixer" in the GUI's checker page
1. Select the file
1. Click on "Check files"

Or, if using the command line, add the option "--TryToFix --Force"

The resulting decoded frame (e.g. with FFmpeg "ffmpeg -i FFV1+PCM_WithChecksum_VideoBitFlip.mkv.fixed Decoded_Fixed.png") is:

<img src="/MediaConch/images/video_bitflip_corrected.png" alt="video_bitflip_corrected">

...and it's a miracle! The image is the expected one.

There is currently one limitation: if the bit in error is in the slice footer (7 bytes at the end of a slice), CRC values are not found and the correction cannot be done (all slices may be lost in this case). Detecting "bit flipping" in the footer is possible with a different algorithm and is planned in a later release of MediaConch. Performance may also be improved if there is a request for it.

## Matroska "bit flip" correction

Matroska can also support CRC protection per Cluster (often a block containing a video GOP and the corresponding audio, which can be a single video frame if the GOP is 1 as expected in archives). The next version of FFmpeg will create Matroska files with CRC by default (yeah!). This permits to protect stream formats not having their own CRC protection like PCM, as well as the container itself.


Demo below:

Download [this file](https://mediaarea.net/MediaConch/files/FFV1+PCM_WithChecksum_AudioBitFlip.mkv). This is a file created by FFmpeg with hand made flipped bit. The1st bit (most significant bit of 1st byte) of the PCM packet is flipped. The resulting decoded packet (e.g. file opened in open source audio editor [Audacity](http://www.audacityteam.org/)) starts with:

<img src="/MediaConch/images/audio_bitflip_detected.png" alt="audio_bitflip_detected">

Obviously the 1st audio sample is completely wrong!

1. Click on "Enable fixer" in the GUI checker page
1. Select the file
1. Click on "Check files"

If using the CLI, add the option "--TryToFix"

The resulting decoded frame starts with:

<img src="/MediaConch/images/audio_bitflip_corrected.png" alt="audio_bitflip_corrected">

Another miracle! The audio waveform is as expected.

There is currently one limitation: if the bit in error is in the CRC element header of the Matroska cluster), CRC values are not found and the correction can not be done. Detecting “bit flipping” in the CRC element header is possible with a different algorithm and is planned in a later release of MediaConch.
Performance may also be improved if there is a request for it.

## What's next for us?

We still need to create a better messaging system during the fixing process within the UI. Currently, the fixing takes a long time and there is no notification to the user for when the file has been fixed. We also need to improve performance!

## What's next for you?

What can we fix next? It's up to you! [Let us know](mailto:info@mediaarea.net) what are the most important issues you have with your video files.