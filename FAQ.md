
# How to transfer files to/from the SD/LittleFS memory?

Use the [WebUI](https://github.com/pr3y/Bruce/wiki/Others#webui)


# Default passwords?

For AP mode wifi network the password is `brucenet`.

For the WebUI, username=`admin`, password=`bruce`


# IR/RF transmitter/receiver not working?

 - if using unofficially supported modules, double-check that the used pins are correct. These can be [changed in the Settings](https://www.youtube.com/watch?v=i4wRNeGQJfw).
 - check if the module is active and working during transmission:
   - for IR, you can [use a smartphone camera to check if the IR LED is blinking](https://www.youtube.com/watch?v=i4wRNeGQJfw).
   - use a multimeter or an oscilloscope to check activity on the data pin/LED/antenna.
   - use another device to check and compare the signals. e.g. [rtl_433](https://github.com/merbanan/rtl_433) for RF, [Tasmota](https://tasmota.github.io/docs/Tasmota-IR/) for both IR and RF.
 - try putting the transmitter and receiver closer (<10cm), many cheap modules have poor ranges.
 - most RF modules only supports the 433MHz frequency with ASK/OOK modulation. Check if your `.sub` file or source signal is compatible.
 - check the [serial log](https://github.com/pr3y/Bruce/wiki/Serial) for errors.

# Port to non-M5Stack boards?

Not officially supported.

For boards that do not have screen and buttons, an [headless mode was added](https://github.com/pr3y/Bruce/issues/107).
For this to work, you have to manually add a new target in the [platformio.ini](https://github.com/pr3y/Bruce/blob/main/platformio.ini), and then define the pins and features for the modules you have connected.
Then, [compile the firmware for your new target](https://github.com/pr3y/Bruce/wiki/Building-from-source) and hope it works fine!