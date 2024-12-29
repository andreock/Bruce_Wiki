# VS Code
You can open the project folder on Visual Studio Code with PlatformIO extension and click on "PlatformIO: Build" on the bottom.
After compiling the project, you need to merge the bootloader, partitions and the actual firmware on a single one, for that you can run the PlatformIO Custom task named "build-firmware" to output the single combined binary.
With this you will have 5 .bin files on the project folder, with they being the build for M5Cardputer, M5StickC Plus 1.1, M5StickC Plus 2, M5core and M5Core2. 

## LINUX BUILD
Requirements
```sh
sudo apt update
sudo apt install python3-pip git
pip3 install platformio
export PATH=$PATH:~/.local/bin
source ~/.bashrc
echo 'export PATH=$PATH:~/.local/bin' >> ~/.bashrc
source ~/.bashrc
git clone https://github.com/pr3y/Bruce.git
cd Bruce
```
Fedora based just change to
```sh
sudo dnf update
sudo dnf install python3-pip git
```

Step by Step to build the project

```sh
pio run --target clean
pio run -e m5stack-cardputer
pio run -e m5stack-cplus2
pio run -e m5stack-cplus1_1 
# or pio run to all builds
# pio run
pio run -e m5stack-cardputer -t build-firmware
pio run -e m5stack-cplus2 -t build-firmware
pio run -e m5stack-cplus1_1 -t build-firmware
```

# Windows build
* Install [Git](https://git-scm.com/download/win)
* Install Python using the Microsoft Store
* Install VSCode
* Download the repository and extract it somewhere you want
* Within VSCode, `File>Open Folder...` and select the folder of the firmware
* If it doesn't prompt to install Platformio, click on "Extentions" (4 swares icon on the left) and install Platformio (and restart VsCode)
* In the Status bar (down on the screen) click where is written `Default (Bruce-main)`
* A little Menu will appear in the Search bar (up on screen), select your device "env"
* Now click in the :heavy_check_mark: Icon in the Status Bar (beside the cute little House), it will start building your project
* if you want to upload directly, you can do it clicking in the "->" arrow to upload to your device
* If you want to output a binary you can flash, use the "build-firmware" Custom task in the PlatformIO Extension Sidebar Menu named "project tasks"


# Github
You can also use the Github workflow to build the binaries for you with Actions, the last releases are also available there on the Artefacts, but you can also fork the project and make the changes you want to this, then build on your own Actions also.