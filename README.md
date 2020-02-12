# WLAN RGB(W) LED Controller
Gerät zum Steuern von 12V RGB(W) LED Streifen über WLAN.

![Ansicht](https://github.com/damianmelson/WLAN-RGBW-LED-Controller/blob/master/images/ansicht_oben.jpg)
![Ansicht](https://github.com/damianmelson/WLAN-RGBW-LED-Controller/blob/master/images/ansicht_unten.jpg)

## Schaltplan

![Schaltplan](https://github.com/damianmelson/WLAN-RGBW-LED-Controller/blob/master/images/schaltplan.png)

Jumperstellung und GPIO-Belegung:<br>
SJ1 und SJ2 links = RGB<br>
SJ1 und SJ2 rechts = RGBW<br>

|   | RGB  | RGBW |
|---|------|------|
| R | IO14 | IO5  |
| G | IO5  | IO14 |
| B | IO12 | IO12 |
| W |      | IO13 |

U3 optionaler IR-Empfänger am GPIO4.

## Platine
[Gerberdaten](https://github.com/damianmelson/WLAN-RGBW-LED-Controller/tree/master/gerber) für [PCBWay](https://www.pcbway.com) und [ALLPCB](https://www.allpcb.com).<br>

![Platine oben](https://github.com/damianmelson/WLAN-RGBW-LED-Controller/blob/master/images/pcb_oben.png)
![Platine unten](https://github.com/damianmelson/WLAN-RGBW-LED-Controller/blob/master/images/pcb_unten.png)

[Bauelemente](https://github.com/damianmelson/WLAN-RGBW-LED-Controller/tree/master/docs) von [reichelt elektronik](https://www.reichelt.de), [LCSC](https://lcsc.com) und [eBay](https://www.ebay.de).<br>
U2 bestückbar mit 12V auf 3.3V DC-DC Step-Down Konvertermodul von [eBay](https://www.ebay.de).<br>

Strombelastbarkeit:<br>
RGBW [Leiterbahnbreite](https://www.mikrocontroller.net/articles/Leiterbahnbreite) 56 mil.

## Firmware
- J1 Lötbrücke öffnen, FLASH Lötbrücke schließen.<br>
- JP1 mit einem USB zu TTL Adapter (3.3V Logikpegel) verbinden.<br>
- [MagicHome](https://github.com/damianmelson/WLAN-RGBW-LED-Controller/tree/master/firmware) RGB Firmware flashen:<br>
`esptool.py --port /dev/ttyUSBx --baud 230400 write_flash 0x00000 MagicHome_RGB.bin`<br>
USBx ist anzupassen an die aktuell benutzte Schnittstelle.<br>
- FLASH Lötbrücke öffnen, J1 Lötbrücke schließen.<br>

Alternative [ESPurna](https://github.com/xoseperez/espurna) und [Tasmota](https://github.com/arendst/Tasmota) Firmware mit IR-Empfang für MagicHome LED Controller.

## Gehäuse
[TEKO](http://www.tekoenclosures.com) 10014 Gehäuse Serie Soap.

## FHEM
MagicHome LD382 WiFi RGB LED Controller in [FHEM](https://wiki.fhem.de/wiki/WifiLight) anlegen:<br>
`define <name> WifiLight RGB LD382:<IP|FQDN>`

## App
MagicHome App für [Android](https://play.google.com/store/apps/) und [iOS](https://www.apple.com/ios/app-store/).

