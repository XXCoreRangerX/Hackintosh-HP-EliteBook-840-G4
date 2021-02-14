# Hackintosh-HP-EliteBook-840-G4
OpenCore EFI for the HP EliteBook 840 G4

# Overview:
This repository was built to make a fully working OpenCore EFI for this laptop. It's based on my work and help from other people.

![Screenshot](img/main.png)

## Laptop Specification:
- BIOS: For the highest stability use 1.29 (latest version works too, but need to remake SSDT-BATT for better battery management)
- CPU: Intel® Core i7-7600U Quad Core (for other CPUs, you need to make CPUFriendDataProvider.kext [yourself](https://dortania.github.io/OpenCore-Post-Install/universal/pm.html#using-cpu-friend))
- GPU: Intel® HD Graphics 620
- RAM: 8GB DDR4 2133MHz
- Wi-Fi/BT: Apple AirPort BCM94360CS2 (if you're using the builtin Intel WiFi - inject [Itlwm](https://github.com/OpenIntelWireless/itlwm) and [IntelBluetoothFirmware](https://github.com/OpenIntelWireless/IntelBluetoothFirmware) kexts)
- Audio: Conexant CX8200
- ETH: Intel® Ethernet Connection I219-V
- Display: 14" Full HD Touchscreen (for the non-touch model, remove everything regarding VoodooI2C, and use VoodooInput from VoodooRMI)
- Touchpad: Synaptics SMBus
- Keyboard: PS2 HP Keyboard
- SD Card Reader: Realtek

## BIOS Settings:
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

### CPU Power Management
The settings I used for CPUFriendFriend, for managing CPU power:
| Feature | Setting |
| ------------- | ------------- |
| LFM (Low Frequency Mode) | 800Mhz (recommended value from Intel ARK website) |
| EPP (Energy Performance Preference) | 0x3F (focused on performance, but with decent battery saving)|
| Performance Bias | 0x05 (focused on fair performance and high stability)|
| Additional Energy Savings Options | Yes |

### Configure sleep
![Screenshot](img/sleep.png)

These are the settings that work for me. Setting hibernatemode to 0 doesn't let me put the laptop into sleep mode, so I kept the default value.

To apply patches for sleep - type the following commands in the terminal:
```
sudo pmset autopoweroff 1
sudo pmset powernap 0
sudo pmset proximitywake 0
sudo pmset sleep 1
sudo pmset standby 1
```

### HiDPI Scaling (Retina Scaling)
![Screenshot](img/hidpi.png)

Retina displays on real Apple devices have a high pixel density because of HiDPI scalling. One logical pixel is four physical pixels on Retina displays. This can be emulated on Hackintoshes too. I used a script called [one-key-hidpi](https://github.com/xzhih/one-key-hidpi) which works pretty good on this device. Since Full HD is quite hard to work on while using a 14" display, this is a really useful fix. However, using it will make the Apple boot logo large at 2nd boot stage, and I haven't found a way to fix that yet.

These are the options I used in the script:
| Feature | Setting |
| ------------- | ------------- |
| HiDPI | Enable HiDPI |
| Icon | MacBook Pro |
| Resolution | 1920x1080 |

## Not working:
- DRM (isn't supported on iGPU only systems)
- Proper CFG Unlock (there isn't an option in the BIOS, and I didn't find any way to disable it)
- FingerPrint Scanner (currently there's no way to emulate any fingerprint scanner (different than original Touch ID) under macOS
- Trackpoint
- Boot chime
- External display on VGA
- Dot to disable touchpad (in the upper left corner of the touchpad)
- WiFi Button (LED always orange, button does nothing)
- F4 and F10 functions (need to disable FN+F3 and map FN+F10 to Play/Pause)

## Not tested:
- NFC module 
- LTE module
- SC reader
- Dock station
- USB-C


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
