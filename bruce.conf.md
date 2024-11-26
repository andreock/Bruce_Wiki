If there is no `bruce.conf` file on the SD card, Bruce will create this simple json file:

```json
{
  "priColor": "a80f",
  "secColor": "880f",
  "bgColor": "0",
  "rot": 1,
  "dimmerSet": 10,
  "bright": 75,
  "tmz": -3,
  "soundEnabled": 1,
  "wifiAtStartup": 0,
  "webUI": {
    "user": "admin",
    "pwd": "bruce"
  },
  "wifiAp": {
    "ssid": "BruceNet",
    "pwd": "brucenet"
  },
  "wifi": {
    "Net1": "pwd1",
    "Net2": "pwd2"
  },
  "irTx": 2,
  "irRx": 1,
  "rfTx": 2,
  "rfRx": 1,
  "rfModule": 0,
  "rfFreq": 433.9200134,
  "rfFxdFreq": 1,
  "rfScanRange": 3,
  "rfidModule": 0,
  "wigleBasicToken": "",
  "devMode": 0
}
```

Which will be used to persist the information between boots and even to M5Launcher when you finish running other applications that sometimes reuse EEPROM.
Also there is now an option to set a default wifi to connect for default.

TODO: Don't store pwd in cleartext :P
