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

Unity Dash don't respect the cedilla. Any other programs will work fine (Firefox, Google Chrome, Gnome programs, KDE programs, etc).

### Credits

Original version of .XCompose file was taken from http://tamh.info/en/win-us-intl-4-linux. I just changed few entries to make it don't raise some warnings.
