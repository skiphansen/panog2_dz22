# Fujitsu Zero Client DZ22-2

![](https://github.com/skiphansen/pano_blocks/blob/master/assets/dz22_1.png)
![](https://github.com/skiphansen/pano_blocks/blob/master/assets/dz22_2.png)

This project contains information about hacking the Fujitsu Zero Client DZ22-2

This is an 22 in LCD monitor with a built in Pano device similar to the [Rev B G2](https://github.com/tomverbeure/panologic-g2/wiki/Identifying-different-Pano-generations-and-revisions#second-generation).  
Please see Tom Verbeure's reverse engineering [project](https://github.com/tomverbeure/panologic-g2)
for the G2 and the [Pano Hacker's Wiki](https://github.com/tomverbeure/panologic-g2/wiki)
for additional information.

## Features

- Based on the largest FPGA in the Spartan 6 family with 147,443k equivalent logic cells
- 1680 x 1050 pixels TFT LCD display with LED back lighting
- Swivel mount providing landscape or portrait orientation
- PoE (Power over Ethernet)
- Build in speakers with volume control
- 3.5 mm jack sockets for headphones **and** microphone.
- 4 USB sockets
- DVI-D port for second monitor
- digital screen controller with microprocessor for storing 12 different display modes

## LCD interface

It appears that the DZ22 uses the same bitfile and basic design as a "normal" 
G2.  One of the monitor ports in connected internally to a NT68667FG monitor
controller which includes a scaler.

According to the [User Manual](./assets/4503673.pdf) the scaler should be
capable of handling horizontal rates from 30 to 82 kHz and vertical rates from 
59 to 76 Hz.  This will be handy for porting projects designed for VGA 
interfaces.

Interestingly the NT68667FG includes a 8031 processor which handles the OSD
display for screen adjustments was well as volume and power control.

The firmware for the NT68667FG appears to be store externally in an 128K SPI 
flash [chip](./Pm25LV010.pdf). There really shouldn't be any need to hack the 
controller's firmware, but that might be a fun project if someone is interested.  

The firmware even appears to be updateable via one of the USB ports after 
putting the controller in an update mode probably via some odd button press 
sequence.  Some old Philips LCD monitors used similar controllers and their 
[service manual](./assets/Philips_meridian2_service_manual.pdf) documented the 
procedure.

I was unable to find any information about programming the 8031, but Ghidra
supports it the 8031 ...

## Links

- Pano Hacker's [Wiki](https://github.com/tomverbeure/panologic-g2/wiki)
- [PCB pictures](https://github.com/zsteva/panologic-fujitsu) take by Zeljko Stevanovic
- [User Manual](./assets/4503673.pdf)
- [Citrix XenDesktop Manual](./assets/62122223.pdf)
- SGM7222 USB switch [spec sheet](./assets/1640934749.pdf)
- [NT68667FG spec sheet](./assets/NT68667FG_Novatek.pdf)
- [Youtube video](https://www.youtube.com/watch?v=FunpjWlPepY) showing how to open it.
