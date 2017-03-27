Quick Start Guide
03/27/2017
Egan Ford <egan@sense.net>

NOTE: READ ALL INSTRUCTIONS

Prereqs:

* MacOS 10.12 64-bit:

  * Install XQuartz, Xcode (from your installation media) in that order.
  * Install Macports (macports.org), then:

  sudo port install gtk2 pkgconfig gcc6
  sudo port select --set gcc mp-gcc6
  export PATH=/opt/local/bin:$PATH


* Ubuntu:

  sudo apt-get install libgtk2.0-dev 


* RedHat/CentOS:

  sudo yum install subversion gtk2-devel

------------------------------------------------------------------------

Start up X11 and use xterm

------------------------------------------------------------------------

Download x49gp source:

git clone https://github.com/datajerk/x49gp.git

------------------------------------------------------------------------

Edit FIRMWARE (optional):

The default firmware will be 4950_92.bin, for HPGCC3 development copy
49_hpgcc.bin in to x49gp and change FIRMWARE in the Makefile.

------------------------------------------------------------------------

Build:

cd x49gp
make
make sdcard
make config

------------------------------------------------------------------------

Mount SD card:

OS/X:

open sdcard.dmg

Linux:

sudo mkdir -p /Volumes/X49GP/
sudo mount -o loop sdcard /Volumes/X49GP

------------------------------------------------------------------------

Put stuff in SD, e.g.:

OS/X:

cp BACKUP /Volumes/X49GP/

Linux:

sudo cp BACKUP /Volumes/X49GP/

NOTE:  If using HPGCC2 don't forget the the ARMToolbox.

------------------------------------------------------------------------

Eject SD:

OS/X:

hdiutil detach $(df | grep -i x49gp | head -1 | awk '{print $1}')

Linux:

sudo umount /Volumes/X49GP

------------------------------------------------------------------------

Run:

./x49gp config

------------------------------------------------------------------------

Where's the key labels?

Good question.  This is a bug when compiled for 64-bit platforms.

Hack:

cp hp50g-hack.png hp50g.png

------------------------------------------------------------------------

Do stuff, e.g.:

Restore backup:

BACKUP
3
-\>TAG
RESTORE

Install ARMToolbox (HPGCC2):

2
SETUP.BIN
3
-\>TAG
RCL
EVAL
(Right Click ON, Left Click C)

------------------------------------------------------------------------

To Exit Emulator

* ctrl-c to exit (from launch window)

------------------------------------------------------------------------

Start Over:

* clean slate?

rm -f flash-49g+ flash-50g flash-noboot sram s3c2410-sram
make flash-49g+ flash-50g flash-noboot sram s3c2410-sram
./newconfig

* soft reset only?

./newconfig

------------------------------------------------------------------------

Known Limitations:

* HPGCC SD Card I/O
  . libfsystem unavailable.
  . f* calls unstable (HPGCC2)
  . f* calls stable (HPGCC3)

------------------------------------------------------------------------

Change Log:

Additional note: August 22, 2013

Updated this so that it'll compile on Ubuntu 12.04.

--Nicholas Kirchner

