## Linux version of Amlogic USB Burning Tool

# Installation
1. Create a new udev rule for Amlogic devices (in `/etc/udev/rules.d`). Name it `70-persistent-usb-amlogic.rules`. The content of the file should be:

```
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", ATTR{idVendor}=="1b8e", ATTR{idProduct}=="c003", MODE:="0666", SYMLINK+="worldcup"
```

2. This tool depends on `libusb-0.1-4`. You must install these tools first.

After creating your rule, either reload udev rules or reboot your machine. Ensure that the root folder of this repository is in your PATH variable or switch to this folder and give execute permissions to use.

# How to use
Connect your device and put it into USB burning mode. Open a terminal and navigate to the folder where your `aml_upgrade_package.img` is located. Issue the command:

```
aml-flash --img=aml_upgrade_package.img --soc=gxl --wipe --reset=n --parts=all
```

For more options, just issue the `aml-flash` command. The __soc__ parameter can be gxl (S905, S905X, and S912), axg (A113 audio SoC), txlx (TV SoC - T962), m8 (S802, S805, and S812). I have tested this tool successfully on S812, S905, S905X, and S912.

# Note
This tool is for Linux x86-64 only.
