# The WiFi ID Card

Welcome to my adventures in placing my WiFi info, on an ID card (ID-1 Format, 85.6 x 53.98 mm or 3.370 x 2.125 inches).

## Why the need for this project

Picture this: you invite some friends at your place, or family, and they get tired of dealing with you or just want to have some internet time away from the kids (that are destroying your house) and the question arrives "can I connect to the WiFi?". At this point you open a drawer, look frenetically for the original piece of paper from the cable company, and then you remember that you saw your kids playing with that exact same piece of paper some days ago, it is now gone. “Fine”, you say, “I know it by heart, the SSID is (insert generic cable company SSID here) and the password is (m4573r_h4x0r)”.
This is quite common, I don’t have a data plan so, every time I want to show or do something on the internet while away, this is the kind of thing that happens. But recently, I’ve noticed a QR Code icon on my phone and it lead me to wonder, how do this work, and, more important, how can I use it. There are alternatives, like WPS, but my kids are always touching that big button so I disabled that feature on the router (yes I know that sometimes it doesn't work, but a recent firmware release took care of exacly that).

## How it will be done

### The Format

The idea is to generate an ID card size document with the WiFi information in both text and on a QR Code (the WPS Pin can also be included).
The ID-1 Card Format has the following dimentions (ISO/IEC 7810) [^ISO7810]:

| Dimentions (mm) | Dimentions (inch) |
| --------------- | ----------------- |
| 85.6 x 53.98    | 3.370 × 2.125     |

This format size was chosen since it can be placed on those ID card holders and then glued on the router and take it every time it's needed. Yes I know that my kids might play with it also, but I can either print a new one, or show a pdf version that I will keep on my phone.

[^ISO7810]: https://www.iso.org/standard/70483.html

### The QR Code

There are a million websites where one can get a QR with the WiFi information. The problem of this, you have no idea how this information might be used. Moreover, I really like to try things by myself.
This standard was invented by the ZXing Project [^ZXingProject] in june 2010 [^ZXingCommit]. It's actually pretty neat since it supports different configurations like WEP/WPA/no password, SSID/hidden SSID, TTLS/PWD, etc. Looking at the documentation [^ZXingDocumentation], we cand define a specific syntax with all the WiFi parameters, to create a QR Code afterwards. As an example:
```
WIFI:T:WPA;S:networkname;P:password;;
```
Where:

| Parameter | Example       | Description         |
| --------- | ------------- | ------------------- |
| T         | `WPA`         | Authentication type |
| S         | `networkname` | Network SSID        |
| P         | `password`    | Password            |

The remainder parameters as well as all the different possibilities are described on the official documentation [^ZXingDocumentation]. I will focus on these three parameters as they the ones used on the majority of cases, incuding mine.
Now that we know the syntax needed, how do we create our card?

[^ZXingProject]: https://github.com/zxing
[^ZXingCommit]: https://github.com/zxing/zxing/commit/58fefb095c9564dcbd0dbf4d2f1f90cffede10c8
[^ZXingDocumentation]: https://github.com/zxing/zxing/wiki/Barcode-Contents#wi-fi-network-config-android-ios-11

### The Software

Inkscape is the software to go. Free and open source, this design tool does everything I need, from text, to generate QR codes. Even better, we can script this in a way to autogenerate our ID card with all the informations. 




