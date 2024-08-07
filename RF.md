## Supported modules

- **M5Stack [RF433R](https://docs.m5stack.com/en/unit/rf433_r) and [RF433T](https://docs.m5stack.com/en/unit/rf433_t)** modules -> fixed frequency of 433MHz, only ASK/OOK modulation
- **CC1101 SPI module** ([via GPIO pins](https://github.com/pr3y/Bruce/pull/135), also testing with exti/o2 from m5stack) -> lot of frequencies and modulations supported

### CC1101 connection pinout

(Still WIP, this page will be updated when ready for prime time)


## Unofficial

- **[FS1000A transmitter + XY-MK-5V receiver](https://components101.com/modules/433-mhz-rf-transmitter-module)** (also sold with other names)  -> fixed frequency (usually 433MHz), only ASK/OOK modulation
- other single-pinned modules ([comparison](http://x311.blogspot.com/2017/10/comparison-of-cheap-rf-modules-with-ask.html))

**NOTE: some have poor ranges**, may need to mod the antenna to get a better range.

default pins: `Tx=GROVE_SDA`, `Rx=GROVE_SCL` 


## Unsupported modules

- HC-11 and HC-12


## Features

- [x] Scan/Copy
- [ ] Replay
- [x] Custom SubGhz (limited compatibility)
- [x] Spectrum
- [x] Jammer Full (New) - @incursiohack
- [x] Jammer Intermittent (New) - @incursiohack

## Replay payloads like flipper!

Bruce now can send raw formats, like the ones supported in [this repository](https://github.com/Zero-Sploit/FlipperZero-Subghz-DB/tree/main/subghz)

methods to transmit `.sub` files:

 - via the "Custom SubGhz" app in the "RF" menu
 - via the SDCard/LittleFS file manager in the "Others" menu
 - via the WebUI, click on the [antenna-like button next to the file](https://github.com/pr3y/Bruce/pull/124)
 - via a [serial cmd](https://github.com/pr3y/Bruce/wiki/Serial) like `subghz tx_from_file plug1_on.sub`


