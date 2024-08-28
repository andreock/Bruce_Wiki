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
1. [optionnal] but recommended: work from a [Python virtualenv](https://github.com/pyenv/pyenv-virtualenv)
2. [build your firmware](https://github.com/pr3y/Bruce/wiki/Building-from-source)
3. [install your build](https://github.com/pr3y/Bruce/wiki/Installing)

## Bruce structure

Main code in `src/core` and modules in `src/modules`.
In `module` repository, we have one folder for each category. Don't hesitate to ask in the Discord where to add the files for your module.
Here we will create a new directory and new files:
```
src/
|-- core/
|-- modules/
|----- lora/
     |---- lora.h
     |---- lora.cpp
```

## Dependencies

If you need to install a new library, you have to choices:
1. use `pio` package manager
2. add your custom library in `lib/`

**Pio package manager**
If you want to install dôme librairies,  you can search or install them like:
```bash
pio pkg search mylib
pio pkg install -l mylib
```

**Warning**: do not commit the `platform.io` auto generated file. Instead add your lib in the adequat section of the file. Or ask on the Discord where to write it. 

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

We need to register our item by modifying several files. Add +1 to the `opt` counter definition in `src/main.cpp` in the `loop` function. At this time, it's 9 so we put 10 in it:
```C
int opt = 10;
```

Then we need to link our item in the main menu in `src/core/main_menu.cpp`. In `getMainMenuOptions` function, set a new switch case by switching the options. Add a new function call, here `loraOptions()` which does not exist for now. It will contains the options inside the LoRa menu:
```C
case 5: // FM Radio
  FMOptions();
  break;
case 6: // LoRa
  loraOptions(); // This is a new function we will declare later
  break;
case 7: // Other
  otherOptions();
  break;
case 8: // Clock
  runClockLoop();
  break;
case 9: // Config
  configOptions();
  break;
```

Now we need to call the item display, also in `src/code/main_menu.cpp`. We need to declare the item name in `texts` table, and to call the display in the switch case bellow. Do not forget to adjust the table length. Our display function `darwLoRa()` does not exist for now.
```C
const char* texts[10] = { "WiFi", "BLE", "RF", "RFID", "IR", "FM","LoRaWAN", "Others", "Clock", "Config" }; // add +1 to table length and add LoRa item.

// [...]

case 5:
  drawFM(WIDTH/2-40,27+(HEIGHT-134)/2);
  break;
case 6:
  drawLoRa(WIDTH/2-40,27+(HEIGHT-134)/2); // This is our new display call, dont change the parameters
  break;
case 7:
  drawOther(WIDTH/2-40,27+(HEIGHT-134)/2);
  break;
case 8:
  drawClock(WIDTH/2-40,27+(HEIGHT-134)/2);
  break;
case 9:
  drawCfg(WIDTH/2-40,27+(HEIGHT-134)/2);
  break;
```

We're done for the register part. Now, we need to declare 2 functions we called earlier: 
1. `drawLoRa()` --> the icon that will be draw on screen
4. `loraOptions()` --> the declaration of the menu when the main item is selected

### Draw a new icon

![main-menu](https://github.com/user-attachments/assets/98669885-fa9c-49c8-968d-6690da07f17b)

**drawLoRa()**
With this function, you can draw your own icon. This time, you need to declare it in `src/core/display.h`.
```C
void drawLoRa(int x, int y);
```
To be able to draw, you can use the following functions:
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

Here is an exemple of the definition in `src/core/display.cpp`:
```C
void drawLoRa(int x, int y) {
  // Blank
  tft.fillRect(x,y,80,80,BGCOLOR);

  tft.drawArc(19+x,45+y,12,10,130,230,FGCOLOR,BGCOLOR);
  tft.drawArc(19+x,45+y,22,20,130,230,FGCOLOR,BGCOLOR);
  tft.drawArc(19+x,45+y,32,30,130,230,FGCOLOR,BGCOLOR);
  tft.drawCentreString("L o R a",40+x, 40+y, SMOOTH_FONT);
}
```

### Add or modify menus

![menu](https://github.com/user-attachments/assets/fcf04298-d988-400f-8ba9-97fde78307b9)

**loraOptions()**
First comes the declaration in `main_menu.h`:
```C
void loraOptions();
```
Now we need to declare the options, also in `main_menu.cpp`. For this we use the `loopOptions()` function. 
This function takes as an argument an `options` object. In parameter, the `*_run` are functions called when the option will be selected by the user. For now, those functions do not exist.
Here is an exemple:
```C
/**********************************************************************
**  Function: loraOptions
**  LoRaWAN menu options
**********************************************************************/
void loraOptions(){
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

As we will use it later, do not forget to add the new import in `src/core/main_menu.cpp` at the begining of the file:
```C
#include "modules/lora/lora.h"
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

You may want to be able to draw a sub-menu, for exemple if you want to scan the nework ids, the use select the option and then a sub-menu appears with the found results. For this you can do the exact same thing as a simple menu, it will automatically detect you'are in a sub-menu. Moreover, you can dynamically generate your sub-menu options like this.

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

You can now start to code the main functions of your modules. Here we already made a call for `lora_gw_run()` and `lora_msg_run()`. Start to declare them in `src/modules/lora/lora.h`:
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
