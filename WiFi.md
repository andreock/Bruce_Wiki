## WiFi Atks

### Beacon Spam

### Target Atk
Scans for a WiFi AP to either get more information of it (MAC and channel), Send Deauth frames, Clone AP name and make a Evil Portal or Deauth + Clone.

## TelNet
Connect to TelNet servers and execute remote commands.

## SSH
Connect to SSH servers and execute remote commands.

## RAW Sniffer
Saves .pcap to SD card with raw monitoring info everytime every 10 seconds.

## DPWO-ESP32
Searches for default credentials for some router operators [more info here](https://github.com/caioluders/DPWO)

## Evil Portal
In EVIL Portal mode, BRUCE reads the keyboard input for the SSID and activates a open WiFi, with DNS, DHCP and Web servers activated. 
* EVIL Portal serves a fake login page that claims to provide internet access if you log in.
* This is a social engineering attack, and will log the username and passwords entered on the page. 
* You can type the ssid before and change the current SSID by connecting to the portal from your own device and browsing to http://172.0.0.1/creds or http://172.0.0.1/ssid
* If your device has an SD Card reader with a FAT filesystem formatted card inserted, the usernames and passwords will be logged to Bruce_creds.csv on the SD Card for you to peruse later. 
* SD Card support is only enabled by default on the M5Stack Cardputer platform. It can be enabled on M5Stick devices but an SD Card reader must be built and attached to the front panel pin header.
New features, SPIFFS and SDCard
* For examples of portals you can check https://github.com/pr3y/Bruce/tree/main/sd_files

## Scan Hosts
Does a ping sweep on current network based on the mask (equivalent to nmap -sn flag), after that it will list every host online, then you can select some host to have a TCP port scan on selected ports (20, 21, 22, 23, 25, 80, 137, 139, 443, 3389, 8080, 8443, 9090), as seen in "ports" variable on scan_hosts.cpp 

## Wireguard Tunneling
To be able to connect to a wireguard tunnel with your cardputer easily, you need to have your .conf file and place on the SD card root directory called "wg.conf"
If you don't know how to generate a .conf file for wireguard [read here](https://www.wireguard.com/quickstart/) 