# WiFi Atks

## Beacon Spam

## Target Atk
Scans for a WiFi AP to either get more information of it (MAC and channel), Send Deauth frames, Clone AP name and make a Evil Portal or Deauth + Clone.

## Wardriving
Wardriving in Bruce is possible [after this PR](https://github.com/pr3y/Bruce/pull/100), so if you have a GPS module from M5stack you can start wardriving and check for the .csv that can be uploaded to Wigle also!

## TelNet
Connect to TelNet servers and execute remote commands.

## SSH
Connect to SSH servers and execute remote commands.

## RAW Sniffer
Saves .pcap to SD card with raw monitoring, you can also select for it to save only EAPOL/HandShakes and stop spamming deauth packets to detected beacons previously detected.

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

### **Setting AP Name from HTML**  

#### **Overview**  
The `EvilPortal` system now supports the ability to define an Access Point (AP) name directly within your HTML files. By including a specific tag in the first line of your HTML file, the system will automatically extract and set the AP name, streamlining the setup process.

#### **How It Works**  
1. Add the following tag in the **first line** of your HTML file:  
   ```html
   <!-- AP="YourCustomAPName" -->
   ```
   Replace `YourCustomAPName` with the desired name for your Access Point.  

2. When the HTML file is loaded, the system will:  
   - Parse the first line of the file.  
   - Detect the `AP="..."` tag.  
   - Extract the value and set it as the AP name.  

3. If the tag is not present it will ask you for AP name (as usual).

#### **Example HTML File**  
```html
<!-- AP="MyCoolNetwork" -->
<!DOCTYPE html>
<html>
<head>
    <title>EvilPortal</title>
</head>
<body>
    <h1>Welcome to EvilPortal!</h1>
</body>
</html>
```

- In this example, the AP name will automatically be set to **MyCoolNetwork**.

#### **Benefits**  
- **Dynamic Configuration**: Easily customize AP names without modifying code.  
- **Ease of Use**: Set up AP names directly in your HTML files for faster deployment.  

#### **Notes**  
- Ensure the `<!-- AP="..." -->` tag is in the **very first line** of the file.  
- The feature does not affect the functionality of other HTML content.

## Scan Hosts
Does a ARP scan on current network based on the mask (equivalent to arp -a), after that it will list every host online, then you can select some host to have a TCP port scan on selected ports (20, 21, 22, 23, 25, 80, 137, 139, 443, 3389, 8080, 8443, 9090), as seen in "ports" variable on scan_hosts.cpp and let you choose a target host attack such as:

## Host Info
Discover open ports (20, 21, 22, 23, 25, 80, 137, 139, 443, 3389, 8080, 8443, 9090) on the Host

### SSH Connect
Tries to connect into the Host using SSH.

### Station Deauth
Spams deauth frames targetted to this particular device

### ARP Spoofing
- Sends fake ARP Resonses to the host and to the Gateway, provoking communication interruption. this is the fist step of a Man-In-The-Middle attack using the 2nd OSI layer vulnerability.

### ARP Poisoning
Sends fale ARP responses to all hosts and to the gateway with random MAC addresses. It can possibly cause CAOS in the network, as all devices won't find the gateway to communicate.

## TCP Client
Allows the ESP32 to connect to a remote server as a client over TCP. You can configure the target server's IP address and port, enabling data transmission to and from the server.

## TCP Listener
Listen for incoming TCP connections on a specified port. It waits for client connections, allowing the device to act as a server and handle communication with connected clients.

## Wireguard Tunneling
To be able to connect to a wireguard tunnel with your cardputer easily, you need to have your .conf file and place on the SD card root directory called "wg.conf"
If you don't know how to generate a .conf file for wireguard [read here](https://www.wireguard.com/quickstart/) 

## Brucegotchi
This feature does a lot of things at the same time, such as:
- Pwngrid spam
- Deauth nearby WiFi networks in different channels
- Collect and save HandShakes (EAPOL)