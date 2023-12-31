The Tool Control system is built around an Arduino Uno. The LCD Display requires four GND connections, plus two 5V connections, plus the 5V and GND connections for the two buttons, so terminal blocks are used to connect multiple wires to these pins.

# Components
* Arduino Uno
* Ethernet Shield
* 16x2 LCD Screen
* MFRC522 RFID Reader
* 2 x Momentary Push Buttons
* Relay
* 1 x 8mm M3 Female-Female Hex Standoffs
* 2 x Terminal Strip Terminals (or 2 x 5-way Wago)
* 7 x Male-Female Jumper Wires
* 2 x Male-Bare Jumper Wires (Can use Male-Any Jumpers and cut off the non male end depending on what you have available)
* 6 x Female-Bare Jumper Wires (same as above)
* 6 x Male-Female Jumper Wires
* Junction Box Style Enclosure (To be replace with 3D Printed Enclosure in Version 2)

# Pin Mapping

## Arduino

| Arduino Pin | Destination | Use |
| ------------- | ------------- | ------------- |
| A0 | LCD D4 Pin | Data pin for LCD Display |
| A1 | LCD D5 Pin | Data pin for LCD Display |
| A2 | LCD D6 Pin | Data pin for LCD Display |
| A3 | LCD D7 Pin | Data pin for LCD Display |
| 2 | LCD RS Pin | Register Select pin for LCD Display |
| 3 | LCD E Pin | Enable pin for LCD Display |
| 5 | RFID SDA Pin | Slave Select for RFID SPI |
| 6 | Induct Button | Input for Induct Button |
| 7 | Sign Out Button | Induct for Sign Out Button |
| 9 | RFID RST Pin | Reset pin for RFID |
| 11 | RFID SCK Pin | SCK pin for RFID SPI |
| 12 | RFID MOSI Pin | MOSI pin for RFID SPI |
| 13 | RFID MISO Pin | MISO pin for RFID SPI |
| GND (next to 13) | RFID GND Pin | Ground pin for RFID |
| 3.3V | RFID 3.3V Pin | Power pin for RFID |
| GND (next to power pins) | Terminal Block | Ground ref for LCD |
| 5V | Terminal Block | 5V ref for LCD |

## RFID 

## LCD

| LCD Pin | Destination | Use |
| ------------- | ------------- | ------------- |
| VSS | Ground Terminal Block | Ground |
| VDD | +5V Terminal Block | Power |
| V0 | Ground Terminal Block | Contrast |
| RS | Arduino Pin 2 | Register Select |
| R/W | Ground Terminal Block | Read/Write Signal |
| E | Arduino Pin 3 | Enable Signal |
| DB4 | Arduino Pin A0 | Data Pin |
| DB5 | Arduino Pin A1 | Data Pin |
| DB6 | Arduino Pin A2 | Data Pin |
| DB7 | Arduino Pin A3 | Data Pin |
| A | +5V Terminal Block | Backlight Power |
| K | Ground Terminal Block | Backlight Ground |

# How it works

[[TBC]]