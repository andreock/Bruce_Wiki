# VS Code
You can open the project folder on Visual Studio Code with PlatformIO extension and click on "PlatformIO: Build" on the bottom.
After compiling the project, you need to merge the bootloader, partitions and the actual firmware on a single one, for that you can run the shell scripts "build.sh" or "build.bat", which will use esptool.py to output the binaries.
You also need to run the "deauth_setup" to be able to compile.
With this you will have 3 .bin files on the project folder, with they being the build for M5Cardputer, M5StickC Plus 1.1, M5StickC Plus 2. 

## LINUX BUILD
Requirements
```sh
sudo apt update
sudo apt install python3-pip git
pip3 install esptool --user
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

After running the first time, a compilation error will occur.
```sh
pio run --target clean
pio run -e m5stack-cardputer
pio run -e m5stack-cplus2
pio run -e m5stack-cplus1_1 
```

To bypass the error we need to run only once 
```sh
bash deauth_setup.sh
``` 

Step by Step to build the project

```sh
bash clean.sh
pio run --target clean
pio run -e m5stack-cardputer
pio run -e m5stack-cplus2
pio run -e m5stack-cplus1_1 
bash build.sh
```

# Github
You can also use the Github workflow to build the binaries for you with Actions, the last releases are also available there on the Artefacts, but you can also fork the project and make the changes you want to this, then build on your own Actions also.