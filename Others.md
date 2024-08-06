
## SD Card Mngr
Create Folders or Rename, Copy (to SPIFFS also) and Delete files.

## SPIFFS Mngr
Delete, Copy, Rename or Read files from SPIFFS.

## WebUI
Make you device as an AP or connect to a network to use the WebUI, with this you can manage your files on the SD card and also SPIFFS
Before setting up, you need to access http://bruce.local with the credentials on screen to have access to the manager.

## BadUSB
Only DuckyScript payloads are supported!! for more info on creating your own DuckyScripts [read here](https://docs.hak5.org/hak5-usb-rubber-ducky/ducky-script-basics/hello-world)

To choose a payload for the BadUSB on Cardputer instead of getting rickrolled, you need to create a file on the SD card root directory ending with ".txt".
You can then select which payload that will be sent when the Cardputer is connected via USB cable.
New features, SPIFFS and SDCard

## Led control
Control ESP32 S3 Stamp RGB LED, with the options purple, white, red, green and blue to extra style, also led flash blinks the LED.

## Openhaystack
This is a little more complex to setup but basically you can use [this repository](https://github.com/MatthewKuKanich/FindMyFlipper) to generate a AirTag public key encoded in base64.
Then to work for Bruce, you should get your Public key decoded with base64 and save it on a file on the SD root called "pub.key".
To create pub.key file you should run this in bash:
```sh
base64 -d <<< "your_base64_public_key"|tee pub.key
```