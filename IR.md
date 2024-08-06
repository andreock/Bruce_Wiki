## Supported modules

- builtin IR emitter found in most M5Stack boards (poor angular range)
- [M5Stack Mini Infrared Emitter & Receiver Unit](https://shop.m5stack.com/products/ir-unit)

### Unofficial

- [Elecrow Arduino Infrared Remote Control IOT Smart IR Module](https://www.elecrow.com/arduino-infrared-remote-control-iot-smart-ir-module.html)
- [LOLIN D1 IR Shield](https://www.wemos.cc/en/latest/d1_mini_shield/ir.html)
- [KY-005](https://arduinomodules.info/ky-005-infrared-transmitter-sensor-module/) and [KY-022](https://arduinomodules.info/ky-022-infrared-receiver-module/) IR Transmiter/Receiver (also sold with other names)
- [DIY board](https://tasmota.github.io/docs/IR-Remote/#related-projects)

default pinouts: `Tx=GROVE_SDA, Rx=GROVE_SCL`

NOTE: KY-005 and KY-022 may need modding to get a good range ([source1],(https://www.reddit.com/r/AskElectronics/comments/183mhh6/increase_voltage_power_for_ir_led_powered_by_33v/)
 [source2](https://circuitdigest.com/forums/internet-things/how-interface-hx-53-ir-transmitter-infrared-sensor-module-esp32))

### Unsupported modules

 - YT-IRTM transmitter/receiver (serial connection, NEC protocol only)

## Features:

 - [x] TV-B-Gone: Spams infrared for turning off screens.
 - [x] Custom IR: Send custom IR codes from a file in LittleFS and SDCard.
 - [x] IR read

For examples of IR files, you can check https://github.com/pr3y/Bruce/tree/main/sd_files



