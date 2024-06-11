# Debian-WSL2-xrdp
### Running KDE Plasma with xrdp on WSL 2

This guide will help you set up Debian on WSL 2 with a KDE Plasma GUI, accessed via xrdp. 
Before you start, ensure that WSL is installed on your system. 

**Note: that this method was developed before Microsoft introduced official GUI support in WSL 2.**

If WSL is not installed, please follow the instructions [here](https://learn.microsoft.com/en-us/windows/wsl/install).

If you haven't already, install Debian from the Microsoft Store: [Debian WSL](https://aka.ms/wsl-debian-gnulinux).

### - Setting Up Debian:

- Set the DISPLAY Variable:
Append the following line to your .bashrc file to set the DISPLAY variable:


```echo '[ -z $DISPLAY ] && export DISPLAY=127.0.0.1:0.0' >> ~/.bashrc```

- Install dbus-x11:
Install the dbus-x11 package which is necessary for dbus support:

```sudo apt install dbus-x11```

After installation, configure dbus-x11 with the following commands:

```dbus-launch --exit-with-x11	sudo dbus-uuidgen --ensure```

### - Configure xrdp:

Edit the xrdp.ini configuration file to change the default port:

```sudo nano /etc/xrdp/xrdp.ini```

In the file, locate the line with port=3389 and change it to:

```port=3390```

Save the file by pressing Ctrl+X, then Y, and hit Enter twice.

### - Remove Screensavers:
It is highly recommended to remove screensavers to avoid issues with login after the screensaver starts. Run the following command to remove them:

```sudo apt purge xscreensaver gnome-screensaver light-locker i3lock```

By following these steps, you should be able to run Debian on WSL 2 with a KDE Plasma GUI accessible via xrdp. 
If you encounter any issues, you may need to reboot the WSL instance or check the configurations again. 
