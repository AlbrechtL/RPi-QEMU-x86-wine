RPi-QEMU-x86-wine SD-card image
===============================


Description
-----------
This Raspberry Pi image enables you to run x86 Linux and Windows applications on a Raspberry Pi (all models inc pi3).
The build is based on the information found in the following thread: https://forum.winehq.org/viewtopic.php?f=8&t=17701&start=25#p84325

![Notepad Screenshot](/Screenshots/Notepad.png?raw=true)

(Originally based on AlbrechtL's Wheezy image - updated to work with Pi Zero, and Pi3 
also now Jessie version)

Download
--------
- [https://sourceforge.net/projects/pi-qemu-wine/]

Installation
------------
- You will need a 4 GB SD-card
- Unpack the image
- Copy the image to a SD-card

        # sudo dd bs=4M if=20150924_RPi-QEMU-x86-wine.img /dev/mmcblk

- Put the SD-card into your Raspberry Pi

Usage
-----
Two user are available
- Username: pi
- Password: raspberry


- Username: root
- Password: 123456

To run x86 Linux and Windows programs just run the "start_x86env_wine-user" script as the "pi" user in a terminal.
     
    # sudo /home/pi/start_x86env_wine-user

Now you are in a Debian wheezy i386 enviroment and you can try to load any x86 program. Inside the chroot enviroment you are logged in as the user "wine-user".

To run Windows programs just run "wine". Notepad example:

    # wine ~/.wine/drive_c/windows/notepad.exe


If you would like to use programs that need super user access like "apt-get" run the script "/home/pi/start_x86env_root" instead of "start_x86env_wine-user":

    # sudo /home/pi/start_x86env_root


Included Software
-----------------
- Based on 2015-05-05-raspbian-wheezy.img
- Kernel 4.1.8 with 3G/1G user/kernel memory split: https://forum.winehq.org/viewtopic.php?t=1905
- QEMU 1.4.0 with NPTL patch: https://github.com/AlbrechtL/qemu
- Wine 1.5.26: http://www.playonlinux.com/wine/binaries/linux-x86/PlayOnLinux-wine-1.5.26-linux-x86.pol
- Installed Debian Wheezy i386 repository in a chroot enviroment "/home/pi/chroot-wheezy-i386".
- Binfmt: To wrap the call to QEMU


Speed
-----
Don't expect a super fast PC! The x86 emulation is done by QEMU in software.
Some people said it is as fast as a 300 MHz Pentium PC. But benchmarks a welcome!

More Information
-----------------
Please read the following threads:
- https://www.raspberrypi.org/forums/viewtopic.php?f=41&t=12727
- https://forum.winehq.org/viewtopic.php?f=8&t=17701&sid=c5501c4a5fb33680caf6a37b47cf62ed
- http://www.forum-raspberrypi.de/Thread-raspbian-windowsprogramme-ausfuehren-mit-qemu-und-wine (only German)
- http://wiki.winehq.org/ARM
