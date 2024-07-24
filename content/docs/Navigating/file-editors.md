---
_schema: default
title: File Editors
nav_title: File Editors
nav_section: Navigating
weight: 214
draft: false
---
Certain files can be edited directly from within Diode Drive. This removes the need of opening the file in an external editor - which may be insecure. If an editor is available, a pencil icon ("edit") will be shown when previewing the file. You can edit the file by clicking the edit icon:

![](/uploads/image-96.png)

### **Markdown File Editor (.md, .txt files)**

As of version 1.5.2 (May 2022), Diode Drive has a Markdown file editor built into the user interface. This feature is in Beta - it is mostly functional, but has a few known issues you should understand.<br>1) There is no file locking - if two devices update a file, the most recently saved version will over-write the other version<br>2) There is no content merging - if a device edits the file when offline, and then comes back online, a more recent version will over-write the content<br>3) There is no concurrent/collaborative editing - file edits are done by one device at a time<br>4) Edit performance for large files (&gt;500 lines long) degrades with the size of the file - shorten or archive portions of long files to maintain snappy edits<br><br>As such, the best use case for this feature at current time is personal note taking. Team environments may experience the issues noted above. These items will be addressed in an upcoming release.

The markdown file editor is loaded when a markdown or text file (.md, .txt) are edited.

The editor has a formatting ribbon at the top. This ribbon can be used to add formatting (e.g. bold, italics, bullets, tables, images, etc...) to the text that you enter.

![](/uploads/image-97.png)

If the screen is narrow, the controls will be collapsed into an expanding control pane:

![](/uploads/image-98.png)

When edits are made to the file, "Save" will be highlighted, allowing you to save the edits - the Back button and cmd-s (ctrl-s) will also save the file.

![](/uploads/image-99.png)

---

&nbsp;