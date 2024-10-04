
# How to transfer files to/from the SD/LittleFS memory?

Use the [WebUI](https://github.com/pr3y/Bruce/wiki/Others#webui)


# Default passwords?

For AP mode wifi network the password is `brucenet`.

For the WebUI, username=`admin`, password=`bruce`


# IR/RF transmitter/receiver not working?

 - [IR requires a line-of-sight between the transmitter and the receiver](https://www.quora.com/Does-an-IR-remote-need-a-line-of-sight), which can be easily blocked by solid objects. [Other IR light sources like the sun can cause interferences](https://www.garagedoordoctorllc.com/can-sunlight-exposure-affect-garage-door-sensors/).
 [Solid objects can also block RF signals](https://jemengineering.com/blog-5-ways-physical-objects-impact-rf-signals/), especially if made of metal.
 - try putting the transmitter and receiver closer (<10cm), many cheap modules have poor ranges, or may be too noisy.
 - if using unofficially supported modules, double-check that the used pins are correct. These can be [changed in the Settings](https://www.youtube.com/watch?v=i4wRNeGQJfw).
 - check if the module is active and working during transmission:
   - for IR, you can [use a smartphone camera to check if the IR LED is blinking](https://www.youtube.com/watch?v=i4wRNeGQJfw).
   - use a multimeter or an oscilloscope to check activity on the data pin/LED/antenna.
   - use another device to check and compare the signals. e.g. [rtl_433](https://github.com/merbanan/rtl_433) for RF, [Tasmota](https://tasmota.github.io/docs/Tasmota-IR/) or a [Broadlink RM4 Pro](https://www.ibroadlink.com/productinfo/762672.html) for both IR and RF.
 - most RF modules only supports the 433MHz frequency with ASK/OOK modulation. Check if your `.sub` file or source signal is compatible.
 - check the [serial log](https://github.com/pr3y/Bruce/wiki/Serial) for errors, some signals may [fail to decode](https://github.com/pr3y/Bruce/issues/216).

# Port to non-M5Stack boards? CYD?

Not officially supported.

For boards that do not have screen and buttons, an [headless mode was added](https://github.com/pr3y/Bruce/issues/107). It can be controlled via the [WebUI](https://github.com/pr3y/Bruce/wiki/Others#webui) and [serial commands](https://github.com/pr3y/Bruce/wiki/Serial) only, and does not expose all the Bruce features.

For this to work, you have to manually add a new [configuration environment](https://docs.platformio.org/en/latest/projectconf/sections/env/index.html) in the [platformio.ini](https://github.com/pr3y/Bruce/blob/main/platformio.ini), and then define the pins and features for the modules you have connected.
Then, [compile the firmware for your new target](https://github.com/pr3y/Bruce/wiki/Building-from-source).

A sample env for the esp32-s3-devkitc-1 is [defined here](https://github.com/pr3y/Bruce/blob/3813139ae0fc220180e7d443d4d6caea3e689224/platformio.ini#845), it should work for all ESP32-S3 boards with 8MB PSRAM.


# What kind of files i need to put on the SD card?

There is some file examples of what you can do [in here](https://github.com/pr3y/Bruce/tree/main/sd_files), including [evil portal templates](https://github.com/pr3y/Bruce/tree/main/sd_files/portals), [nfcs](https://github.com/pr3y/Bruce/tree/main/sd_files/nfc) and [infrared](https://github.com/pr3y/Bruce/tree/main/sd_files/infrared)