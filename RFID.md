## RFID and NFC

**RFID** is a technology that uses electromagnetic fields to automatically identify and track tags attached to objects. These tags contain electronically stored information that can be read by an RFID reader. RFID is widely used in areas like inventory management, access control, and transportation systems.

**NFC**, on the other hand, is a subset of RFID technology that operates within a shorter range, typically within a few centimeters. NFC allows devices to establish communication by bringing them close together. It is commonly used for contactless payments, data sharing between devices, and smart access systems.


## Difference between RFID tags that can be written and cloned

RFID tags that can be **written** to allow users to modify the data stored on the tag, enabling dynamic information updates. However, these tags do not support writing to **block 0**, which often contains manufacturer data or unique identifiers.

Tags that can be **cloned** are a security concern. Cloning an RFID tag involves making a duplicate copy of the tag's information, which can be used maliciously for unauthorized access or fraudulent activities. To clone a tag, you typically need to write to **block 0**, which requires a special type of tag that supports this functionality.

## Common types of tags for RFID and NFC

- **MIFARE Classic 1k/4k**: A widely used RFID protocol that operates at 13.56MHz frequency and offers 1KB or 4KB of memory storage. It is commonly used in access control systems, transportation, and loyalty programs. You can find clonable version of those tags [here](https://pt.aliexpress.com/item/1005006787338686.html).
- **NTAG Series**: NTAG tags, such as NTAG213 and NTAG215, are popular NFC tag types operating at 13.56MHz. They are known for their compatibility with a wide range of NFC-enabled devices and applications. Those tags support NDEF records that can be interpreted by smartphones.
- **EM4100 and T5557**: RFID protocols operating at 125kHz frequency, commonly used for low-frequency access control systems, identification badges, key fobs, asset tracking, and other applications requiring proximity-based identification.


![RFID2 moudule](./media/nfc.gif)

## Supported modules

- RFID 13.56MHz
  - **M5Stack [RFID2](https://docs.m5stack.com/en/unit/rfid2) module** 
  - **MFRC-522** - with the I2C module from m5stack
- RFID 125kHz
  - **RDM6300** ([Connection Schema](https://github.com/pr3y/Bruce/pull/182#issuecomment-2287692412))

## Unsupported modules

- **PN532** - WIP

## Features
### RFID 13.56MHz
- [x] Read
- [x] Write
- [x] Clone
- [x] Write NDEF Records (NFC tags only)
- [x] Erase
- [x] Save file
- [x] Load file
- [ ] Emulate

### RFID 125kHz
- [x] Read
- [x] Save file
