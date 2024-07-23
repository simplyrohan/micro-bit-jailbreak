# micro-bit-jailbreak
An attempt to create a custom firmware for the BBC micro:bit so full functionality of the Arm Cortex®-M0 processor can be used.

# references
[Offical Micropython Implementation](https://github.com/bbcmicrobit/micropython)

[Bluetooth NodeJS Custom Firmware](https://github.com/sandeepmistry/node-bbc-microbit-firmware/tree/master?tab=readme-ov-file)

# building
The current micro:bit firmware uses a `yotta` build system ([install](https://docs.yottabuild.org/#installing-on-linux)).
However, the project is deprecated and unmaintained. Unsurprisingly so, I could not install it locally due to many conflicting packages. I did manage to install it on an Ubuntu virtual machine (Github Codespace)

After installing yotta, on an Ubutu system run
```
sudo add-apt-repository -y ppa:team-gcc-arm-embedded
sudo apt-get update
sudo apt-get install gcc-arm-embedded
sudo apt-get install cmake ninja-build srecord libssl-dev
sudo -H pip3 install yotta
```

That alone from the micropython repository, wasn't enough for me. I also needed to install gcc-arm-none-eabi
```
gcc-arm-none-eabi
```

Then just follow the instructions from the micropython implementation
```
yotta target bbc-microbit-classic-gcc-nosd@https://github.com/lancaster-university/yotta-target-bbc-microbit-classic-gcc-nosd

yotta up

make all
```
It will produce a hex file in `build/`. Just drag that over your micro:bit drive and your done.