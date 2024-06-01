## VS Code
You can open the project folder on Visual Studio Code with PlatformIO extension and click on "PlatformIO: Build" on the bottom.
After compiling the project, you need to merge the bootloader, partitions and the actual firmware on a single one, for that you can run the shell scripts "build.sh" or "build.bat", which will use esptool.py to output the binaries.
You also need to run the "deauth_setup.sh" to be able to compile:
```sh
git clone https://github.com/pr3y/Bruce.git
cd Bruce
./deauth_setup.sh
<compile the project on VS Code using PlatformIO>
./build.sh
```
With this you will have 3 .bin files on the project folder, with they being the build for M5Cardputer, M5StickC Plus 1.1, M5StickC Plus 2. 

## Github
You can also use the Github workflow to build the binaries for you with Actions, the last releases are also available there on the Artefacts, but you can also fork the project and make the changes you want to this, then build on your own Actions also.