
# How to transfer files to/from the SD/LittleFS memory?

Use the [WebUI](https://github.com/pr3y/Bruce/wiki/Others#webui)


# Default passwords?

For AP mode wifi network the password is `brucenet`.

For the WebUI, username=`admin`, password=`bruce`


# IR/RF transmitter/receiver are not working

 - if using unofficially supported modules, double check the wiring is correct
 - try putting the transmitter and receiver closer, many cheap modules have poor ranges.
 - check the [serial log](https://github.com/pr3y/Bruce/wiki/Serial) for errors

# Port to non-M5Stack boards?

Not officially supported.

For boards that do not have screen and buttons, an [headless mode was added](https://github.com/pr3y/Bruce/issues/107).
For this to work, you have to manually add a new target in the [platformio.ini](https://github.com/pr3y/Bruce/blob/main/platformio.ini), and then define the pins and features for the modules you have connected.
Then, [compile the firmware for your new target](https://github.com/pr3y/Bruce/wiki/Building-from-source) and hope it works fine!