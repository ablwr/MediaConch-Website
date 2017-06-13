---
layout: default
title:  "Interview with Eddy Colloton"
date:   2017-06-13
categories: mediaconch, interview
---

# Interview with Eddy Colloton

*Editor's note: This is the first in a series of interviews with people using MediaConch within their institutions. Enjoy!*


**Hey Eddy! Introduce yourself please.**

Hey Ashley! I’ve recently become a “Denverite” and have started a new job as an [Assistant Conservator specializing in electronic media](http://www.kunc.org/post/built-past-floppy-disk-and-vhs-art-need-creative-conservation&sa=D&ust=1497302411695000&usg=AFQjCNEd4gxsXMGMqdLlhnkyQ3U_cuCpug) at the Denver Art Museum (DAM). Before that, I was down in Baton Rouge, Louisiana working as a [National Digital Stewardship Resident](https://ndsr.americanarchive.org/&sa=D&ust=1497302411696000&usg=AFQjCNFAxhriwjXWqTbSm04mdYPhmQx3aA) with Louisiana Public Broadcasting (LPB). When I’m not working, I like to listen to podcasts, read comics, play bass, and stare into the endless void that is “twitter” ([@EddyColloton](https://twitter.com/EddyColloton)). I’m on a big H. P. Lovecraft kick right now so let me know if you have any recommendations (Dunwich Horror is my current fav, but At the Mountains of Madness is a close second).


**What does your media ingest process look like? Does your media ingest process include any tests (manual or automated) on the incoming content? If so , what are the goals of those tests?**

The ingest procedures I’m using for the Denver Art Museum are pretty different from the ones we worked out at Louisiana Public Broadcasting, for all kinds of reasons. The two institutions have very different types of collections, and they use their repositories very differently, too.

At the Denver Art Museum, ideally, material will enter the digital repository upon acquisition. Ingest procedures need to be able to be tailored to the eccentricities of a particular media artwork, and flexible enough to cover the wide array of media works that we acquire (websites, multi-channel video installations, software-based artworks, or just a collection of tiff files). With this in mind, we’re using [Archivematica](https://www.archivematica.org/en/&sa=D&ust=1497302411701000&usg=AFQjCNGiYD7IxXFq_vJwvx1v9OhMyEjDsQ) for ingest of media into our digital repository. It allows us to automate the creation of METS wrapped PREMIS XML documentation, while manually customizing which microservices we choose to use (or not use) as we ingest new works. Some of the microservices I use on a regular basis are file format identification through [Siegfried](http://www.itforarchivists.com/siegfried&sa=D&ust=1497302411703000&usg=AFQjCNFls8VIadFVVfzr7aMZO4wnAxp8KQ), metadata extraction with [MediaInfo](https://mediaarea.net/ru/mediainfo&sa=D&ust=1497302411704000&usg=AFQjCNE2WXrMudOm6zPEugJ8iAiqmrqCtQ), [ExifTool](http://www.sno.phy.queensu.ca/~phil/exiftool/&sa=D&ust=1497302411705000&usg=AFQjCNGQvM_KgEjvGZxJSdFCmY6FQEWBFA), and [Droid](http://www.dcc.ac.uk/resources/external/droid&sa=D&ust=1497302411706000&usg=AFQjCNGX3FGken7O5d-JRMZ9EnANE6DGCw), and normalization using tools like [FFmpeg](https://ffmpeg.org/&sa=D&ust=1497302411707000&usg=AFQjCNEb6U7fL221fOQdmYIQ7KkZAROX3Q).

Things couldn’t be more different at LPB. All completed locally produced programming automatically becomes part of the LPB archive. The LPB Archive is then responsible for preserving, describing and making that content accessible through the Louisiana Digital Media Archive (LDMA), located at [http://www.ladigitalmedia.org/](http://www.ladigitalmedia.org/&sa=D&ust=1497302411709000&usg=AFQjCNHbwgFXa_vEoYBlwssXCi1WyF-m9A). LPB’s ingest procedures need to allow for a lot more throughput, but there’s much less variability in the type of files they collect compared to the DAM. With less of a need for manual assessment, LPB uses an automated process to create MediaInfo XML files, an MD5 checksum sidecar, and a MediaConch report through a custom watchfolder application that our IT engineer, Adam Richard, developed. That code isn’t publically available unfortunately, but you can see the scripts that went into it on [my GitHub](https://github.com/eddycolloton/LPB_ArchiveProcesses&sa=D&ust=1497302411710000&usg=AFQjCNFHpD6_n8dWf5Gicn-w0iqKZEwWFQ).


**Where do you use MediaConch? Do you use MediaConch primarily for file validation, for local policy checking, for in-house quality control, for quality testing for vendor files?**

Primarily policy checking, as a form of quality assurance. At LPB, most of our files were being created through automated processes. Our legacy material was digitized using production workflows, to take advantage of existing institutional knowledge. This was very helpful, because we could then repurpose equipment, signal paths, and software. But, using these well worn workflows also meant that occasionally files would be encoded incorrectly, aspect ratio being one of the most common errors. We would check files against a MediaConch policy as a way of quickly flagging such errors, without having to invest time watching and reviewing the file ourselves.

At the Denver Art Museum, we plan to use MediaConch in a similar way. The videotapes in the museum’s collection will be digitized by a vendor. Pre-ingest, I plan to do tests on the files for quality assurance. After fixity checks, I will check to make sure our target encoding and file format was met by the vendor using MediaConch. I intend to use the [Carnegie Archive’s python script from their GitHub](https://github.com/CarnegieHall/quality-control/blob/master/mediaconch/mediaconch-xmlreport-summary.py&sa=D&ust=1497302411714000&usg=AFQjCNGNBDXo2efUjLy6ztfFzk-hz3bIgQ) to automate this process. Once I know that the files are encoded to spec, I will be creating QCTools reports and playing back the files for visual QC. I’ve been following the [American Archive of Public Broadcasting’s QC procedures](https://americanarchivepb.wordpress.com/2017/04/12/pbs-newshour-digitization-project-update-ingest-and-digital-preservation-workflows/&sa=D&ust=1497302411715000&usg=AFQjCNEbvjjJMWxL0v4GLuwhRRx9l5EsKw) with interest to see if there’s any tricks I can cop from their workflow.


**At what point in the archival process do you use MediaConch?**


Basically pre-ingest for both LPB and the DAM. When using MediaConch as a policy checker, my goal is to make sure we’re not bothering to ingest a file that is not encoded to spec.

**Do you use MediaConch for MKV/FFV1/LPCM video files, for other video files, for non-video files, or something else?**


I use MediaConch for MKV/FFV1/LPCM video files and for other types of video files as well. At LPB we were using MediaConch as a policy checker with IMX50 encoded files in a Quicktime wrapper and H.264 encoded files in a .mp4 wrapper. You can find the policies I created for LPB [here](https://github.com/eddycolloton/MediaConch&sa=D&ust=1497302411720000&usg=AFQjCNGAbyEM1vzB7hJkVhtTkYVLDqvNEA), and I talk through the rationale of creating those policies in the digital preservation plan that I created for LPB, [available here](https://aapbndsr.files.wordpress.com/2017/03/lpb_digital_preservation_plan_aapb_ndsr.pdf&sa=D&ust=1497302411721000&usg=AFQjCNElVoA6Px0syynhoms4_AdmpOvB1w) (MediaConch stuff on page 24, and page 45). I’m happy to report that LPB is currently testing a new workflow that will transcode uncompressed .mov files into lossless MKV/FFV1/LPCM files (borrowing heavily from the Irish Film Archive’s [lossless transcoding procedures](https://github.com/kieranjol/IFIscripts/blob/master/makeffv1.py&sa=D&ust=1497302411722000&usg=AFQjCNHbDuGNzix5cDWsLOm6m9ccLT1YIA), as well as the CUNY TV team’s [“make lossless” microservice](https://github.com/mediamicroservices/mm/blob/master/makelossless&sa=D&ust=1497302411724000&usg=AFQjCNGC5RRaNQ_h1pnbNukiiKlcY1wDNA)).

At the DAM, we’ll be using MediaConch as a policy checker with Quicktime/Uncompressed/LPCM files, and for validation of our MKV/FFV1/LPCM normalized preservation masters.

My understanding is that MediaConch is going to be integrated into [Archivematica’s next release](https://wiki.archivematica.org/MediaConch_workflow&sa=D&ust=1497302411728000&usg=AFQjCNFRIcrfLP_yKT6oNtDbVgaWflqz7A). I’m really looking forward to that update, since at the DAM we have decided to create MKV/FFV1/LPCM files for any digital video in the collection that uses a proprietary codec, or an obsolete format. A lot of the electronic media in the museum’s [design collection](http://denverartmuseum.org/collections/architecture-design-graphics&sa=D&ust=1497302411729000&usg=AFQjCNHi1BIRCa2vf08SKkJmoxmCX32ARg) comes from [the AIGA Archives](http://designarchives.aiga.org/%23/home&sa=D&ust=1497302411731000&usg=AFQjCNHc2eqfNGphFONluVYYj8ivFAwMPA), which the DAM collects and preserves. A ton of the video files from the AIGA Archives were created in the aughts, and they use all kinds of whacky codecs - my favorite so far is one that MediaInfo identifies as “RoadPizza” (apparently a QuickTime codec). Given that I don’t want to rely on the long-term support of the RoadPizza codec, we’re normalizing files like that to MKV/FFV1/LPCM through an automated Archivematica micro-service that uses the following FFmpeg script (which I cobbled together using [ffmprovisr](https://amiaopensource.github.io/ffmprovisr/&sa=D&ust=1497302411732000&usg=AFQjCNHx6UqnvVMH3B319D-dCYkd6EEYYg)):


`ffmpeg -i input_file -c:v ffv1 -level 3 -g 1 -slicecrc 1 -slices 16 -c:a pcm_s16le output_file.mkv`


To be clear we are also keeping the original file, but just transcoding a second version of the file to be cautious.

Through that implementation we intend to use the Archivematica MediaConch microservice to [validate the encoding of the video files that we have normalized for preservation](https://wiki.archivematica.org/Requirements/MediaConch_integration%23Post-normalization&sa=D&ust=1497302411737000&usg=AFQjCNE6BYrfOcDR5b1z1TItdfwNpShYnQ).


**Why do you think file validation is important the field?**


I wish this was a joke but it honestly helps me sleep better at night. MediaConch and melatonin make for a well rested AV archivist/conservator, hah. I like knowing that the video files that we are creating through automated transcoding processes are up to spec, and comply with the standards being adopted by the IETF.


Also, using MediaConch as a policy checker saves me time, and prevents me from missing bonehead mistakes, of which their are loads, because I work with human beings (and possibly some aliens, you never know).


**Anything else you'd like to add?**


Just want to offer a big thanks to the MediaConch team for everything that they do! I know there’s a pretty big overlap betwixt [team Conch](https://mediaarea.net/MediaConch/team.html&sa=D&ust=1497302411743000&usg=AFQjCNGc9v_uSSu6xXg7-nRvy7idDGMmoA), [CELLAR](https://datatracker.ietf.org/wg/cellar/charter/&sa=D&ust=1497302411744000&usg=AFQjCNFHpwMhQl4Cky0kBwOFNZzsVi8nfQ), and the [QCTools](https://www.bavc.org/preserve-media/preservation-tools/qctools&sa=D&ust=1497302411745000&usg=AFQjCNF063AK_HNeUl-RJh6oqizFIkNapA) peeps - you’re all doing great work, and regularly making my job easier. So thanks for that.

*To read more from Eddy, check out his [Louisiana Public Broadcasting Digital Preservation Plan](https://aapbndsr.files.wordpress.com/2017/03/lpb_digital_preservation_plan_aapb_ndsr.pdf)*
