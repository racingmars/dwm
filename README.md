dwm - dynamic window manager
============================
dwm is an extremely fast, small, and dynamic window manager for X.

Matthew's DWM Customizations
----------------------------

This repository contains the build of DWM that I use on my desktop. It
contains the following patches from https://dwm.suckless.org/patches/,
modified as necessary to work together nicely:

 * actualfullscreen (Add a real fullscreen mode instead of just the
                     monocle layout; toggle with Mod4-F.)
 * pertag       (Keep layout and other properties per tag instead of global.)
 * vanitygaps   (Add gaps around windows. _Note_: all dynamic gap size
                 modification functions except togglegaps are removed.
		 togglegaps is invoked with Mod4-Ctrl-0.)

The original patches are in the patches directory.

Additionally, this repository contains my own configuration (in config.h; the
config.h.def file is maintained as the defaults as modified by each patch).

The dwm.1 man page isn't modified to reflect the customizations: you may read
it for a general idea of how dwm works, but the definitive source of key
bindings is the `config.h` file in this repository.

The remainder of this readme is the original dwm readme.


Requirements
------------
In order to build dwm you need the Xlib header files.


Installation
------------
Edit config.mk to match your local setup (dwm is installed into
the /usr/local namespace by default).

Afterwards enter the following command to build and install dwm (if
necessary as root):

    make clean install


Running dwm
-----------
Add the following line to your .xinitrc to start dwm using startx:

    exec dwm

In order to connect dwm to a specific display, make sure that
the DISPLAY environment variable is set correctly, e.g.:

    DISPLAY=foo.bar:1 exec dwm

(This will start dwm on display :1 of the host foo.bar.)

In order to display status info in the bar, you can do something
like this in your .xinitrc:

    while xsetroot -name "`date` `uptime | sed 's/.*,//'`"
    do
    	sleep 1
    done &
    exec dwm


Configuration
-------------
The configuration of dwm is done by creating a custom config.h
and (re)compiling the source code.
