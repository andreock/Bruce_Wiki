## Resume

1. [Prerequisites](#prerequisites)
2. [Bruce structure](#bruce-structure)
3. [Dependencies](#dependencies)
4. [Development](#development)
    1. [Add a new item in the main menu](#add-a-new-item-in-the-main-menu)
    2. [Draw a new icon](#draw-a-new-icon)
    3. [Add or modify menus](#add-or-modify-menus)
    5. [Add or modify sub-menus](#add-or-modify-sub-menus)
    6. [Module functions](#module-functions)

## Prerequisites

First you need to clone the repository and build Bruce from sources. You will find the documentation here:
1. [optional] but recommended: work from a [Python virtualenv](https://github.com/pyenv/pyenv-virtualenv)
2. [build your firmware](https://github.com/pr3y/Bruce/wiki/Building-from-source)
3. [install your build](https://github.com/pr3y/Bruce/wiki/Installing)

## Bruce structure

Main code in `src/core` and modules in `src/modules`.
In `module` repository, we have one folder for each category. Don't hesitate to ask in the Discord where to add the files for your module.
Here we will create a new directory and new files:
```
src/
|-- core/
|------ menu_items/
        |---- LoRaMenu.h
        |---- LoRaMenu.cpp
|-- modules/
|------ lora/
        |---- lora.h
        |---- lora.cpp
```

## Dependencies

If you need to install a new library, you have two choices:
1. use `pio` package manager
2. add your custom library in `lib/`

**Pio package manager**
If you want to install dôme librairies,  you can search or install them like:
```bash
pio pkg search mylib
pio pkg install -l mylib
```

**Warning**: do not commit the `platform.io` auto generated file. Instead add your lib in the adequate section of the file. Or ask on the Discord where to write it. 

**Custom library**
Simply put your lib in `lib/mylib'. Then you can import it with:
```C
#include "../lib/mylib/mylib.h"
```

## Development 

As an exemple, we will see how to add a LoRa module in Bruce. This is a 868 MHz RF module with dedicated protocol. But we are not interested in how LoRa works, it's just for the templating.

### Add a new item in the main menu

You can either add a feature in an existing menu, or create a new item in the main menu. We will first see how to add an item.

**Register an item**

We need to register our item by modifying 2 files:
* `src/core/menu_items/LoRaMenu.h`
* `src/core/menu_items/LoRaMenu.cpp`

In `LoRaMenu.h, we declare the menu object with the mandatory methods:
* `optionsMenu()` --> declare the menu options
* `draw()` --> draw the item in main menu
* `getName` --> return the name of the menu


In the end, it looks like this:
```C
#ifndef __LORA_MENU_H__
#define __LORA_MENU_H__

#include "MenuItemInterface.h"

class LORAMenu : public MenuItemInterface {
public:
    void optionsMenu(void);
    void draw(void);
    String getName(void);

private:
    String _name = "LoRa";
    void configMenu(void);
};

#endif
```

Now in `LoRaMenu.cpp` we will declare the methods we need. Their contents will be explained later in this tutorial.
```C
#include "LoRaMenu.h"
#include "core/display.h"
#include "modules/lora/lora.h"

void LoRaMenu::optionsMenu() {
    // We will see that later (see bellow)

    delay(200);
    loopOptions(options,false,true,"LoRa");
}

String LoRaMenu::getName() {
    return _name;
}

void LoRaMenu::draw() {
    // We will see that later (see bellow)
}
```

We're done for the register part. Now, we need to develop the content of the 2 methods previously declared: 
1. `LoRaMenu::draw()` --> the icon that will be draw on screen
4. `LoRaMenu::optionsMenu()` --> the declaration of the menu when the main item is selected

### Draw a new icon

![main-menu](https://github.com/user-attachments/assets/98669885-fa9c-49c8-968d-6690da07f17b)

**drawLoRa()**
With this function, you can draw your own icon. To be able to draw, you can use the following functions:
| Function | Description |
|:------------|:---------------|
| `tft.drawLine() `| Draw a simple line |
| `tft.drawRect()` | Draw a rectangle |
| `tft.drawRoundRect()` | Draw a rounded border rectangle |
| `tft.drawCentreString() `| Display a screen center on coordinates |
| `tft.drawCircle()` | Draw a circle |
| `tft.drawArc()` | Draw an arc |
| `tft.fillRect()` | Draw and fill a rectangle |
| `tft.fillRoundRect()` | Draw and fill a rounded border rectangle  |
| `tft.fillCircle()` | Draw and fill a circle |
| `tft.fillScreen()` | Fill the whole screen |

Here is an exemple of the definition in `src/core/menu_items/LoRaMenu.cpp`:
```C
void LoRaMenu::draw() {
  // Blank
  tft.fillRect(iconX,iconY,80,80,BGCOLOR);

  tft.drawArc(19+iconX,45+iconY,12,10,130,230,FGCOLOR,BGCOLOR);
  tft.drawArc(19+iconX,45+iconY,22,20,130,230,FGCOLOR,BGCOLOR);
  tft.drawArc(19+iconX,45+iconY,32,30,130,230,FGCOLOR,BGCOLOR);
  tft.drawCentreString("L o R a",40+iconX, 40+iconY, SMOOTH_FONT);
}
```

### Add or modify menus

![menu](https://github.com/user-attachments/assets/fcf04298-d988-400f-8ba9-97fde78307b9)

**LoRaMenu::optionsMenu()**

We need to declare the options, like we started in `src/core/menu_items/LoRaMenu.cpp`. For this we use the `loopOptions()` function. 
This function takes as an argument an `options` object. In parameter, the `*_run` are functions called when the option will be selected by the user. For now, those functions do not exist.
Here is an exemple:
```C
void LoRaMenu::optionsMenu() {
  options = {
    {"LoRa Gw",         [=]() { lora_gw_run(); }},
    {"Messenger",       [=]() { lora_msg_run(); }},
    {"Scan nets",       [=]() { lora_scan_run(); }},
    {"Main Menu",       [=]() { backToMenu(); }}
  };
  delay(200);
  loopOptions(options,false,true,"LoRa");
}
```

**Return to the main menu**
You can notice the `backToMenu()` call. It's only switching a global boolean: `returnToMenu`. This way you can implement a main menu return like this:
```C
if (!returnToMenu) {
  // Run you stuff
}

// Will return to main menu after you last call
```

### Add or modify sub-menus

![sub-menu](https://github.com/user-attachments/assets/576c614a-683f-4c61-b04c-4ac8abe1aaf0)

You may want to draw a sub-menu, for exemple if you want to scan the nework ids, the user selects the desired option, then a sub-menu appears with the found results. For this you can do the exact same thing as a simple menu, it will automatically detect you'are in a sub-menu. Moreover, you can dynamically generate your sub-menu options like this.

This is a module specific feature, so the declaration will be in `src/modules/lora/lora.h`:
```C
void lora_scan_run();
```

Here is an exemple of a dumb scan with dynamic options, in `src/modules/lora.cpp`:
```C
void lora_scan_run() {
  char number[1];
  
  // Display a banner while scanning runs in the background
  displayRedStripe("Scanning..", TFT_WHITE, FGCOLOR);
  delay(2000);

  options = { };
  for(int i=1; i<10; i++) {
    sprintf(number, "Scan %d", i);
    options.push_back({number,    [=]()  { /*do_things(i);*/ }});
  }
  options.push_back({"Main menu", [=]() { backToMenu(); }});

  delay(200);
  loopOptions(options);
  delay(200);
}
```

### Module functions

You can now start to code the main functions of your module. Here we already made a call for `lora_gw_run()` and `lora_msg_run()`. Start to declare them in `src/modules/lora/lora.h`:
```C
void lora_scan_run();
void lora_gw_run();
void lora_msg_run();
```

Then code the functions in `src/modules/lora/lora.cpp`:
```C
#include "lora.h"

// Important imports to play with buttons, keyboard, screen etc.
#include "core/globals.h"
#include "core/display.h"
#include "core/mykeyboard.h"

void lora_gw_run() {
  // Do some stuff
}

void lora_msg_run() {
  // Do some stuff
}
```

# Add support to more devices

```
.
├── platformio.ini
├── boards
    ├── [board]
    │   └── interface.cpp
    ├── pinouts
    │   ├── pins_arduino.h
    │   └── [board].h
    ├── [board].json
    └── [board].ini
...
```

# Files
(Replace \[board] with the board name)

## boards/pinouts/pins_arduio.h
This is where you will put the flag that will include your boards pinouts header.

## boards/pinouts/\[board].h
This is where you put the flags and pinouts to the board. Look at other boards for whats needed.
Here is an official example and what we are actually using here:
https://github.com/espressif/arduino-esp32/blob/master/variants/esp32s3/pins_arduino.h

## boards/\[board]/interface.cpp
This is where you do the board specific setup code

## boards/\[board].json
This is the board config. Look at other boards for whats needed.
Here is an offical example and what we are actually using here:
https://github.com/platformio/platform-espressif32/blob/master/boards/esp32-s3-devkitc-1.json

## boards/\[board].ini
This is the platformio config for the device. Look at other boards for whats needed.

## .github/workflows/buil_parallel.yml
This is the last file that should be changed to add a new device build, you should just add a new line with the environment you choose before and set the bootloader address.
