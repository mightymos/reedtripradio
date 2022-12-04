### Description
Alternative firmware for wireless 433MHz magnetic door/window reed sensors.

STC15W104 are 8051 based processors + SYN115 radio transmitter.
'104 model has 4KB flash space and board also has a tamper detect switch which is cool.

Some sensors have STC15W101 but with only 1KB flash. Also some sensors purchased did not have tamper switch.
However 1KB flash would not support hardware abstraction layer (unless emulated EEPROM area can be used for code space).

STC processors do not allow read/verify of written firmware so open source alternative is needed to confirm program behavior.

Boards contain a header that may be populated with pins labeled with G (ground), T (transmit), and R (receive) for flashing.

### Receiver Hardware
[Sonoff RF Bridge 433](https://tasmota.github.io/docs/devices/Sonoff-RF-Bridge-433/ "Sonoff Bridge 433 MHz")

[Sonoff RF Bridge 433 (espurna)](https://github.com/xoseperez/espurna "ESPurna")

ESPurna is nice because it treats wireless sensors as "virtual" sensors (show up as permanent switch entities in Home Assistant).
Also ESPurna can learn unique sensor codes.

[Portisch](https://github.com/Portisch/RF-Bridge-EFM8BB1 "Portisch")
Some Sonoff Bridge(s) contain an onboard EFM8BB1 which can additionally be flashed to support more radio protocols.


Flashing tool:
https://github.com/area-8051/stcgal-patched

Firmware uses hardware abstraction layer (HAL):
https://github.com/area-8051/uni-STC

| Proposed features | original or added | status |
| ------------- | ------------- | ------------- |
| Transmit on reed switch open/close (interrupt)  | original  | DONE |
| Transmit on tamper switch open/close (interrupt)  | original  | DONE |
| Manage power modes  | original  | DONE |
| Support inverted protocols  | added  | DONE |
| Ability to select any supported rc-switch transmission protocol  | added  | DONE |
| "Heart beat" mode for periodic transmission   | added  | DONE |
| Adjustable LED blink behavior   | added  | TODO |
| Adjustable sleep behavior  | added  | DONE |
| User configuration/input with tamper switch press(es) or serial bytes  | added  | DONE |
| Add tamper closed key  | added  | DONE |
| Add tamper "trip" mode   | added  | TODO |
| Store settings in EEPROM  | added  | DONE |
| Send information over radio (e.g., settings?, battery?)  | added  | TODO |
| Compare power usage to original firmware  | added  | TODO |
| Test transmission protocols 2-12  | added  | TODO |

![alt text](/photos/hookup_example.jpg "Wireless 433 MHz Door Sensor")