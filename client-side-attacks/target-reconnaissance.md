---
title: Target reconnaissance
description: Inspect client foothold in order to perform Client side attacks
tags:
  - Client Side Attacks
  - Enumeration
  - Exiftool
---

## Metadata

``` We can use google dorks to find public pdf file.
site:google.com filetype:pdf 
``` 

Once we got some file to inspect, we can use exiftool to display metadata of any files.

```powershell
# -u : Display unknow tag.
# -a : Display duplicated tag.
exiftool -u -a $file

ExifTool Version Number         : 12.41
File Name                       : brochure.pdf
...
XMP Toolkit                     : Image::ExifTool 12.41
Creator                         : Stanley Yelnats
Title                           : Mountain Vegetables
Author                          : Stanley Yelnats
Producer                        : Microsoft PowerPoint 
Create Date                     : 2022:04:27 07:34:01+02:00
...
```

## Client fingerprinting

http://canarytokens.com to confirm that victim use specific OS to perform our attack.