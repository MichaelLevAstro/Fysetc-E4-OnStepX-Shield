# Shield for adding Extra modules to FYSETC E4 Board

<img width="1425" height="1039" alt="image" src="https://github.com/user-attachments/assets/396caa11-e8d1-470b-9e16-d33d574d5bb8" />

## Added features
- GPS through X-Min pin
- MCP23017 IO expander for homing sensors using I2C
- FRAM for persistent data
- 5V Laser with Switch
- 12v to 24v step up module for a Motor Brake using an XL6009 module

Links to modules:
FRAM:
https://www.aliexpress.com/item/1005006584211412.html?sk=6mia6uv

MCP23017:
https://www.aliexpress.com/item/1005005335661057.html?spm=a2g0o.order_list.order_list_main.26.48951802nkMEFA

DC Step up:
https://www.aliexpress.com/item/32762092828.html?spm=a2g0o.order_list.order_list_main.37.48951802nkMEFA

Home sensors i used (Wide body):
https://www.aliexpress.com/item/32990256417.html?spm=a2g0o.order_list.order_list_main.58.48951802nkMEFA

GPS:
https://www.aliexpress.com/item/1005006495592091.html?spm=a2g0o.order_list.order_list_main.47.48951802nkMEFA
*note: any GPS using a TX should work (as long as it works with TinyGPS++)
*note2: GPS is very sensitive and often can communicate with enough satellites and cant get a fix, up to you to make it work properly in your enclosure.

Laser:
Any 5v laser should work fine


# OnStepX configurations
In config.h

```
#define LIMIT_SENSE_PIN                 0 // Set this to 0 or even comment it out, wont be used

// FRAM
#define NV_DRIVER             NV_MB85RC64

// Homing sensors
#define AXIS1_SENSE_HOME             HIGH
#define AXIS2_SENSE_HOME             HIGH

// GPS
#define TIME_LOCATION_SOURCE          GPS
#define SERIAL_GPS SoftSerial
#define SERIAL_GPS_RX 34
#define SERIAL_GPS_TX 0 // must be set or wont compile
#define SERIAL_GPS_BAUD 9600
```

In src\pinmaps\Pins.FYSETC_E4.h:
```
// Needed for IO expander to work
#define AXIS1_SENSE_HOME_PIN  GPIO_PIN(0)
#define AXIS2_SENSE_HOME_PIN   GPIO_PIN(1)
```

# Connections
<img width="1080" height="686" alt="E4ShieldConnections" src="https://github.com/user-attachments/assets/4b89f366-4621-4fe0-a8d4-e3c578e52410" />

*note: X-Min connector in the shield is a 2 pin connector, you dont have to connect GND, you can connect only the X-Min.

# Assembly
I used M3 standoffs, and removed anything tall from the board, the original heatsinks for the motors drivers and the green power connectors.
Had to make room to fit in my mount.
![WhatsApp Image 2025-07-10 at 00 03 44_10ef709c](https://github.com/user-attachments/assets/f733699d-266a-4a80-9057-503a33c5eeda)
