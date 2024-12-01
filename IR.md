## Supported Modules  

- Built-in IR emitter found in most M5Stack boards  
- [M5Stack Mini Infrared Emitter & Receiver Unit](https://shop.m5stack.com/products/ir-unit) (easier to connect than other modules)  

### Unofficial  

- [KY-005](https://arduinomodules.info/ky-005-infrared-transmitter-sensor-module/) and [KY-022](https://arduinomodules.info/ky-022-infrared-receiver-module/) IR Transmitter/Receiver (also sold under other names).  
  **NOTE:** May require modifications for better range on 3.3V boards ([source 1](https://www.reddit.com/r/AskElectronics/comments/183mhh6/increase_voltage_power_for_ir_led_powered_by_33v/), [source 2](https://circuitdigest.com/forums/internet-things/how-interface-hx-53-ir-transmitter-infrared-sensor-module-esp32).  
- [Elecrow Arduino Infrared Remote Control IOT Smart IR Module](https://www.elecrow.com/arduino-infrared-remote-control-iot-smart-ir-module.html) (works fine at 3.3V, no modifications needed).  
- IR Hats for Raspberry Pi (designed for 3.3V, untested but expected to work).  
- [LOLIN D1 IR Shield](https://www.wemos.cc/en/latest/d1_mini_shield/ir.html) (requires soldering).  
- [DIY Board](https://tasmota.github.io/docs/IR-Remote/#related-projects).  

**Default Pinouts:**  
`Tx = (built-in LED), Rx = GROVE_SCL`  

**Wanted:** Range comparisons of different modules.  

---

### Unsupported/Not Working  

- YT-IRTM transmitter/receiver (serial connection, NEC protocol only).  
- [Flirc](https://flirc.tv/) and other unbranded IR receivers/blasters with USB/USB-C ports, like [this one](https://www.walmart.com/ip/Universal-Remote-Smartphone-IR-Controller-Adapter-USB-C-Infrared-Blaster-Control-for-Android-Phone-All-in-One-Air-Conditioner-TV-DVD-STB-Black/5426981611?selectedSellerId=101177603).  

---

## Features  

- [x] **TV-B-Gone:** Spams infrared signals to turn off screens.  
- [x] **Custom IR:** Send custom IR codes from files in LittleFS or an SD card.  
- [x] **IR Read:** Read and decode IR signals.  

---

## Replay Payloads Like Flipper!  

For example `.ir` files, visit: [Infrared Payloads](https://github.com/pr3y/Bruce/tree/main/sd_files/infrared).

### Methods to Transmit `.ir` Files  

1. **Via the "Custom IR" App:** Select commands individually through the "IR" menu.  
2. **Via SDCard/LittleFS File Manager:** Found under the "Others" menu (spams all commands).  
3. **Via the WebUI:** Click the [antenna button](https://github.com/pr3y/Bruce/pull/124) next to the file (spams all commands).  
4. **Via Serial Command:** Example: `ir tx_from_file AC_LG_SX122CL_off.ir`. For more details, see the [Serial Command Guide](https://github.com/pr3y/Bruce/wiki/Serial) (spams all commands).  
