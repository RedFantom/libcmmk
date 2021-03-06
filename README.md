An unofficial implementation of the Masterkey Lighting API that can be used
to programmatically control LEDs of Coolermaster Masterkey keyboards.

Based entirely on captured USB data without any reverse engineering performed
on official binaries.

# Device Support
The currently supported and known to work devices include:

 * MasterKeys Pro L, (EU / German only)
 * MasterKeys Pro S, (US only)
 * MasterKeys MK750, (EU / German only)

In theory (and as a goal), this library should support any RGB (and in the future possibly monocolor)
MasterKeys keyboards. Gaps in device support are currently a result of a lack of test devices. See
the "Contributing" section if you would like to help in this regard.

# Implemented features:
  - Profile customization (comparable to the official control software)
    * Switching between P1 - P4
    * Configuring effects
    * Configuring custom background lighting
    * Saving profile customizations to the firmware
    * Multilayer/mosaic mode support

  - Manual control (comparable to the official SDK)
    * Set the entire keyboard to a single color or a color map
    * Set individual keys
    * Activate and configure effects active during manual control

# Contributing
Pull requests for new model support, bug fixes or anything else are always appreciated. If your
keyboard model and layout (ISO/ANSI) combination is not among the supported devices and you want
to help out, feel free to open an issue to let me know.

While the protocol is mapped out enough at this point to fully replicate the official control
center software, there are still some unanswered questions. I'll happily take more protocol samples
from other models to try and decipher the remaining packets.

So if you know you way around Wireshark and usbmon or similar capture tools, feel free to record 
some samples and open a new issue for them.

# Build requirements:
  - A C compiler from at least the current century (C99)
  - libusb-1.0


# Ubuntu

## Install dependencies

```
sudo apt-get install libusb-1.0-0-dev
```

## Compile and run:

```
make clean && make
```

Requires root:

```
sudo LD_LIBRARY_PATH=/path/to/out/subdirectory/out:$LD_LIBRARY_PATH ./out/cmmk-testsu
```
