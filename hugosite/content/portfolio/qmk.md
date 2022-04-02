+++
showonlyimage = false
draft = false
image = "img/portfolio/qmk.png"
date = "2016-11-05T19:59:22+05:30"
title = "QMK"
weight = 8
+++

Create configurable layouts with the Quantum Mechanical Keyboard project
<!--more-->

[Quantum Mechanical Keyboard (QMK)](https://github.com/qmk) lets you remap the keys on the board. Super helpful if you're running a non ANSI layout, or if you just want to customise.

## Using QMK - Walkthrough

### Prerequisites

You'll need to download the latest [QMK Toolbox](https://github.com/qmk/qmk_toolbox/releases/latest) to apply the firmware to your board.

### Process Overview

Here's the process to change your keyboard key map

1. Select base layout on [https://config.qmk.fm/](https://config.qmk.fm/)
1. Customise the key mappings to suit you
1. Download Keymap (for future tweaks you might want to do to the keymap, my one is here)
1. Compile the firmware
1. Download the firmware
1. Load the firmware in the [QMK Toolbox](https://github.com/qmk/qmk_toolbox/releases/latest)

## QMK Walk-through

### Testing the board

The first thing to do when the board arrives is to plug it in and test that each of the switches would work when you assemble it. It's easiest to do this with a pair of metal tweezers and using a Keyboard testing site like [https://stendec.io/yakt/](https://stendec.io/yakt/).

### Creating the keymap

The site where you can create your Keymap is [QMK.fm](https://config.qmk.fm), you can start from scratch or use on of the keymaps from the library as a staring point.

After creating a Keymap config, compile then download the firmware file, ready for flashing.

### Flashing the board

Start by plugging in they keyboard, and making sure the prompts to install the drivers happen successfully.

Open the [QMK Toolbox](https://github.com/qmk/qmk_toolbox/releases/latest) app and load in the Firmware file. Click auto-flash and then on your board, press the reset button.

## Running QMK locally

```bash
docker run -p 5001:5001 qmkfm/qmk_api:latest
docker run -e VITE_API_URL=http://localhost:8080 -p 8080:80 qmkfm/qmk_configurator:latest
```