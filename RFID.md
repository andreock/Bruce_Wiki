## Supported modules

- **M5Stack [RFID2](https://docs.m5stack.com/en/unit/rfid2) module** 
- **RDM6300 RFID 125kHz module** ([Connection Schema](https://github.com/pr3y/Bruce/pull/182#issuecomment-2287692412))


It is now possible to use the M5Stack RFID2 (WS1850S) to read and write Mifare Classic cards and tags. From what we investigated, this device does not allow emulation, so we recommend that you use an adhesive NFC tag on your Cardputer.
New functions involving NFC will be developed in the coming seasons.

To use, simply access the NFC / RFID menu, approach the card to which it will be read, press "ENTER" and approach the card to which it will be written. To exit, press "ESC".
Languages ​​in English and Brazilian Portuguese and some error messages were inserted.

![RFID2 moudule](./media/nfc.gif)

## Supported modules

- m5stack RFID2 module
- MFRC-522 with the I2C module from m5stack
- PN532(?)

## Features
- [x] Read and Write
- [ ] Replay ?
