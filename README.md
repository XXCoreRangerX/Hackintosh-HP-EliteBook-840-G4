# Hackintosh-HP-EliteBook-840-G4
OpenCore EFI for the HP EliteBook 840 G4

### Overview:
This repository was built to make a fully working OpenCore EFI for this laptop. It's based on my work and help from other people.

#### Laptop Specification:
- BIOS: For the highest stability use 1.29 (latest version works too, but need to remake SSDT-BATT for better battery management)
- CPU: Intel® Core i7-7600U Quad Core
- GPU: Intel® HD Graphics 620
- RAM: 8GB DDR4 2133MHz
- WiFi/BT: Apple AirPort BCM94360CS2
- Audio: Conexant CX8200
- ETH: Intel® Ethernet Connection I219-V
- Display: 14" Full HD Touchscreen
- Touchpad: Synaptics SMBus
- Keyboard: PS2 HP Keyboard
- SD Card Reader: Realtek

#### BIOS Settings:
- Disable TPM Security
- Disable Physical Presence Interface
- Disable Intel SGX
- Enable System Management Command
- Disable Fast Boot
- Enable USB Storage Boot
- Disable Network PXE Boot
- Disable Power On when AC Detected
- Disable Power On when Lid is Opened
- Disable Secure Boot
- Disable Legacy Boot
- Enable Turbo Boost
- Enable Hyperthreading
- Enable Multi-Processor
- Enable VT-x
- Disable VT-d
- Disable Fast Charge
- Enable Turbo Boost on DC
- Disable HP Application Driver
- Enable LAN Controller
- Disable Wake on LAN
- Disable Lock Wireless Button
- Enable WLAN
- Enable Bluetooth
- Disable LAN/WLAN Auto Switching
- Enable Fan Always On while on AC Power
- Enable Fan Quietness Mode
- Enable Boost Converter
- Enable Touch Device
- Enable Integrated Camera
- Enable Media Card Reader
- Disable Smart Card
- Enable Runtime Power Management
- Disable Extended Idle Power States
- Disable Deep Sleep
- Disable Wake when Lid is Opened
- Disable Wake when AC is Detected
- Disable Wake on USB
- Enable Power Control

#### Not working:
- Proper CFG Unlock (there isn't an option in the BIOS, and I didn't find any way to disable it)
- FingerPrint Scanner (currently there's no way to emulate any fingerprint scanner (different than original Touch ID) under macOS
- Trackpoint
- Boot chime
- External display on VGA
- Touchpad disable (both button and LED not working)
- WiFi Button (LED always orange, button does nothing)
- F4 and F10 functions (need to disable FN+F3 and map FN+F10 to Play/Pause)

#### Not tested:
- NFC module 
- LTE module
- SC reader
- Dock station


##### Thanks to:
- [acidanthera](https://github.com/acidanthera) for OpenCore and almost all the kexts and drivers
- [dortania](https://github.com/dortania) for an awesome OpenCore guide
- [corpnewt](https://github.com/corpnewt) for many useful tools
- [headkaze](https://github.com/headkaze) for Hackintool
- [alexandred](https://github.com/alexandred) for VoodooI2C
- [ben9923](https://github.com/ben9923) for helping me fix all touchscreen related issues
- [1Revenger1](https://github.com/1Revenger1) for VoodooRMI
- [cholonam](https://github.com/cholonam) and [sinetek](https://github.com/sinetek) for Sinetek-rtsx
- [RehabMan](https://github.com/RehabMan) for many laptop hotpatches
- [kreizlie](https://github.com/kreizlie) for modified hotpatches and BIOS settings
- everyone who helped me on Reddit, Discord and GitHub
