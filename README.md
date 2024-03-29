# NitrogenOS FAN Edition #
<img src="https://i.imgur.com/t0nutAA.png">
====================

Create dirs, and install soft, libs
-----------------------------------

    sudo su
    apt update
    apt install repo git gnupg flex bison gperf build-essential zip curl zlib1g-dev gcc-multilib g++-multilib libc6-dev-i386 libncurses5 rsync lib32ncurses-dev x11proto-core-dev libx11-dev lib32z1-dev libgl1-mesa-dev libxml2-utils xsltproc unzip fontconfig
    exit

Create Nitrogen Fan Edition folder
----------------------------------

    mkdir ~/nosfe
    cd ~/nosfe

GIT config (nickname, e-mail)
-----------------------------

    git config --global user.email "mail@domain.com"
    git config --global user.name "login"

To initialize your local repository use
---------------------------------------

    repo init -u https://github.com/nitrogen-os-fan-edition/android_manifest.git -b 11

If you want to save time and space you can do a shallow clone
---------------------------------------

    repo init -u https://github.com/nitrogen-os-fan-edition/android_manifest.git -b 11 --depth=1
    
Then to sync up:
----------------

    repo sync -c -j$(nproc --all) --force-sync --no-clone-bundle --no-tags

OR to sync up without spam in your term:
----------------------------------------

    repo sync -c -q --force-sync --optimized-fetch --no-tags --no-clone-bundle --prune -j$(nproc --all)

Build command are:
------------------
    . build/envsetup.sh
    lunch nitrogen_$device-userdebug
    make -j$(nproc --all) otapackage
