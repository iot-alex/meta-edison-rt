# meta-edison-rt - add some useful things to the standard Intel Edison distro

meta-edison-rt is a layer that can be used with the standard Intel Edison distro to add some convenient extra capabilities including the Qt embedded runtime. Some of the recipes are from meta-oe and an alternative is to add that in device-software as described in the Edison BSP User Guide.

This is very much a work in progress.

Specific additions are:

    IMAGE_INSTALL += "bison"
    IMAGE_INSTALL += "coreutils"
    IMAGE_INSTALL += "git"
    IMAGE_INSTALL += "nano"
    IMAGE_INSTALL += "packagegroup-core-qt4e"
    IMAGE_INSTALL += "cmake"
    
### Installation

Using "..." to represent the install directory of the Edison source:

    cd .../edison-src
    git clone git://github.com/richards-tech/meta-edison-rt
    
The layer needs to added to the bblayers.conf file which is at:

    .../edison-src/out/current/conf/bblayers.conf
    
Add a line to the layers so that the BBLAYERS variable looks like this:

    BBLAYERS ?= " \
        .../edison-src/out/linux64/poky/meta \
        .../edison-src/out/linux64/poky/meta-yocto \
        .../edison-src/out/linux64/poky/meta-yocto-bsp \
        .../edison-src/meta-intel-edison/meta-intel-edison-bsp \
        .../edison-src/meta-intel-edison/meta-intel-edison-distro \
        .../edison-src/out/linux64/poky/meta-intel-iot-middleware \
        .../edison-src/meta-intel-edison/meta-intel-arduino \
        .../edison-src/meta-arduino \
        .../edison-src/meta-edison-rt \
        \
    "
        
    
Then the usual "bitbake edison-image" should work and add the new features.


