# Windows™ US International XCompose for Linux

Latin speakers (spanish, brazilian-portuguese) using a US International keyboard layout faces a different behavior from Windows™ to Linux.

This repo was created to try to provide the same Windows™ behavior for latin speakers using an `en_US` keyboard layout.

It relies on use of [`uim`](http://en.wikipedia.org/wiki/Uim) as Input Method, which supports both GTK+ and Qt immodules with legacy [`XIM`](http://en.wikipedia.org/wiki/Xim) support.


# Install Instructions

* [Ubuntu/Debian](#ubuntu--debian)  
* [Fedora 20](#fedora-20)  
* [openSUSE](#opensuse)

## Ubuntu / Debian

### Binary Package

This deb package has a better approach then the manual installations: it creates a global Compose file, available to all users.

To install, open a terminal and run:

```term
sudo apt-get -y install uim
wget https://github.com/raelgc/win_us_intl/raw/master/deb/bin/win-us-intl_20140423-1_all.deb
sudo dpkg -i win-us-intl_20140423-1_all.deb
im-config -n uim
```

Logout and login.

### Manual Install

Open a terminal and run at home folder:

```term
wget https://raw.githubusercontent.com/raelgc/win_us_intl/master/.XCompose
sudo apt-get -y install uim
im-config -n uim
```
Logout and login.

## Fedora 20

Open a terminal and run at home folder:

```term
wget https://raw.githubusercontent.com/raelgc/win_us_intl/master/.XCompose
gsettings set org.gnome.settings-daemon.plugins.keyboard active false
sudo yum -y install uim uim-gtk3
imsettings-switch -q uim
```
Logout and login.

## openSUSE

Open a terminal and run at home folder:

```term
wget https://raw.githubusercontent.com/raelgc/win_us_intl/master/.XCompose
sudo zypper in uim
```
Logout and login.


# Known Issues

1. Ubuntu Unity Dash don't respect the cedilla. Any other programs will work fine (Firefox, Google Chrome, Gnome programs, KDE programs, etc).
2. Some obscure key combinations haven't been covered yet (acute + ß).
3. Some dead key combinations don't work at all (acute + diaeresis != '")


# How to Contribute

If you modify this file to improve the compatibility with the
 original Windows US Intl Behavior, please open an issue in this repo.
 We'll gladly merge both files after determine those changes will
 match the usual behavior in Windows, giving credit where due
