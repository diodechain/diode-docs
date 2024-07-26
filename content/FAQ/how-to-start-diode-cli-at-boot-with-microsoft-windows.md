---
_schema: default
title: How To Start Diode CLI at Boot With Microsoft Windows
nav_title:
SEO_options:
  title: About Diode
  image:
  description:
draft: false
---
In this tutorial we install the Diode CLI, build our diode string .bat file, and place a .vbs file (that runs the .bat file) into the Windows Startup Directory so that it will run silently at boot.

By running the Diode CLI at boot, the computer can publish certain network resources securely (via the Diode Network) so that they can be accessed remotely.

1. Install [**Diode CLI**](https://diode.io/resources/download/) for Windows and <a href="https://www.architectryan.com/2018/03/17/add-to-the-path-on-windows-10/" target="_blank" rel="noopener"><strong>make sure it's added to the path variable</strong></a>
2. Create file `C:\ProgramData\Microsoft\Windows\diodeproxy.bat` that contains the diode string that is to be run on startup (see [**this article**](https://support.diode.io/article/ss32engxlq-publish-your-local-webserver) for details on how to format this string). For example, to publish localhost port 22 publically to the diode network, the string `diode publish -public 22:22` is placed in this file.
3. Create file `C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup\diodeproxysilent.vbs` that contains the following text:

   ```
   Set WshShell = CreateObject("WScript.Shell")
   WshShell.Run chr(34) & "C:\ProgramData\Microsoft\Windows\diodeproxy.bat" & Chr(34), 0
   Set WshShell = Nothing
   ```
4. The Diode String contained in `diodeproxy.bat` will now run at boot! To change the command ran at boot, simply edit the `diodeproxy.bat` file. If you choose to use a filename or directory other than the one in this example for the .bat file, line 2 of the code snippet above must be updated to reference your .bat file.

**Code Snippet Source:** [**https://www.winhelponline.com/blog/run-bat-files-invisibly-without-displaying-command-prompt/**](https://www.winhelponline.com/blog/run-bat-files-invisibly-without-displaying-command-prompt/)