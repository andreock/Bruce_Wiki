Play on `76-108 MHz` frequencies with a Si4713 module.

Feature added in https://github.com/pr3y/Bruce/pull/195

## :radio: Supported Modules
It needs to a Si4713. Those modules are supported for now:

1. [Adafruit Si4713](https://www.adafruit.com/product/1958)
2. [CJMCU-4713](https://fr.aliexpress.com/w/wholesale-cjmcu%2525252d4713.html?spm=a2g0o.productlist.search.0)

## Wiring

### Schema

![Grove](https://github.com/user-attachments/assets/93bd2591-13c5-4351-bbb3-8ddd94334875)  

![Si4713-1](https://github.com/user-attachments/assets/8e1a5052-3ba9-4b1e-8686-26a1dd2948c7)

### Pins

| Si4713    | M5StickC    |
| --------- | ----------- |
| RST       | G0          |
| SCL       | Grove G32   |
| SDA       | Grove G33   |
| GND       | Grove G     |
| VIN       | Grove 5V    |

## Features

## :play_or_pause_button: Broadcast standard
Broadcast sound from the Si4713 to the selected frequency.  
To be easier to choose, you need to select first the tens: `80`, `90` or `100 MHz`.  
Then you will choose the unit: `81`, `82`, `83`, `84 MHz` etc. and finally the radio frequency: `81.1`, `81.2`, `81.3 MHz` etc.

When broadcast is started, you can leave FM radio menu and run something else. FM broadcast will run in the background.

Auto mode available.

### :no_entry_sign: Broadcast rerserved
**Warning**: this could be illegal depending on your country. Educationnal purpose only.  

Work the same way as broadcast standard but on reserved frequencies, which are 76 - 87.5 MHz.

Auto mode available.

### :stop_button: Broadcast stop
Stop broadcasting.

### :ocean: FM Spectrum
*Work in progress*.  

Display noise spectrum on a given frequency.

Auto mode available.

### :car: Hijack TA
**Warning**: this could be illegal depending on your country. Educationnal purpose only.  

*Work in progress*.

Hijack a traffic announcement radio station to automatically start and set frequency of the cars around the transmitter.
Broadcast is working and TA flag is set, but auto start and switch of car radios does not work for now.

Radio frequency is set to info traffic station which is `107.7 MHz`.

### :bookmark_tabs: Config
*Work in progress*.

### :factory: Auto mode
In this mode, the Si4713 will listen for all frequency and select the one with minimum noise level, which represents a free radio station.