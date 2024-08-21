Bruce also accept command inputs via serial after https://github.com/pr3y/Bruce/pull/84, here are some Serial input commands that Bruce can interact with:
```
ir, subghz, music_player, say, led, power, clock, tone, gpio, i2c, storage, settings, factory_reset
```

Most of these commands are compatible with the [Flipper Zero CLI](https://docs.flipper.net/development/cli#0Z9fs).


# Sending serial commands

- via the [Arduino IDE Serial Monitor](https://docs.arduino.cc/software/ide-v2/tutorials/ide-v2-serial-monitor/), [Putty](https://pbxbook.com/voip/sputty.html), or any other serial terminal app
- via a bash script: `echo "say My name is Bruce" | busybox microcom -s 115200 /dev/ttyACM0  -t 1000`
- via a [python script](https://github.com/wh00hw/pyFlipper)
- from a smartphone using [SerialManager](https://github.com/delletenebre/SerialManager2)
- via the [WebUI](https://github.com/pr3y/Bruce/wiki/Others#webui) ["SerialCmd" button](https://github.com/pr3y/Bruce/pull/134)
- after starting the WebUI, with `curl -XPOST "http://bruce.local/cm" -d "cmnd=say My name is Bruce"`

# Examples

talk to Bruce with
```
say My name is Bruce
```

sleep
```
power sleep
```

play doom!
```
music_player doom:d=4,o=5,b=112:16e4,16e4,16e,16e4,16e4,16d,16e4,16e4,16c,16e4,16e4,16a#4,16e4,16e4,16b4,16c,16e4,16e4,16e,16e4,16e4,16d,16e4,16e4,16c,16e4,16e4,a#4,16p,16e4,16e4,16e,16e4,16e4,16d,16e4,16e4,16c,16e4,16e4,16a#4,16e4,16e4,16b4,16c,16e4,16e4,16e,16e4,16e4,16d,16e4,16e4,16c,16e4,16e4,a#4,16p,16a4,16a4,16a,16a4,16a4,16g,16a4,16a4,16f,16a4,16a4,16d#,16a4,16a4,16e,16f,16a4,16a4,16a,16a4,16a4,16g,16a4,16a4,16f,16a4,16a4,d#
```

turn off my LG TV via a decoded NEC code:
```
ir tx NEC 04000000 08000000
```

turn off my LG AC via a RAW IR file (already stored on the FS):
```
ir tx_from_file AC_LG_SX122CL_off.ir
```

turn on an smart power socket from a decoded Sub file (already stored on the FS):
```
subghz tx_from_file plug1_on.sub
````

send a custom rf command (format ` {3-byte hex_key} {frequency} {te} {count}`):
````
subghz tx 445533 433920000 174 10  # flipper format
````

execute a badusb script (already stored on the FS):
```
badusb tx_from_file HelloWorld.txt
```

set a pin in (digital) output mode (only on unused GPIO pins, using Arduino `pinMode()`):
````
gpio mode 2 0 
````

sets the a pin's value (only on unused GPIO pins, using Arduino `digitalWrite()`):
````
gpio set 2 0 
````

read a pin's value (only on unused GPIO pins, using Arduino `digitalRead()`):
````
gpio read 2
````

read a file content, and output on the console:
````
storage read BruceRF/bruce_0.sub
````

list files on the root (SD card if present, LittleFS otherwise):
````
storage list /
````

delete a file:
````
storage remove BruceRF/bruce_0.sub
````

scan connected I2C devieces:
````
i2c
````

View currently-active settings:
````
settings
````

Reset settings to the default:
````
factory_reset
````
