dwm - dynamic window manager
============================

My build of dwm for Arch Linux, Void Linux, and FreeBSD.

Patches in the `patches/done` dir are those that have been applied to this build.

**Branch names** indicate their corresponding system/distro.

Note
------------
For Gentoo Linux, I prefer to delegate to Portage management of suckless utilities, since installation via compilation is the natural way on Gentoo. See my [overlay repo](https://github.com/Linerre/interlay) and [protage config repo](https://github.com/Linerre/portage.d) for more details.


Requirements
------------
In order to build dwm you need the Xlib header files.

On Void Linux, the following pkgs need to be installed before building:

	# xbps-install -S base-devel libX11-devel libXft-devel libXinerama-devel

On FreeBSD, you might need to install pkgconfig:

	# pkg install pkgconfig


Installation
------------
Edit `config.mk` to match your local setup (dwm is installed into
the `/usr/local/bin` dir by default).

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
