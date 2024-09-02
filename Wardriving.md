Wardriving in Bruce is possible [after this PR](https://github.com/pr3y/Bruce/pull/100), so if you have a GPS module from M5stack you can start wardriving and check for the .csv that can be uploaded to Wigle also!

WiGLE (Wireless Geographic Logging Engine) is an online platform that collects and maps Wi-Fi and cellular network data globally. Users can upload network data they encounter, view coverage maps, and search for specific networks.

## How to Use WiGLE Daily

1 - Network Mapping: Find and map Wi-Fi networks in specific areas, useful for wardriving or security studies.

2 - Coverage Analysis: Check Wi-Fi coverage in public or commercial locations.

3 - Security: Identify insecure or misconfigured networks.

4 - Research: Used by researchers to analyze network patterns and security.


## How to begin

1 - Create an Account: [WiGLE.net](https://wigle.net/)

2 - Join the Group "Bruce": Search for Bruce and select "Join". [Group Stats](https://wigle.net/stats#groupstats)

## How to upload

### BRUCE - [PR 232](https://github.com/pr3y/Bruce/pull/232):
1 - Go to the website [Wiggle Account](https://wigle.net/account), select the API Token option and copy the entire token from 
"Encoded for use". (Be careful, this token should not be shared with anyone)

2 - Insert the token copied from your Wigle account into the "wigleBasicToken" line of the "bruce.conf" file at the root of your SD card.

3 - Select menu Others > SD Card > BruceWardriving > timestamp_wardriving.csv

4 - Select the "Wigle Upload" option.

5 - Select your WiFi network.

6 - Wait for the file to be sent. A loading bar should appear with information at the end saying that the file has been uploaded.

7 - Shark, you have already collaborated, whenever you find new wifi networks in wardriving, just upload the file.

### WEBSITE WIGLE:
1 - Upload File: Upload "file_name_wardriving.csv" in "Uploads" and wait, WiGLE.net may take a few hours to process the file queue. [Uploads](https://wigle.net/uploads)

2 - Shark, you have already collaborated, whenever you find new wifi networks in wardriving, just upload the file.


## Tip
On the "Statistics: Manufacturer > SSID/Manufacturer" page ([SSID Stats](https://wigle.net/stats#ssidstats)), you can find a list of the most used Wi-Fi network names globally, which can inspire ideas for Bruce's Evil Portal ([Evil Portal](https://github.com/pr3y/Bruce/wiki/WiFi#evil-portal)).

[@IncursioHack](https://github.com/IncursioHack)
