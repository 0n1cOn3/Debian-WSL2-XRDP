# Debian-WSL2-xrdp
Running KDE Plasma with xrdp over WSL2
## Entrance of the Guide

Do you wanna run Debian on WSL 2 and this with a GUI, so here we are:
Be sure you have WSL installed.

if WSL is not installed, check out here: https://docs.microsoft.com/en-us/windows/wsl/install-win10

If not already installed, get Debian from the MS-Store: https://aka.ms/wsl-debian-gnulinux

## Setup Debian
The first command which we gonna use is to put the $DISPLAY Variable into the bashrc file:

__*# echo '[ -z $DISPLAY ] && export DISPLAY=127.0.0.1:0.0' >> ~/.bashrc"*__

Now we have to install dbus-x11 for the important command:

__*# sudo apt install dbus-x11*__

and execute the command to configure dbus-x11

__*# dbus-launch --exit-with-x11 && sudo dbus-uuidgen --ensure"*__

Now we're almost done... You have just to change on Setting:

__*# sudo nano /etc/xrdp/rdxp.ini*__

__Change the port 3389 to 3390__ and save the file with Shift+X and Y and hit twice enter.

## IMPORTANT!

Highly recommended to remove the screensavers or your not able to login after Screensaver has started and you have to reboot lxss in Task Manager

__"# sudo apt purge xscreensaver gnome-screensaver light-locker i3lock"__
