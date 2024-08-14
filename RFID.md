It is now possible to use the M5Stack RFID2 (WS1850S) to read and write Mifare Classic cards and tags. From what we investigated, this device does not allow emulation, so we recommend that you use an adhesive NFC tag on your Cardputer.
New functions involving NFC will be developed in the coming seasons.

To use, simply access the NFC / RFID menu, approach the card to which it will be read, press "ENTER" and approach the card to which it will be written. To exit, press "ESC".
Languages ​​in English and Brazilian Portuguese and some error messages were inserted.

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
