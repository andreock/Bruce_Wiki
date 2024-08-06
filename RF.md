## Supported modules

- m5stack [RF433R](https://docs.m5stack.com/en/unit/rf433_r) and [RF433T](https://docs.m5stack.com/en/unit/rf433_t) modules

## Unofficial

- [FS1000A transmitter + XY-MK-5V receiver](https://components101.com/modules/433-mhz-rf-transmitter-module)

default pins: `Tx=GROVE_SDA`, `Rx=GROVE_SCL` 

**NOTE: FS1000A/XY-MK-5V have poor ranges**, check [a comparison with other single-pinned modules here](http://x311.blogspot.com/2017/10/comparison-of-cheap-rf-modules-with-ask.html)

## Unsupported modules

- CC1101 (testing with exti/o2 from m5stack)
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
