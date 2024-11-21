
## SD Card Mngr
Create Folders or Rename, Copy (to SPIFFS also) and Delete files.

## LittleFS Mngr
Delete, Copy, Rename or Read files from LittleFS.

## WebUI
Make you device as an AP or connect to a network to use the WebUI, with this you can manage your files on the SD card and also SPIFFS
Before setting up, you need to access http://bruce.local with the credentials on screen to have access to the manager.

## GPS Tracker
Use a GPS module to track the device. It creates a .gpx file that can be uploaded to online gpx viewers like [GPX Studio](https://gpx.studio/app) and [GPS Visualizer](https://www.gpsvisualizer.com/) or to any gpx viewer app to view the route on a map.

## BadUSB

Only DuckyScript payloads are supported!! for more info on creating your own DuckyScripts [read here](https://docs.hak5.org/hak5-usb-rubber-ducky/ducky-script-basics/hello-world)

To choose a payload for the BadUSB on Cardputer instead of getting rickrolled, you need to create a file on the SD card root directory ending with ".txt".
You can then select which payload that will be sent when the Cardputer is connected via USB cable.

Other methods to run badusb scripts:

1. via the SDCard/LittleFS file manager in the "Others" menu (select a `.txt` file)
2. remotely via the WebUI, click on the [antenna-like button next to the file](https://github.com/pr3y/Bruce/pull/124)
3. via a [serial cmd](https://github.com/pr3y/Bruce/wiki/Serial) like `badusb run_from_file HelloWorld.txt`

### Using Bad USB on StickCs and Core/Core2 devices
You will need to use a CH9329 module such as [this ](https://pt.aliexpress.com/item/1005006680094576.html) or [this ](https://pt.aliexpress.com/item/1005007031564072.html) to run the Bad USB in your device, wiring it into the Grove connector like this:

![CH3929](https://github.com/user-attachments/assets/1af21925-728e-4086-aa8d-f29a932fb3a1)


## Led control
Control ESP32 S3 Stamp RGB LED, with the options purple, white, red, green and blue to extra style, also led flash blinks the LED.

## Openhaystack
This is a little more complex to setup but basically you can use [this repository](https://github.com/MatthewKuKanich/FindMyFlipper) to generate a AirTag public key encoded in base64.
Then to work for Bruce, you should get your Public key decoded with base64 and save it on a file on the SD root called "pub.key".
To create pub.key file you should run this in bash:
```sh
base64 -d <<< "your_base64_public_key"|tee pub.key
```

## Interpreter
Head over to the [Interpreter Section](https://github.com/pr3y/Bruce/wiki/Interpreter).