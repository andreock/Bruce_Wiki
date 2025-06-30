# Ethernet

Bruce supports W5500 Ethernet SPI Card to perform some Layer 2 and Layer 3 attacks

## Scan Hosts

The scan hosts feature perform a ARP scanning of the network, furthermore it can scan all ports of a single host using the Host Info feature

## SSH Connect
Tries to connect into the Host using SSH.

## ARP Spoofing
- Sends fake ARP Resonses to the host and to the Gateway, provoking communication interruption. this is the fist step of a Man-In-The-Middle attack using the 2nd OSI layer vulnerability.

## ARP Poisoning
Sends fale ARP responses to all hosts and to the gateway with random MAC addresses. It can possibly cause CAOS in the network, as all devices won't find the gateway to communicate.

### Wiring

#### M5Stick

- INT_PIN=25
- SS_PIN=26
- MOSI_PIN=32
- SCK_PIN=0
- MISO_PIN=33

## Cardputer

This requires a [microSD sniffer](https://www.sparkfun.com/products/9419) (shared with the SD card) and some soldering skills.


| W5500 |  SD Sniffer  | Cardputer |
| ------ | ------------ | --------- |
|  GND    | GND | |
|  3,3V | Vcc | |
| GDO0   | | *Grove SDA (2)* |
| CSN    | | *Grove SCL (1)* |
|  SCK    | CLK | |
| Mosi   | CMD | |
| Miso   | DAT0 | |

#### CYD

Works with the [microSD sniffer](https://github.com/witnessmenow/ESP32-Cheap-Yellow-Display/blob/main/ADDONS.md#sd-card-sniffer):

- INT PIN = 22
- SS PIN = 27(CYD)
- SS PIN = 21(Phantom)

#### Lilygo T-deck/T-display-s3

Works with the [microSD sniffer](https://github.com/witnessmenow/ESP32-Cheap-Yellow-Display/blob/main/ADDONS.md#sd-card-sniffer):

- INT PIN = 44
- SS PIN = 43(in case of T-deck)
- SS PIN = 1(in case of T-display-s3)

These pins comes from Qwiic connector(RX and TX pin) from the side of the board

#### Lilygo T-display-ttgo

Works with the [microSD sniffer](https://github.com/witnessmenow/ESP32-Cheap-Yellow-Display/blob/main/ADDONS.md#sd-card-sniffer):

- INT PIN = 37
- SS PIN = 38

#### Lilygo T-embed-CC1101

Works with the [microSD sniffer](https://github.com/witnessmenow/ESP32-Cheap-Yellow-Display/blob/main/ADDONS.md#sd-card-sniffer):

- INT PIN = 43
- SS PIN = 44
