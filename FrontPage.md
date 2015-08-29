Simple VNC viewer that is built with **[Twisted-Python](http://twistedmatrix.com/trac/)** and **[pygame](http://www.pygame.org/)**. Originally written by Chris Liechti.

The viewer supports the following encodings: `Hextile, CoRRE, RRE, RAW, CopyRect`

The display is done using pygame because of it's good graphics performance but any GUI system can be used as the code is modular and can easily adapted. Two good examples of code reuse are [VNC client in browser](http://arkaitzj.wordpress.com/2011/11/12/vnc-in-your-browser-through-websockets-handled-by-gevent/) by Arkaitz Jimenez, and most recent [vncdotool](http://sibson.github.io/vncdotool/) by Marc Sibson. Pygame version supports clipboard transfer, but it's not used in the sample application.

## Usage ##

You can simply start `vncviewer.py` and it will ask for a hostname and password if required. Hostnames are in the "host:display" form, where "display" is the VNC dispaly number.

These setting can also be passed over the command line. Note that it's a bad idea to pass the password on the command line as it can be snooped by other users with a simple process listing!

Try -h or --help to see the possible options.

Please keep in mind that VNC transmits keypresses in cleartext, so don't type in passwords on non-encrypted connection over insecure networks.

With "--depth" a display depth can be gived, use "8" for
slower connections.

The "--fast" option uses only RAW and CopyRect encodings and is thus only suitable for fast connections. But delivers better performance in that case, than using the other encodings too.

## What is it good for? ##

Nothing ;-) Use the original VNC viewer for better performance.

However it works very well and seems with a good speed. It could be embedded in other applications that are written in Python or it can be the base of various applications like
supervision of remote desktops, automated tests of GUIs or be embedded in a too for remote support...

## Bugs, etc ##

  * Properties dialog is missing. Like for specifying encodings etc.
  * Listen mode not implemented.
  * Key repetition does not work (pygame?)
  * It does not reduce update requests when minimized.
  * Screen cannot be scrolled, impractical if remote desktop is larger than local
  * The password dialog blocks twisted and everything else