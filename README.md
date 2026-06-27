# HP Elite X2 1012 G2 Hackintosh OpenCore EFI

[![macOS](https://img.shields.io/badge/macOS-Sonoma%2FSequoia-blue)](https://www.apple.com/macos/)
[![OpenCore](https://img.shields.io/badge/OpenCore-1.0.x-green)](https://github.com/acidanthera/OpenCorePkg)
[![Device](https://img.shields.io/badge/HP-Elite%20X2%201012%20G2-lightgrey)](https://support.hp.com)

## 🖥️ Hardware Overview

| Component | Model | Status |
|-----------|-------|--------|
| **Model** | HP Elite X2 1012 G2 (Detachable Laptop/Tablet) | ✅ |
| **BIOS** | P87 Ver. 01.15 (UEFI) | ✅ |
| **CPU** | Intel Core i5-7200U (Kaby Lake, 2C/4T) | ✅ |
| **GPU** | Intel HD Graphics 620 (Device ID: 8086-5916) | ✅ |
| **Audio** | Conexant CX8200 (HDA: 14F1-2008) | ⚠️ |
| **Storage** | Samsung MZNLN128HAHQ-000L1 (128GB SATA SSD) | ✅ |
| **Wi-Fi** | Intel Dual Band Wireless-AC 8265 | ⚠️ |
| **Bluetooth** | Intel 8087-0A2B | ⚠️ |
| **Touchscreen** | WCOM483E (Wacom I2C) | ⚠️ |
| **Keyboard** | PS/2 (HPQ8002) | ✅ |
| **Touchpad** | ALP0110 (PS/2) | ⚠️ |
| **Fingerprint** | Synaptics VFS7552 (138A-0092) | ❌ |
| **SD Card** | Realtek 10EC-522A | ⚠️ |
| **LTE** | HP lt4120 Snapdragon X5 LTE | ❌ |
| **Display** | 12" 2736×1824 (3:2) | ✅ |

## 📋 Detailed Hardware Info

### ⚙️ Core Components

| Item | Detail |
|------|--------|
| **Motherboard** | HP HP ELITE X2 1012 G2 |
| **Chipset** | Sunrise Point (Kaby Lake-U) |
| **BIOS Version** | P87 Ver. 01.15 (2018-01-25) |
| **Firmware** | UEFI (Secure Boot: Disabled) |
| **CPU** | Intel Core i5-7200U @ 2.50GHz (Max 3.10GHz) |
| **Cores** | 2 Physical, 4 Logical |
| **SIMD** | SSE4.2, AVX2 |
| **GPU** | Intel HD Graphics 620 (GT2, 24EU) |
| **GPU ID** | 8086:5916 |
| **GPU ACPI** | `\_SB.PCI0.GFX0` |
| **Memory** | 8GB LPDDR3 (Onboard) |

### 🔊 Audio

| Item | Detail |
|------|--------|
| **Audio Controller** | Intel Sunrise Point-LP HD Audio (8086-9D71) |
| **Codec** | Conexant CX8200 (14F1-2008) |
| **Layout ID** | TBD |
| **Speakers** | ✅ Internal |
| **Mic** | ✅ Internal |

### 🌐 Network

| Item | Detail |
|------|--------|
| **Wi-Fi** | Intel Dual Band Wireless-AC 8265 (8086-24FD) |
| **Bluetooth** | Intel 8087-0A2B (USB) |
| **LTE** | HP lt4120 Snapdragon X5 LTE (03F0-9D1D) — **Not supported** |
| **Ethernet** | None (Tablet design) |

### 🖱️ Input

| Item | Detail |
|------|--------|
| **Keyboard** | PS/2 (HPQ8002) |
| **Touchpad** | ALP0110 (PS/2) |
| **Touchscreen** | WCOM483E (Wacom I2C HID) |
| **Pen** | Wacom AES 2.0 (via WCOM483E) |
| **Buttons** | Volume, Power, Windows Button |

### 🛠️ Other

| Item | Detail |
|------|--------|
| **USB Controller** | Intel xHCI (8086-9D2F) + ASMedia USB 3.1 |
| **SATA** | Intel Sunrise Point-LP AHCI (8086-9D03) |
| **SD Reader** | Realtek 10EC-522A (PCIe) |
| **Fingerprint** | Synaptics VFS7552 (138A-0092) — **Not supported** |

## ✅ Working / ❌ Not Working

| Feature | Status | Notes |
|---------|--------|-------|
| CPU Power Management | ✅ | Native PM via Kaby Lake |
| Intel HD Graphics 620 | ✅ | Full acceleration + QE/CI |
| Display (2736×1824) | ✅ | Native resolution support |
| USB (Type-C/Type-A) | ✅ | Via USBInjectAll + SSDT |
| SATA SSD | ✅ | TRIM support via `trimforce` |
| Keyboard | ✅ | PS/2 via VoodooPS2 |
| Battery | ⚠️ | Requires ACPI patching |
| Audio | ⚠️ | Conexant CX8200 needs AppleALC |
| Wi-Fi | ⚠️ | Intel 8265 via AirportItlwm/HeliPort |
| Bluetooth | ⚠️ | Intel Bluetooth via IntelBluetoothFirmware |
| Touchpad | ⚠️ | ALP0110 PS/2 via VoodooPS2 |
| Touchscreen | ⚠️ | Wacom I2C — experimental |
| Pen Input | ⚠️ | Wacom AES — experimental |
| SD Card Reader | ⚠️ | Realtek PCIe — requires Sinetek-rtsx |
| Brightness Control | ⚠️ | Requires BrightnessKeys + SSDT-PNLF |
| Sleep/Wake | ⚠️ | Requires correct USB mapping |
| Wi-Fi Handoff | ❌ | Intel limitation |
| Fingerprint | ❌ | Synaptics — no macOS driver |
| LTE Modem | ❌ | Snapdragon X5 — no macOS driver |
| Rotation Sensor | ❌ | Requires further investigation |
| Tablet Mode Switch | ❌ | Requires further investigation |
| Docking | ❌ | Not tested |

## 📁 Repository Structure

```
HP-Elite-X2-1012-G2-Hackintosh/
├── EFI/
│   ├── BOOT/
│   │   └── BOOTx64.efi
│   └── OC/
│       ├── ACPI/
│       ├── Drivers/
│       ├── Kexts/
│       ├── Tools/
│       ├── config.plist
│       └── OpenCore.efi
├── README.md
└── Resources/
```

## 🔧 Recommended Kexts

| Kext | Purpose |
|------|---------|
| **Lilu.kext** | Required (patch engine) |
| **WhateverGreen.kext** | Intel HD 620 graphics |
| **AppleALC.kext** | Conexant CX8200 audio |
| **VoodooPS2Controller.kext** | Keyboard + Touchpad |
| **VoodooI2C.kext** + VoodooI2CHID | Wacom Touchscreen |
| **AirportItlwm.kext** | Intel AC 8265 Wi-Fi |
| **IntelBluetoothFirmware.kext** | Intel Bluetooth |
| **USBInjectAll.kext** + USBMap | USB ports |
| **SMCBatteryManager.kext** | Battery status |
| **CPUFriend.kext** | CPU power management |
| **Sinetek-rtsx.kext** | SD card reader |
| **BrightnessKeys.kext** | Brightness hotkeys |
| **ECEnabler.kext** | Embedded controller |
| **RestrictEvents.kext** | Memory warning suppression |

## 🔐 Recommended SSDTs

| SSDT | Purpose |
|------|---------|
| **SSDT-PLUG** | CPU power management |
| **SSDT-EC** | Fake EC (required for Kaby Lake) |
| **SSDT-PNLF** | Backlight control |
| **SSDT-USBX** | USB power properties |
| **SSDT-GPI0** | GPIO controller rename |
| **SSDT-XOSI** | OSI to XOSI patch |
| **SSDT-RHUB** | RHUB to XHUB rename |

## ⚠️ BIOS Settings

| Setting | Value |
|---------|-------|
| Secure Boot | **Disabled** |
| Fast Boot | **Disabled** |
| VT-x | **Enabled** |
| VT-d | **Disabled** (or add `dart=0`) |
| UEFI Boot | **Enabled** |
| Boot Order | USB first |

## 📝 Notes

- **HP Elite X2 1012 G2** is a detachable tablet/laptop with 3:2 aspect ratio 2736×1824 display with Wacom pen support
- Intel AC 8265 Wi-Fi works via **AirportItlwm** (continuous integration builds required)
- Conexant CX8200 audio requires specific **AppleALC** layout-id — experiment with layouts
- Wacom touchscreen (WCOM483E) is I2C connected; may work with **VoodooI2C** + correct GPIO pin config
- Tablet mode auto-detect and rotation may require additional SSDT patching
- The detachable keyboard connects via pogo pins hidden behind the device; ensure it's functional after boot
- The device uses a single USB-C port for charging and data; verify USB mapping carefully

---

> **Disclaimer**: Use at your own risk. This EFI configuration is provided as-is. Make sure to generate your own SMBIOS serial numbers and ROM.
