Sonic Bike Init
============================

Scripts used to startup the sonic bike system. There are four seperate elements that need to be installed/configured in order to get the system up and running on a Beaglebone Black:

- A. Operating system: 3.8.13-bone47.
- B. Init scripts: Contains ultility scripts for auto-start etc.
- C. The sonic bike software: app-findingsong OR app-swamp.
- D. SD Card: Contains a configeration file, sound and map files.

## A. Operating system
Check if you are running kernel version "3.8.13-bone47":

    $ uname -a

###Skip this next section if you are running the correct Kernel
If you have an earler or later version then we can't be sure that things will work properly as we found errors with audio playback in later versions of the kernal. To install the correct version of the kernel, as root (not sudo). You may need to perform these actions while within an SD card as there needs to be space to download large files:

    $ wget https://github.com/RobertCNelson/linux-dev/archive/3.8.13-bone47.tar.gz
    $ gunzip 3.8.13-bone47.tar.gz
    $ tar -xvf 3.8.13-bone47.tar
    $ cd linux-dev-3.8.13-bone47
    $ sudo apt-get install bc lzma lzop libncurses5-dev 
    $ ./build_deb.sh

###Configure the OS
[TODO]

## B. Init scripts
[TODO]
Clone this repository and setup the systemd service so it auto-starts

    cd /home/sonic
    git clone https://github.com/sonicbikes/sonic-bike-init.git
    ln -s /home/sonic/sonic-bike-init/sonic-bike.service /etc/systemd/system/sonic-bike.service

## C.The sonic bike software: app-findingsong OR app-swamp.
There are currently two versions of the software available "app-swamp" which is the --original-- version and "app-findingsong" which is the latest version. The configeration file found on the sd card (instructions below) determines which of these should load up. Both versions of the software can be obtained from github:

    cd /home/sonic
    git clone https://github.com/sonicbikes/app-findingsong.git
    git clone https://github.com/sonicbikes/app-swamp.git

## D. The SD card: Setup

A directory need to be created where the SD card will mount to:
    
    sudo mkdir /home/sonic/sdcard

This directory should contain a configeration file named config.json and folders containing audio files



