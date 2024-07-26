# Firmware Flashing nRF52840 dongle using OpenOCD and a Raspberry Pi 5

OpenOCD is a on chip debugger that allowdirect access to the microcontroler through wired interface

More infornmation can be accessed on the webpage https://openocd.org/

It is recommended to download and compile the source code from the official github https://github.com/openocd-org/openocd/ 
as more and more interface configurations are added to the project.

## 1. The case

I have bought an generic nRF52840 dongle to test OpenThread implementation. However the dongle arrived dead,
no response when plugged to the computer, although externally it was unscratched.

![image](https://github.com/user-attachments/assets/c61afe82-1d1c-4c5f-b435-f061a1996a6f)
![image](https://github.com/user-attachments/assets/922f6fd6-b072-4c0c-a736-098504e5c892)

I opened the dongle as the circuit board used is kind for development, many GPIO pins are exposed on the board.
So I tried to energize using the 5V bus and no luck, tried the 3.3V...  game on!

## 2. Pinout Schematics

![image](https://github.com/user-attachments/assets/98d8d7e5-88ac-4d82-bfbb-cd1a832b6737)

| Pin No.  	 | <br>Name	    | <br>Direction	 | <br>Function                                                                                   |
|------------|--------------|----------------|------------------------------------------------------------------------------------------------|
| 1          | GND          | —              | Power Ground                                                                                   |
| 2          | P0.10        | J24            | See nRF52840 chipset datasheet                                                                 |
| 3          | P0.09        | L24            | See nRF52840 chipset datasheet                                                                 |
| 4          | P1.04        | U24            | See nRF52840 chipset datasheet                                                                 |
| 5          | P1.02        | W24            | See nRF52840 chipset datasheet                                                                 |
| 6          | P1.00        | AD22           | See nRF52840 chipset datasheet                                                                 |
| 7          | P1.07        | P23            | See nRF52840 chipset datasheet                                                                 |
| 8          | P1.01        | Y23            | See nRF52840 chipset datasheet                                                                 |
| 9          | P0.24        | AD20           | See nRF52840 chipset datasheet                                                                 |
| 10         | P0.22        | AD18           | See nRF52840 chipset datasheet                                                                 |
| 11         | P0.20        | AD16           | See nRF52840 chipset datasheet                                                                 |
| 12         | P0.17        | AD12           | See nRF52840 chipset datasheet                                                                 |
| 13         | P0.15        | AD10           | See nRF52840 chipset datasheet                                                                 |
| 14         | P0.13        | AD8            | See nRF52840 chipset datasheet                                                                 |
| 15         | P0.14        | AC9            | See nRF52840 chipset datasheet                                                                 |
| 16         | VBUS         | USB5V          | This interface cannot be powered at the same time as the USB interface, the maximum is 5.5V    |
| 17         | VDD          | —              | Chip power supply pin, maximum 3.6V, cannot be supplied with USB power supply at the same time |
| 18         | GND          | —              | Power Ground                                                                                   |
| 19         | P0.04        | J1             | See nRF52840 chipset datasheet                                                                 |
| 20         | P0.26        | G1             | See nRF52840 chipset datasheet                                                                 |
| 21         | P0.11        | B19            | See nRF52840 chipset datasheet                                                                 |
| 22         | P0.31        | A8             | See nRF52840 chipset datasheet                                                                 |
| 23         | P0.29        | A10            | See nRF52840 chipset datasheet                                                                 |
| 24         | P0.02        | A12            | See nRF52840 chipset datasheet                                                                 |
| 25         | P1.15        | A14            | See nRF52840 chipset datasheet                                                                 |
| 26         | P1.13        | A16            | See nRF52840 chipset datasheet                                                                 |
| 27         | P1.11        | B19            | See nRF52840 chipset datasheet                                                                 |
| 28         | P1.10        | A20            | See nRF52840 chipset datasheet                                                                 |
| 29         | GND          | —              | Power Ground                                                                                   |
| 30         | GND          | —              | Power Ground                                                                                   |
| 31         | V            | VDD            | Download interface, try to avoid USB and VDD supplying power at the same time                  |
| 32         | R            | RESET          |                                                                                                |
| 33         | D            | SWDIO          |                                                                                                |
| 34         | C            | SWCLK          |                                                                                                |
| 35         | G            | GND            |                                                                                                |
| 36         | RST          | RESET          | Reset button.                                                                                  |
| 37         | SW           | P1.06          | function button                                                                                |
| 38         | LED1         | RGB LED        | R (red): P0.08; G (green): P1.09; B (blue): P0.12;                                             |
| 39         | LED          | LED            | P0.06                                                                                          |
| 40         | G            | GND            | USB Test Port /span&gt;                                                                        |
| 41         | D+           | —              |                                                                                                |
| 42         | D-           | —              |                                                                                                |
| 43         | V            | VBUS           | USB Test Port                                                                                  |

