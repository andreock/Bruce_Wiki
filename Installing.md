# How to install

## For m5stack devices
The easiest way to install Bruce is if you already use M5Launcher to manage your m5stack device, you can install it with OTA

Or you can burn it directly from the [m5burner tool](https://docs.m5stack.com/en/download), just search for 'Bruce' (My official builds will be uploaded by "owner" and have photos.) on the device category you want to and click on burn

Alternatively you can also download the latest binary from releases and flash locally using esptool.py
```sh
esptool.py --port /dev/ttyACM0 write_flash 0x00000 Bruce_device_version.bin
```
or use a web flasher like https://web.esphome.io/
