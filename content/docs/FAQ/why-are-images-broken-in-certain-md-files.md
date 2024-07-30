---
_schema: default
title: Why Are Images Broken in Certain MD files?
nav_title: Why Are Images Broken in Certain MD files?
nav_section: FAQ
weight: 20024
draft: false
---
As of July 2023, there is a bug with the Diode App in which images cannot be added to markdown files if the file has a parentheses character, either `(` or `)` , in its file name or in its file path.

If the filename or the file path (e.g. Zone directory or subdirectory within the Zone) has a parentheses, images cannot be added to the markdown file.

**Workaround**

You can fix this issue by removing the parentheses from the filename or path. You can do this by going through the following three steps:

1\. Is the parentheses in the filename or in a subdirectory that is inside of the Zone?

If the parentheses is in the filename or a Zone subdirectory, you can simply open the OS explorer view and remove the parentheses. Do this by using Diode to view the folder containing the file, and click the open button:

![](/uploads/image-3.png)

That will open the operating system's explorer window, and you can click the path or file name to rename it by removing the parentheses.

2\. Is the parentheses in the Zone name itself?

If the parentheses is in the Zone name, you must first use the Zone Settings' "Zone Name" setting to first rename the Zone to remove the parentheses:

![](/uploads/image-4.png)

Then click the "Location on Disk":

![](/uploads/image-5.png)

Then click "Choose", and then immediately "Select" (no location change required), and then "Save" - your Zone has now been moved to the new name without the parentheses.

![](/uploads/image-6.png)

3\. Is the parentheses in the Zone's path?

If the special character is in the Zone's base path, you must use Zone Settings "Location on Disk" to move the Zone folder to a new location that does not have a parentheses in it.

Go to the Zone Settings, and click Location on Disk:

![](/uploads/image-7.png)

Then click "Choose" to select a new base directory whose path does not include a parentheses:

![](/uploads/image-8.png)

Click Save - your Zone has now been moved to the new name without the parentheses.

![](/uploads/image-9.png)

**Why do I have use this workaround?**

The technical reason why this workaround is required has to do with Markdown source syntax using parentheses itself to encapsulate an image path. Due to the different layers of encoding and decoding happening inside the file system, the app, the viewer, and the editor, supporting parentheses in the image path itself is not yet supported.