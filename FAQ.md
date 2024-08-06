
# how to transfer files to/from the SD/LittleSD?

use the [WebUI](https://github.com/pr3y/Bruce/wiki/Others#webui)


# port to non-M5Stack boards?

Not officially supported.

For boards that do not have screen and buttons, an [headless mode was added](https://github.com/pr3y/Bruce/issues/107).
For this to work, you have to manually add a new target in the [platformio.ini](https://github.com/pr3y/Bruce/blob/main/platformio.ini), and then define the pins and features for the modules you have connected.
Then, [compile the firmware for your new target](https://github.com/pr3y/Bruce/wiki/Building-from-source).