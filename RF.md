# Supported Modules

## Official Modules

- **[M5Stack RF433R](https://docs.m5stack.com/en/unit/rf433_r)** and **[RF433T](https://docs.m5stack.com/en/unit/rf433_t)**
  - **Frequency**: Fixed at 433MHz
  - **Modulation**: Only ASK/OOK
  - **Connection**: Easier to connect

- **[CC1101 SPI Module](https://github.com/pr3y/Bruce/wiki/CC1101)**
  - **Frequency Range**: Supports multiple frequencies and modulations
  - **Connection**: More complicated, can be tested with exti/o2 from M5Stack

## Unofficial Modules

- **[FS1000A Transmitter + XY-MK-5V Receiver](https://components101.com/modules/433-mhz-rf-transmitter-module)**
  - **Frequency**: Fixed (usually 433MHz)
  - **Modulation**: Only ASK/OOK
  - **Note**: Also sold under various names

- **Other Single-Pinned Modules**
  - [Comparison of Cheap RF Modules](http://x311.blogspot.com/2017/10/comparison-of-cheap-rf-modules-with-ask.html)

![RF-Pins](https://github.com/user-attachments/assets/03e7290c-5219-4b80-b146-89cd2a814204)

> **Note**: Some modules may have poor range; modifying the antenna can improve performance.

**Default Pins**: 
- `Tx = GROVE_SDA`
- `Rx = GROVE_SCL`

---

# Unsupported/Not Working

- HC-11
- HC-12
- LoRa modules

---

# Features

- [x] Scan/Copy
- [x] Replay
- [x] Custom SubGhz (limited compatibility)
- [x] Spectrum Analysis
- [x] Jammer Full (New) - @incursiohack
- [x] Jammer Intermittent (New) - @incursiohack

---

# Replay Payloads Like Flipper!

Bruce can now send raw formats similar to those supported in [this repository](https://github.com/Zero-Sploit/FlipperZero-Subghz-DB/tree/main/subghz).

## Methods to Transmit `.sub` Files:

1. Via the **Custom SubGhz** app in the **RF** menu.
2. Via the **SDCard/LittleFS** file manager in the **Others** menu.
3. Via the **WebUI** by clicking the [antenna-like button next to the file](https://github.com/pr3y/Bruce/pull/124).
4. Via a [serial command](https://github.com/pr3y/Bruce/wiki/Serial), such as: