---
_schema: default
title: Change Profile Directory
nav_title: Change Profile Directory
nav_section: For Your IT Admin
weight: 304
draft: false
---
Diode Drive supports changing the <a href="https://support.diode.io/article/e7gtnjcp5o" target="_blank" rel="noopener"><strong>profile directory</strong></a> away from the default location by using one of the following methods:

**Use a file**

1. Move your current ~/.config/ddrive directory to its new location (or create a blank folder in the location you want to house your profile). The folder name can be anything - it doesn't have to be called "ddrive".

On Mac or Linux, you can do this by opening a terminal window and, for example, typing: `mv ~/.config/ddrive ~/Desktop/ddrive`

1. Create a new **file** called "ddrive." in the .config folder (e.g. on a Mac, at ~/.config/ddrive.).

On Mac or Linux, you can do this by opening a terminal window and typing `touch ~/.config/ddrive`

1. Edit the ddrive file to add a line containing the absolute path to the new location. The ddrive file it is a text file and should have a single line containing path, ending with the profile folder name.

On Mac or Linux, you can do this by opening a terminal window and typing `nano ~/.config/ddrive` - that will open the Nano editor, where you can type your new path, and save the file. For example:

![](/uploads/image-32.png)

**Set an environment variable**

Add `export CONFIG_DIR=/your/desired/path/to/config` to your `~/.profile` file, then log out & back in, to override your configuration directory.