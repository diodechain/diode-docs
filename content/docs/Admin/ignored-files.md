---
_schema: default
title: Ignored Files
nav_title: Ignored Files
nav_section: For Your IT Admin
weight: 306
draft: false
---
The Diode app will ignore, and will not sync, certain types of files and folders:

* Any file that:
  * is 8 characters long ending in a tilde and a number. e.g. `MYFILE~1`
    * These are FAT file system secondary names
  * starts with `._` or `.~`
    * These are Mac index files
* Any folder (and its contents) that:
  * is named `.ddrive`
    * This is a reserved folder for local settings