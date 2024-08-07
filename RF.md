## Supported modules

- M5Stack [RF433R](https://docs.m5stack.com/en/unit/rf433_r) and [RF433T](https://docs.m5stack.com/en/unit/rf433_t) modules
- CC1101 (WIP, also testing with exti/o2 from m5stack) https://github.com/pr3y/Bruce/pull/135

## Unofficial

- [FS1000A transmitter + XY-MK-5V receiver](https://components101.com/modules/433-mhz-rf-transmitter-module) (also sold with other names)

default pins: `Tx=GROVE_SDA`, `Rx=GROVE_SCL` 

**NOTE: FS1000A/XY-MK-5V have poor ranges**, check [a comparison with other single-pinned modules here](http://x311.blogspot.com/2017/10/comparison-of-cheap-rf-modules-with-ask.html)

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

1. via the "Custom SubGhz" app in the "RF" menu
2. via the SDCard/LittleFS file manager in the "Others" menu
3. via the WebUI, click on the [antenna-like button next to the file](https://github.com/pr3y/Bruce/pull/124)
4. via a [serial cmd](https://github.com/pr3y/Bruce/wiki/Serial) like `subghz tx_from_file plug1_on.sub`
