## Win US Intl Keyboard Layout for Linux

Latin speakers (spanish, brazilian-portuguese) using a US International keyboard layout faces a different behavior from Windows(TM) to Linux.

This repo was created to try to provide the same Windows(TM) behavior for latin speakers using a `en_US` keyboard layout.

It relies on use of [`uim`](http://en.wikipedia.org/wiki/Uim) as Input Method, which supports both GTK+ and Qt immodules with legacy [`XIM`](http://en.wikipedia.org/wiki/Xim) support.


### Install Instructions (Ubuntu)

1. Download the .XCompose file to your home. Run in terminal:

    `wget https://raw.githubusercontent.com/raelgc/win_us_intl/master/.XCompose`

2. Install [`uim`](http://en.wikipedia.org/wiki/Uim) to enable .XCompose compatibility:

    `sudo apt-get install uim`

3. Make `uim` the default Input Method for user under X Window System:

    `im-config -n uim`

4. Logout and login (or restart all programs you were using).

5. To test it, run in terminal:

    `$ strace -e open xterm |& grep Compose`
    
    Output will be like:

    ```term    
    open("/home/rael/.XCompose", O_RDONLY)  = 6
    open("/usr/share/X11/locale/en_US.UTF-8/Compose", O_RDONLY) = 7
    ```

### Known Issues

1. Ubuntu Unity Dash don't respect the cedilla. Any other programs will work fine (Firefox, Google Chrome, Gnome programs, KDE programs, etc).
2. Some obscure key combinations haven't been covered yet (acute + ß).
3. Some dead key combinations don't work at all (acute + diaeresis != '")

### How to Conttribute

If you modify this file to improve the compatibility with the
 original Windows US Intl Behavior, please open an issue in this repo.
 We'll gladly merge both files after determine those changes will
 match the usual behavior in Windows, giving credit where due
