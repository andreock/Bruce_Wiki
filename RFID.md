## Supported modules

- **M5Stack [RFID2](https://docs.m5stack.com/en/unit/rfid2) module** 
- **RDM6300 RFID 125kHz module** ![Connection Schema](https://private-user-images.githubusercontent.com/2038003/357653419-b89f0c91-aa65-4624-8083-c68911c8b29c.jpg?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MjM2MDEyNDgsIm5iZiI6MTcyMzYwMDk0OCwicGF0aCI6Ii8yMDM4MDAzLzM1NzY1MzQxOS1iODlmMGM5MS1hYTY1LTQ2MjQtODA4My1jNjg5MTFjOGIyOWMuanBnP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI0MDgxNCUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNDA4MTRUMDIwMjI4WiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9YzQ5ZTU4MjFjNTYzMDFhZDMxZDJlOGEzODI2NDQ4Yjc3NmFjZmRhZThmYTBhMjc2NmY4MWU4ZjBjOWI3NzkxZSZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QmYWN0b3JfaWQ9MCZrZXlfaWQ9MCZyZXBvX2lkPTAifQ.Q51rRuzFvNjJGba4wKN5dSIagPouc4DhuLdrO-lXzSo)


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
