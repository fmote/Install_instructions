# Firmware Flashing nRF52840 dongle using OpenOCD and a Raspberry Pi 5

OpenOCD is a on chip debugger that allowdirect access to the microcontroler through wired interface

More infornamtion can be accessed on the webpage https://openocd.org/

It is recommended to download and compile the source code from the official github https://github.com/openocd-org/openocd/ 
as more and more interface configurations are added to the project.

## The case

I have bought an generic nRF52840 dongle to test OpenThread implementation. However the dongle arrived dead,
no response when plugged to the computer, although externally it was unscratched.

I opened the dongle as the circuit board used is kind for development, many GPIO pins are exposed on the board.
So I tried to energize using the 5V bus and no luck, tried the 3.3V and bingo!
