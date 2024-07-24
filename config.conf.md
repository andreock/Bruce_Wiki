If there is no `config.conf` file on the SD card, Bruce will create this simple json file:
```json
[
  {
    "rot": 1,
    "dimmerSet": 10,
    "bright": 75,
    "wui_usr": "admin",
    "wui_pwd": "bruce",
    "Bruce_FGCOLOR": 992,
    "IrTx": 44,
    "IrRx": 1,
    "RfTx": 2,
    "RfRx": 1,
    "tmz": 3,
    "wifi": [
      {
        "ssid": "myNetSSID",
        "pwd": "myNetPassword"
      }
    ]
  }
]
```

Which will be used to persist the information between boots and even to M5Launcher when you finish running other applications that sometimes reuse EEPROM.
Also there is now a option to set a default wifi to connect for default.

TODO: Dont store pwd in cleartext :P
