Bruce also accept command inputs via serial after https://github.com/pr3y/Bruce/pull/84, here are some Serial input commands that Bruce can interact with:
```
ir, rf, music_player, say, led, power, clock
```

# Sending serial commands

- via the [Arduino IDE Serial Monitor](https://docs.arduino.cc/software/ide-v2/tutorials/ide-v2-serial-monitor/), Putty, or any other serial terminal app
- via a bash script: `echo "say My name is Bruce" | busybox microcom -s 115200 /dev/ttyACM0  -t 1000`
- via a [python script](https://github.com/wh00hw/pyFlipper)
- from a smartphone using [SerialManager](https://github.com/delletenebre/SerialManager2)

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

turn off my lg tv via a decoded NEC code
```
ir tx NEC 04000000 08000000
```

turn off my LG AC via a RAW IR file (already stored on the FS):
```
ir tx_from_file AC_LG_SX122CL_off.ir
```

turn on a powerplug from decoded Sub file (already stored on the FS):
```
subghz tx_from_file plug1_on.sub
````

execute a badusb script (already stored on the FS):
```
badusb tx_from_file HelloWorld.txt
```





