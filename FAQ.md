
# How to transfer files to/from the SD/LittleFS memory?

Use the [WebUI](https://github.com/pr3y/Bruce/wiki/Others#webui)


# Default passwords?

For AP mode wifi network the password is `brucenet`.

For the WebUI, username=`admin`, password=`bruce`


# IR/RF transmitter/receiver not working?

 - [IR requires a line-of-sight between the transmitter and the receiver](https://www.quora.com/Does-an-IR-remote-need-a-line-of-sight), which can be easily blocked by solid objects. Light can bounce off some surfaces and still reach the receiver, but don't rely on that too much. [Other IR light sources like the sun can also cause interferences](https://www.garagedoordoctorllc.com/can-sunlight-exposure-affect-garage-door-sensors/).
RF signals propagate in all directions and does not require a line of sight, but can [still be blocked by solid objects](https://jemengineering.com/blog-5-ways-physical-objects-impact-rf-signals/), especially if made of metal.
 - try putting the transmitter and receiver closer (<10cm), many cheap modules have poor ranges, or may be too noisy.
 - if using unofficially supported modules, double-check that the used pins are correct. These can be [changed in the Settings](https://www.youtube.com/watch?v=i4wRNeGQJfw).
 - check if the module is active and working during transmission:
   - for IR, you can [use a smartphone camera to check if the IR LED is blinking](https://www.youtube.com/watch?v=i4wRNeGQJfw).
   - use a multimeter or an oscilloscope to check activity on the data pin/LED/antenna.
   - use another device to check and compare the signals. e.g. [rtl_433](https://github.com/merbanan/rtl_433) for RF, [Tasmota](https://tasmota.github.io/docs/Tasmota-IR/) or a [Broadlink RM4 Pro](https://www.ibroadlink.com/productinfo/762672.html) for both IR and RF.
 - most RF modules only supports the 433MHz frequency with ASK/OOK modulation. Check if your `.sub` file or source signal is compatible.
 - check the [serial log](https://github.com/pr3y/Bruce/wiki/Serial) for errors, some signals may [fail to decode](https://github.com/pr3y/Bruce/issues/216).
 - even if the signal decodes properly, some devices may use [rolling codes](https://en.m.wikipedia.org/wiki/Rolling_code) or other security mechanism to prevent replay attacks.


# Feature X is missing in my device?

Check the [table here](https://github.com/pr3y/Bruce#specific-functions-per-device-the-ones-not-mentioned-here-are-available-to-all).

e.g. BadUSB is only available on ESP32-S3-based devices.


# Port to other boards?

For unsupported boards you have to manually add a new [configuration environment](https://docs.platformio.org/en/latest/projectconf/sections/env/index.html) in the [platformio.ini](https://github.com/pr3y/Bruce/blob/main/platformio.ini), and define the pins for the modules to be connected, buttons and LCD.
Then, [compile the firmware for your new env](https://github.com/pr3y/Bruce/wiki/Building-from-source). Depending on the board more code changes may be needed.

For boards that do not have a display and buttons, an [headless mode was added](https://github.com/pr3y/Bruce/issues/107). Headless boards can be controlled only via the [WebUI](https://github.com/pr3y/Bruce/wiki/Others#webui) and [serial commands](https://github.com/pr3y/Bruce/wiki/Serial), and provide a subset of all the Bruce features.

A sample env for the [esp32-s3-devkitc-1 board](https://docs.espressif.com/projects/esp-idf/en/stable/esp32s3/hw-reference/esp32s3/user-guide-devkitc-1.html) is [defined here](https://github.com/pr3y/Bruce/blob/3813139ae0fc220180e7d443d4d6caea3e689224/platformio.ini#L845), it should work with any headless ESP32-S3 boards.


# What kind of files i need to put on the SD card?

There is some file examples of what you can do [in here](https://github.com/pr3y/Bruce/tree/main/sd_files), including [evil portal templates](https://github.com/pr3y/Bruce/tree/main/sd_files/portals), [nfcs](https://github.com/pr3y/Bruce/tree/main/sd_files/nfc) and [infrared](https://github.com/pr3y/Bruce/tree/main/sd_files/infrared)

# How do i customize Bruce?

You can choose a startup image other than Bruce's default by adding your image as 'boot.jpg' or 'boot.gif' on the root of the filesystems, you can also choose a startup sound if you have a file named 'boot.wav' for it.
Also its possible to render images on the Bruce itself via the LittleFS or SD Card manager.

# Themes
Now its possible to have other themes for the menu functionalities!

To use it, create a JSON file named `Theme.json` with the following structure:
```json
{
  "priColor": "ffff",
  "secColor": "ffff",
  "bgColor": "0000",
  "border": 0,
  "label": 1,
  "wifi": "wifi.png",
  "ble": "ble.png",
  "rf": "rf.png",
  "rfid": "rfid.png",
  "ir": "ir.png",
  "fm": "fm.png",
  "files": "files.png",
  "gps": "gps.png",
  "nrf": "nrf.png",
  "interpreter": "interpreter.png",
  "others": "others.png",
  "clock": "clock.png",
  "connect": "connect.png",
  "config": "config.png"
}
```

And you will also need all of those pngs on the root of the filesystem (SD or LittleFS) for you device with a compatible resolution for it to work.