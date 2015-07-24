# meta-edison-rt - add some useful things to the standard Intel Edison distro

meta-edison-rt is a layer that can be used with the standard Intel Edison distro to add some convenient extra capabilities including the Qt embedded runtime. Some of the recipes are from meta-oe and an alternative is to add that in device-software as described in the Edison BSP User Guide.

This is very much a work in progress.

Specific additions are:

    IMAGE_INSTALL += "bison"
    IMAGE_INSTALL += "coreutils"
    IMAGE_INSTALL += "git"
    IMAGE_INSTALL += "portaudio-v19"
    IMAGE_INSTALL += "espeak"
    IMAGE_INSTALL += "alsa-lib"
    IMAGE_INSTALL += "alsa-utils"
    IMAGE_INSTALL += "alsa-tools"

    # This sets the default audio output to be plughw:1,0
    IMAGE_INSTALL += "alsa-defaults"

    IMAGE_INSTALL += "nano"
    IMAGE_INSTALL += "packagegroup-core-qt4e"
    IMAGE_INSTALL += "cmake"
    
### Installation

Using "..." to represent the install directory of the Edison source:

    cd .../edison-src/device-software
    git clone git://github.com/richards-tech/meta-edison-rt
    
The layer needs to added to the bblayers.conf file which is at:

    .../edison-src/build/conf/bblayers.conf
    
Add a line to the layers so that the BBLAYERS variable looks like this:

    BBLAYERS ?= " \
        .../edison-src/poky/meta \
        .../edison-src/poky/meta-yocto \
        .../edison-src/poky/meta-yocto-bsp \
        .../edison-src/device-software/meta-edison \
        .../edison-src/device-software/meta-edison-distro \
        .../edison-src/device-software/meta-edison-middleware \
        .../edison-src/device-software/meta-edison-arduino \
        .../edison-src/device-software/meta-edison-devtools \
        .../edison-src/device-software/meta-edison-rt \
        \
        "
        
    
Then the usual "bitbake edison-image" should work and add the new features.


