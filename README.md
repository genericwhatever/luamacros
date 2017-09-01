# Luamacros
This software can recognize and manage multiple keyboards connected to your computer with Windows OS. This key feature allows you to use it as a macro triggering application.
Other typical usage is for flight simulation, where macro triggers can come from various sources, like:
* Secondary keyboards
* Game controllers (Joysticks)
* COM interface (Arduino)
* A small embedded http server
* The flight simulator itself - Xplane, on variable change

Macro actions can be anything scripted in the Lua language with some extensions:
* Serial communication
* Xplane simulator events (commands, data ref changes)
* Http get
* OS commands

For details see http://www.hidmacros.eu/forum/.

# Binary Download
Download [luamacros.zip](http://www.hidmacros.eu/luamacros.zip).

# Developers Guide
To compile & extend Luamacros yourself, you must:
* Download & install the lates Lazarus environment: https://www.lazarus-ide.org/
* Clone Luamacros code from this repository: https://github.com/me2d13/luamacros.git
* Before opening luamacros project you need to install several packages into Lazarus IDE. They are located in the lib subfolder. Maybe this could be somehow included into Lazarus project, but I'm not such expert - just found a way that works. Those packages are:
  * Inetbase - for http communication 
  * uniqueinstance_package - to ensure only one luamacros instance is running
  * ExtraHighliters_RT - for Lua syntax highlighting
  * LazSerialPort - for COM device communication
* Those packages have zip files in the lib subdirectory. Just extract those zip files, open the lpk file from extracted location and choose 'Use - Install'.
* Now you should be able to open all 3 projects. These are:
  * LuaMacros - the main application exe. Important: if you need to execute compiled exe don't forget to copy lua dlls from lib directory to the same place as exe file
  * XplPlugin - dll used as XPlane plugin. Note this is 64b project so you need to adapt FPC compiler accordingly
  * WinHook - dll to set global keyboard hook
* When starting from your build environment make sure you copy LUA dlls (see lib folder) into your output directory. These dlls must be in the same directory as LuaMacros.exe. Without them the program won't even start, or will crash with some segmentation error (in IDE).

Hope it helps, have fun, feel free to extend this guide
