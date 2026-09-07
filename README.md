# vr65816
WDC 65C816 Single Board Retro-Computer compatible with [Rumbledethump's Picocomputer Architecture](https://picocomputer.github.io/)

This project is based on [Rumbledethump's Picocomputer 6502 design](https://github.com/picocomputer/schematic), so he gets top billing. 

That said, any flaws are my fault, 'cause his board works GREAT! 

Report any problems to me using the ['Issues'](https://github.com/vruumllc/vr65816_schematic/issues) menu item above, and please don't bother him.

## Is the vr65816 for you?
Should you be building the vr65816 at all? This board is targeted at experienced programmers interested in exploring and exploiting the 65816 microprocessor. I built it because I wanted to create projects requiring more memory than the 64kB limit of the 8-bit 6502 processor. 

If you aren't an experienced programmer and just want a simple but capable retro-computer to build, create and play games on, or to re-live the exciting early days of the personal computer, then I'd strongly suggest starting with the Rumbledethump's Picocomputer 6502. Order a PCB and support his fantastic project [here](https://ko-fi.com/rumbledethumps). 

## My goals for this project
- Use 2 [Rasberry Pi Pico2s](https://www.raspberrypi.com/products/raspberry-pi-pico-2/) with [Rumbledethumps' rp6502 firmware](https://github.com/picocomputer/rp6502)
- Run [WDC 65C816](https://www.westerndesigncenter.com/wdc/documentation/w65c816s.pdf) at up to 8Mhz, clocked by Pico2W RIA
- Use currently produced through-hole ICs only, and no programmable logic
- Use 1MB SRAM, 64kB extended RAM (on Pico2W RIA), and no hardware ROM
- Use [WDC 65C22](https://www.westerndesigncenter.com/wdc/documentation/w65c22s.pdf) for timers and peripheral I/O
- Design, [breadboard](https://github.com/vruumllc/vr65816_schematic/blob/main/images/vr65816_breadboard.jpg), and test it. 
- Run all existing apps and games ("[ROMs](https://discord.com/channels/534571197908647946/1487969279251841216)") for the Rumbledethumps' RP6502 Picocomputer
- Enable [creation](https://github.com/picocomputer/rp6502-sdk) of new "ROMs" utilizing [advanced features and memory of the '816](https://archive.org/details/0893037893ProgrammingThe65816/mode/2up)
- Use [KiCad](https://www.kicad.org/download) to create fully open source schematic and board design files

<img src="images/vr65816_schematic_revA.png" width="800px"/>
<img src="images/vr65816_PCB_revA.png" width="800px"/>

## Getting the parts
I used [Mouser's 'Create a BOM'](https://www.mouser.com/en/Bom/) feature to order all parts except the PCB.  Use the 'Mouser Part Number' and 'Qty' columns from the [vr65816_full_BOM.csv](https://github.com/vruumllc/vr65816_schematic/blob/main/vr65816_full_BOM.csv) file in this repository.

My cost per kit of parts was about $114 USD, including shipping, fees, and taxes.

## Getting a PCB
I used [PCBWay](https://www.pcbway.com/Member/Login/) to fabricate my PCB:
- Click on "PCB Prototype" at upper left after logging in
- Enter Length=125 and Width=150 mm for the Size
- Select Quantity desired (5 minimum)
- Select Solder Mask and Silkscreen Colors, Surface Finish, and 'Remove Product No.' as desired
- Press the 'Calculate' button at the bottom to generate a price quote
- If the price is right, press 'Save to Cart', then 'Agree' buttons
- Drag the [vr65816_gerbers.zip](https://github.com/vruumllc/vr65816_schematic/blob/main/vr65816_gerbers.zip) file into the web dialog, then click 'Submit the file now'

After a wait of a few minutes while the file is 'Under Review' you will be allowed to place your order.

My cost was about $90 USD including shipping, fees, and taxes -- about $18 USD per PCB.

The total price per vr65816 therefore came out to be about $132 USD (September 2026, Silicon Valley, USA).

## More things you need that you may already own
Rumbledethumps has made a huge effort to support modern hardware, so you don't have to rely on ancient and expensive peripherals to use this retro-computer. Here is a list of peripherals you may already have, with some example links if you don't:

(All links are just clarifying examples and not an endorsement or guarantee of compatibility)

- USB micro-B cable with either [A](https://www.adafruit.com/product/592) or [C](https://www.adafruit.com/product/3878) connector (depending upon what your desktop or laptop computer has)
- [USB-OTG Hub with micro-B connector](https://vilros.com/products/vilros-microusb-to-usb-4-port-otg-hub-black-great-for-pi-zero)
- USB2 flash drive formatted for FAT32 (or 'msdos' in Linux)
- Keyboard, Mouse and [Gamepad](https://www.logitechg.com/en-us/shop/p/f310-gamepad) (USB-2 cable or [wireless](https://www.logitech.com/en-us/shop/p/mk470-slim-wireless-keyboard-mouse), or Bluetooth LE)
- Stereo headphones or computer speakers
- VGA Monitor and cable

  OR
  
- HDMI Monitor, cable, and [VGA to HDMI adapter](https://ventiontech.com/products/vga-to-hdmi-adapter-1080p-vga-male-to-hdmi-female-converter-cable-with-audio-usb-power-for-ps4-3-hdtv-vga-hdmi-converter) (NOT HDMI to VGA adapter!!!)

## Building the vr65816 
On a scale from 1 to 10 for electronics kit build difficulty, the vr65816 ranks about a 3. While it is probably not the best project to learn soldering on, it is an easy kit to build -- well within the capabilities of a supervised middle-school student. The component identifications are all on the back of the PCB, and listed in the [BOM](https://github.com/vruumllc/vr65816_schematic/blob/main/vr65816_full_BOM.csv).

The hardest part is making sure you have the right resisters in the right places (consult a [resister color key](https://en.wikipedia.org/wiki/Electronic_color_code), or use an Ohm meter to make sure). Other than that, just make sure your sockets (and the chips inserted in them) are the correct direction as indicated by the notch on the PCB, and that the 2 LEDs are soldered with the shorter leg (with the flat) in the hole with the square solder pad (cathode in pin1). I guess the middle row of the VGA connector might be a little tricky if you don't have a fine tipped soldering iron...but...you can do this! 

## Uploading the Picocomputer firmware
Get the latest released firmware from [here](https://github.com/picocomputer/rp6502/releases). You want the file named rp6502-#.##-pico.zip, where #.## is the latest version number. 
- Unzip the files to a temporary folder on your host computer
- Plug the micro-B USB cable into the Pico 2W (the one with the rectangular metal shield around the wireless chip)
- Press the BootSel button on the Pico 2W, then plug the other end of the cable into your host computer
- Release the BootSel button, and you should see a new drive appear on your host computer
- Copy (or drag) the rp6502-#.##-ria-w.uf2 file into the new drive
- The file should upload to the Pico 2W and turn it into the "RIA", lighting the LED.
- Repeat the process for the Pico 2, this time copying the rp6502-#.##-vga.uf2, creating the "VGA card" for the vr65816.
- Unplug the USB cable from your host computer, leaving it connected to the Pico 2 VGA micro-B port

## Testing your vr65816
OK! You should now have a completed vr65816 retro-computer of your very own. Let's test it.
- Plug the USB 2 OTG hub into the micro-B port of the Pico 2W RIA
- On your host computer, copy the [test "ROM" files](https://github.com/vruumllc/vr65816_schematic/tree/main/test_ROMS) (ending in .rp6502) from this repository into the USB flash drive
- Remove the USB flash drive from your host computer and plug it into the USB 2 OTG hub connected to the RIA
- Plug in any other USB 2 peripherals like keyboard, mouse, and gamepad, if you have them
- Plug in the headphones or computer speakers, if you have them
- Plug in the video monitor if you have it, using the VGA to HDMI adapter if you have an HDMI monitor
- Finally, plug the USB cable connected to the Pico 2 VGA back into you host computer.

If you have a video monitor connected, you should see "Picocomputer 6502" and the RIA and VGA firmware versions you uploaded, followed by the prompt ']' and a blinking cursor.

If you don't have monitor, keyboard, mouse, gamepad, or speakers yet, don't worry.  You can still continue testing as long as you have the USB cable connected from the Pico 2 VGA to your host computer.  Besides powering the vr65816, this cable supplies a serial communication channel operating at 115200 baud, 8 data bits, 1 stop bit, no parity, and no flow control. You can use a serial terminal program on your host computer to interact with the vr65816. The details vary depending upon your host computer type. I use Linux and like GTKTerm. PuttySSH also works well and exists for both Linux and Windows. Sorry, I've never owned a Mac, so you are on your own.

If you've arrived at the ']', you've verified that the Pico half of the vr65816 is working.  You are looking at the prompt for the 'monitor' program (not to be confused with a computer display!), which runs on the Pico 2W RIA. Try typing "help" to see all that it can do for you. 

You still haven't tested the 65816 half of the board, however! To do that, simply type "0" and return.  You should see the contents of the first 16 bytes of the 65816 memory, thus verifying that the RIA can talk to the 65816 microprocessor and access its memory.

Congratulations! Time to start having fun by loading some ROMs.

## Caveats
Rumbledethump's Picocomputer Architecture for the WDC 65C02 was developed over several YEARS and encompasses not just the hardware and its firmware, but platform support on two compilers, and a programming infrastructure developed for Microsoft's Visual Studio Code IDE.  All of this is a wonderful base for my project, but I went into it knowing that since it was developed for the 6502, that there would some limitations re-using it. I also knew I had NO intentions of forking any of his architecture, and instead learn to work within the limitations. You should too. 

Here are some things to keep in mind before building my vr65816:


