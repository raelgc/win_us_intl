# Windows™ US International XCompose for Linux

![Keyboard](keyboard.jpg)

Latin speakers (spanish, brazilian-portuguese) using a US International keyboard layout faces a different behavior from Windows™ to Linux.

This repo was created to try to provide the same Windows™ behavior for latin speakers using an `en_US` keyboard layout.

It relies on use of [`uim`](http://en.wikipedia.org/wiki/Uim) as Input Method, which supports both GTK+ and Qt immodules with legacy [`XIM`](http://en.wikipedia.org/wiki/Xim) support.


# Install Instructions

* [Ubuntu/Debian](#ubuntu--debian)  
* [Fedora 20 to 26](#fedora-20-to-26) 
* [Fedora 27 and later](#fedora-27-and-later)  
* [openSUSE](#opensuse)
* [Arch Linux](#arch-linux-with-gnome)

## Ubuntu / Debian

### Binary Package (Unity and Ubuntu GTK environments)

This deb package has a better approach then the manual installations: it creates a global Compose file, available to all users.

To install, open a terminal and run:

```term
sudo apt-add-repository -y ppa:rael-gc/utils
sudo apt update
sudo apt install win-us-intl
gsettings set org.gnome.settings-daemon.plugins.xsettings disabled-gtk-modules '["'keyboard'"]'
im-config -n uim
```

Logout and login. If that doesn't work, try rebooting the system.

## Manual Install (KDE and other QT environments)

Open a terminal and run at home folder:

```term
wget https://raw.githubusercontent.com/raelgc/win_us_intl/master/.XCompose
sudo apt-get -y install uim
im-config -n uim
```
Logout and login. If that doesn't work, try rebooting the system.

## Fedora 20 to 26

Open a terminal and run at home folder:

```term
wget https://raw.githubusercontent.com/raelgc/win_us_intl/master/.XCompose
gsettings set org.gnome.settings-daemon.plugins.keyboard active false
sudo yum -y install uim uim-gtk3
imsettings-switch -q uim
```

Logout and login. If that doesn't work, try rebooting the system.

## Fedora 27 and later

```term
wget https://raw.githubusercontent.com/raelgc/win_us_intl/master/.XCompose
gsettings set org.gnome.settings-daemon.plugins.xsettings disabled-gtk-modules '["'keyboard'"]'
sudo yum -y install uim uim-gtk3
imsettings-switch -q uim
```

Logout and login. If that doesn't work, try rebooting the system.

## openSUSE

Open a terminal and run at home folder:

```term
wget https://raw.githubusercontent.com/raelgc/win_us_intl/master/.XCompose
sudo zypper in uim
```
Logout and login. If that doesn't work, try rebooting the system.

## Arch Linux (with GNOME)

Open a terminal and run at home folder:
```term
wget https://raw.githubusercontent.com/raelgc/win_us_intl/master/.XCompose
gsettings set org.gnome.settings-daemon.plugins.xsettings disabled-gtk-modules '["'keyboard'"]'
sudo pacman -S uim
```

Include these lines on file `~/.xprofile`:
```shell
export GTK_IM_MODULE=uim
export QT_IM_MODULE=uim
uim-xim &
export XMODIFIERS=@im=uim
```

Logout and login. If that doesn't work, try rebooting the system.


# Known Issues

1. Ubuntu Unity Dash don't respect the cedilla. Any other programs will work fine (Firefox, Google Chrome, Gnome programs, KDE programs, etc).
2. Some obscure key combinations haven't been covered yet (acute + ß).
3. Some dead key combinations don't work at all (acute + diaeresis != '")

# Troubleshooting

## 1. It's not working for me

Make sure your keyboard is using `English (US, intl., with dead keys)` as layout.
Make sure you logged out before testing.
Make sure you rebooted your computer if logging out didn't work.
In case of issues with `Qt` environments, try define global variables like described in [uim/Setup](https://en.wikibooks.org/wiki/Uim/Setup) page.

## 2. Uim is displaying a toolbar

New versions of `uim` are displaying a float toolbar, which can be removed. Open `uim-pref-gtk` (or `uim-pref-qt`) and in **Toolbar** section change `Display` value to `Never`.

## 3. Double quotes are not working if I press <kbd>' + Shift + Space</kbd>

New versions of `uim` have Global Bindings using <kbd>Space</kbd> and <kbd>Shift</kbd> as accelerators. Open `uim-pref-gtk` (or `uim-pref-qt`) and at the **Global Key Bindings 1** and **Global Key Bindings 2** section edit all shortcuts, removing the assigned keys.

## 4. It doesn't work with an application

Please, take a look in the [Uim Troubleshooting guide](https://en.wikibooks.org/wiki/Uim/Troubleshooting), specifically in the "**Uim doesn't work with an application**" section.

If the Qt or GTK immodule causes application crashes or it doesn't work, try to force uim to use XIM in the application: 

    QT_IM_MODULE=xim opera # force uim to use XIM in Opera


# How to Contribute

If you modify this file to improve the compatibility with the original Windows US Intl Behavior, please open an issue in this repo. We'll gladly merge both files after determining those changes will match the usual behavior in Windows, giving credit where due.
