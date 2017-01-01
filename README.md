# RSM  Firefox Theme

Offical [RSM](https://github.com/jacobtey/RSM-theme) Firefox theme.

#####RSM Firefox

![alt tag](http://i.imgur.com/UjJabE3.png)

#####RSM Darker Firefox

![alt tag](http://i.imgur.com/5fMURDp.png)

#####RSM Dark Firefox

![alt tag](http://i.imgur.com/5HuYVUl.png)


### Requirements
This theme is compatible with Firefox 40+ and Firefox 38 ESR

### Installation
The theme is available on addons.mozilla.org.

[RSM Firefox collection on AMO](https://addons.mozilla.org/en/firefox/collections/jacobtey/a/)

#### Manual building and installation

These instructions are for testers and package maintainers. They also allow to install the theme globally for all users.

You will need `autoconf` and `automake` for the following.

Clone the repository

    git clone https://github.com/jacobtey/rsm-firefox-theme && cd rsm-firefox-theme

Generate the .xpi files (drag and drop these into your Firefox window)

    ./autogen.sh --prefix=/usr
    make mkxpi

Alternatively the theme can be installed globally without using the .xpi files

    ./autogen.sh --prefix=/usr
    sudo make install

Other build options to append to `autogen.sh` are

    --disable-light         disable RSM Light Firefox support
    --disable-darker        disable RSM Darker Firefox support
    --disable-dark          disable RSM Dark Firefox support

Uninstall the theme with

    sudo make uninstall

#### Firefox ESR (Debian Stable users see here)
This repo includes separate Firefox ESR compatible branches. The installation process is mostly identical to the manual installation above

    git clone https://github.com/horst3180/rsm-firefox-theme && cd rsm-firefox-theme
    git checkout firefox-38-esr   # Execute this for Firefox 38 ESR
    git checkout firefox-45-esr   # Execute this for Firefox 45 ESR
    ./autogen.sh --prefix=/usr
    make mkxpi
