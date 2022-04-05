+++
image = "img/portfolio/xd64.jpg"
showonlyimage = false
date = "2022-03-30T19:44:32+05:30"
title = "XD64 Kit"
draft = false
weight = 2
+++

A build guide for the XD64, which is a GH60 based PCB. A very versatile 65% keyboard kit.
<!--more-->

The [XD64 is sold by KP Republic](https://kprepublic.com/collections/xd64-60), is a 60% (ish) QMK-programmable GH60 based keyboard kit (the GH60 was a popular open source keyboard build project in the early-mid 2010's). The XD64 fits in the GH60 keyboard cases, comes with USB-C pre-soldered and ready to plug in to the laptop (upgraded from mini USB in the GH60), it has RGB under-glow and pins available for per-key LEDs. The PCB itself is super flexible when it comes to supported layouts.

## Purchase and BOM

I paid £49 delivered, and went for `kit 8` that included the case, plate, pcb, stabs, switches and leds.
Here's the link to the kit on [AliExpress](https://www.aliexpress.com/item/32919981329.html)

Additionally i've purchased these items

Item | Spec |  Description | Cost
---- | ---- | ----------- | ----
Rubber washers for screws | Nitrile 2mm I.d 1.5mm thick | These provide some cushioning for the screws that hold the plate and pcb to the case tray. | £2 for 10

## QMK

[Quantum Mechanical Keyboard (QMK)](https://github.com/qmk) lets you remap the keys on the board. Super helpful if you're running a non ANSI layout, or if you just want to customise.

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
1. Verify the MCU is set to `atmega32u4`
1. Check auto-flash
1. Push the reset button on the bottom of the keyboard

## QMK Walk-through

### Testing the board

The first thing to do when the board arrives is to plug it in and test that each of the switches would work when you assemble it. It's easiest to do this with a pair of metal tweezers and using a Keyboard testing site like [https://stendec.io/yakt/](https://stendec.io/yakt/).

![board test](docassets/XD64-OUTOFTHEBOX.png)

### Creating the keymap

The Xd64 can have between 60 and 64 keys mapped depending on desired layout. I'm shooting for the 64 key layout, which means the usual ISO layout but with a small backspace and small right shift.

The site where you can create your Keymap is QMK.fm, and here is the layout i started with [ISO Split backspace layout](https://config.qmk.fm/#/xiudi/xd60/rev3/LAYOUT_60_iso_split_bs_rshift)

I then clicked through the key allocation config, and saved my keymap [here](qmk/layouts/xiudi_xd60_rev3_layout_60_iso_split_bs_rshift_gord.json)

After creating the Keymap config, i compile then download the firmware file, ready for flashing.

### Flashing the board

Start by plugging in they keyboard, and making sure the prompts to install the drivers happen successfully.

Open the [QMK Toolbox](https://github.com/qmk/qmk_toolbox/releases/latest) app and load in the Firmware file. Click auto-flash and then on your board, press the reset button on the underside.

![QMK toolbox](docassets/qmkToolbox.png)

### More Testing

After you've loaded the firmware, it's time to test that your new keys are registering correctly.

I use https://stendec.io/yakt/ as it supports ISO layouts.

Here's what my successful test looked like
![xd64 tested layout](docassets/XD64-2.png)

## Case mods

1. Rubber washers (2mm Internal Diameter)
1. Foam
1. Stickers!

## Switch Soldering

Hot swap sockets are pretty popular at the moment, but once you know what kind of switches you like - then it's cheaper to just solder them in.
The switches i'm putting in were stock 3 pin Gateron Red switches, which have been disassembled, lubricated, resprung and filmed to perform more like a Gateron Yellow-Black.

### Switch BOM

1. Gateron 3 pin red switches (these came with another keyboard, although my kit did come with 70 Gateron Yellows)
1. Sadan Switch films [AliExpress](https://www.aliexpress.com/item/1005002052631446.html) (£5.12 for 110)
1. 80g switch springs [AliExpress](https://www.aliexpress.com/item/1005001972722893.html) (£6.41 for 110)
1. Krytox 205g0 [Ebay](https://www.ebay.co.uk/itm/144261195166) (£5.87 for 5g w/brush)

## Stabs

The stabilisers that came with kit are Cherry style PCB mounted stabilisers. They were a super tight fit on the board, so the only tweak i did was to lubricate the stem, housing and bar ends with Krytox 205g0.

## Keycaps

I tried silicon o-rings on the keycaps to go "full stealth" - but these caused interference with the press, so i took them out.

I went with a GMK Coffee clone for the Keycap set which is quite nice. It contains the ISO modifiers, but not the regional UK-ISO keys.

## Lessons learned

Getting the layout right is super critical. I should have put switches in the plate and added keycaps to make sure that everything worked. As it was;

- The layout around the right shift key was not what i wanted. I expected i'd be able to put the up arrow above the down arrow and have a classic cursor config - but this wasn't possible with the 2.25u plate i ordered to accommodate an ISO left shift. My layout around the cursors is therefore sub optimal. I might cut the plate slightly to accommodate my preferred layout of the cursor keys, and downsize the right shift to 1u.
- I`d soldered the left control key in slightly the wrong position. I needed to de-solder and move slightly before it looked correct.

Other lessons i can take from the build;

- Don`t sticker bomb the inside of the case, it causes interference with some of the key presses. In my case it turned my space bar from being buttery smooth to being awful.
- I can`t live without the specific UK-ISO modifier keys, my keycap set didn't come with these.
- I prefer a full size backspace key. I'll therefore be adding a stabliser and moving the delete key at some point.
- A 65% layout is nice, but i think it loses too many keys for my workflow. I prefer a 75% layout, and that is as small as i will go in the future.
- Soldering switches is easy, but the minute you want to tweak the layout or disassemble a switch that's sticky you face a world of pain. It's not just about the de-soldering, you need to remove a bunch of keycaps to get to the PCB screws, then unscrew it which means the rubber standoff washers get displaced, before you can even start de-soldering. Hotswap is the future, and i won`t buy another board that doesn't have hot-swap sockets.

## Final assembly

![final build](docassets/finalbuild.jpg)

I`m super happy with the build, the keys are buttery smooth and the keycaps feel nice.
The case is a little cheap, and i may consider getting a Walnut Wooden one in the future.