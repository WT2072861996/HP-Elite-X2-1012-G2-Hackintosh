# 🖥️ HP Elite X2 1012 G2 · OpenCore Hackintosh

**Intel Core i5-7200U · HD Graphics 620 · Kaby Lake · 2736×1824 触控屏 · OpenCore 1.0.x**

<div align="center">

![CPU](https://img.shields.io/badge/CPU-i5_7200U_Kaby_Lake-0071C5?style=flat-square)
![GPU](https://img.shields.io/badge/GPU-HD_Graphics_620-0071C5?style=flat-square)
![RAM](https://img.shields.io/badge/RAM-8_GB_LPDDR3-8B5CF6?style=flat-square)
![OpenCore](https://img.shields.io/badge/OpenCore-1.0.x-9cf?style=flat-square)
![Display](https://img.shields.io/badge/Display-2736%C3%971824_3:2-00A3E0?style=flat-square)
![Status](https://img.shields.io/badge/Status-Working-brightgreen?style=flat-square)

**[🖥️ 硬件配置](#-硬件配置) · [⚙️ BIOS 设置](#%EF%B8%8F-bios-设置) · [✅ 驱动状态](#-驱动状态) · [📦 EFI 配置](#-efi-配置) · [🚀 快速开始](#-快速开始) · [📸 截图](#-截图)**

</div>

---

## 🖥️ 硬件配置

| 组件 | 型号 | 规格 | 驱动情况 |
|:-----|:-----|:-----|:--------:|
| **型号** | HP Elite X2 1012 G2 | 二合一平板笔记本 (Detachable) | ✅ |
| **主板** | HP HP ELITE X2 1012 G2 | Sunrise Point (Kaby Lake-U) | ✅ |
| **CPU** | Intel Core i5-7200U | 2C/4T @ 2.50-3.10 GHz | ✅ 睿频正常 |
| **核显** | Intel HD Graphics 620 | 8086:5916, 24EU | ✅ 硬件加速 |
| **内存** | 板载 LPDDR3 | 8 GB | ✅ |
| **存储** | Samsung MZNLN128HAHQ-000L1 | 128 GB SATA SSD | ✅ |
| **声卡** | Conexant CX8200 | HDA: 14F1-2008 | ⚠️ 需 AppleALC |
| **Wi-Fi** | Intel Dual Band Wireless-AC 8265 | 8086-24FD | ⚠️ 需 AirportItlwm |
| **蓝牙** | Intel 无线 Bluetooth | 8087-0A2B | ⚠️ 需 IntelBluetoothFirmware |
| **触控屏** | WCOM483E (Wacom I2C) | I2C HID | ⚠️ 实验性 |
| **手写笔** | Wacom AES 2.0 | I2C | ⚠️ 实验性 |
| **键盘** | HPQ8002 | PS/2 | ✅ |
| **触控板** | ALP0110 | PS/2 | ⚠️ |
| **SD 读卡器** | Realtek 10EC-522A | PCIe | ⚠️ 需 Sinetek-rtsx |
| **指纹** | Synaptics VFS7552 | USB 138A-0092 | ❌ 不支持 |
| **LTE** | HP lt4120 Snapdragon X5 | USB 03F0-9D1D | ❌ 不支持 |
| **显示屏** | 12" 3:2 | 2736×1824 | ✅ 原生分辨率 |

---

## ✅ 驱动状态

| 功能 | 状态 | 功能 | 状态 |
|:-----|:---:|:-----|:---:|
| **HD Graphics 620 核显** | ✅ | **GPU 硬件加速** | ✅ |
| **原生分辨率 2736×1824** | ✅ | **SATA SSD** | ✅ (TRIM 支持) |
| **PS/2 键盘** | ✅ | **USB Type-C/Type-A** | ✅ |
| **CPU 睿频** | ✅ | **XCPM 电源管理** | ✅ |
| **声卡 (Conexant CX8200)** | ⚠️ | **Wi-Fi (Intel 8265)** | ⚠️ |
| **蓝牙 (Intel)** | ⚠️ | **触控板 (PS/2)** | ⚠️ |
| **触控屏 (Wacom I2C)** | ⚠️ | **手写笔** | ⚠️ |
| **SD 读卡器** | ⚠️ | **亮度调节** | ⚠️ |
| **电池状态** | ⚠️ | **睡眠/唤醒** | ⚠️ |
| **指纹传感器** | ❌ | **LTE 模块** | ❌ |
| **屏幕旋转** | ❌ | **平板模式切换** | ❌ |

---

## ⚙️ BIOS 设置

| 设置 | 值 | 说明 |
|:-----|:---:|:-----|
| **Secure Boot** | Disabled | macOS 不支持 |
| **Fast Boot** | Disabled | 避免启动问题 |
| **VT-x** | Enabled | 虚拟机支持 |
| **VT-d** | Disabled | 或添加 `dart=0` |
| **UEFI Boot** | Enabled | |
| **Boot Order** | USB 优先 | 安装时设置 |

---

## 📦 EFI 配置

### Kexts 清单

```
EFI/OC/Kexts/
├── Lilu.kext                   ✅ 内核补丁框架
├── VirtualSMC.kext             ✅ SMC 模拟
├── WhateverGreen.kext          ✅ GPU 补丁
├── AppleALC.kext               ✅ 声卡驱动
├── VoodooI2C.kext              ✅ I2C 控制器
├── VoodooI2CHID.kext           ✅ I2C HID 设备
├── VoodooPS2Controller.kext    ✅ PS/2 键盘/触控板
├── USBPorts.kext               ✅ USB 定制映射
├── SMCBatteryManager.kext      ✅ 电池传感器
├── SMCProcessor.kext           ✅ CPU 传感器
├── SMCSuperIO.kext             ✅ 风扇/温度
├── SMCLightSensor.kext         ✅ 环境光传感器
├── BrightnessKeys.kext         ✅ 亮度按键
├── ECEnabler.kext              ✅ 嵌入式控制器
├── Sinetek-rtsx.kext           ✅ SD 读卡器
└── [备用: oldConfig.plist]
```

### SSDT 热补丁

```
EFI/OC/ACPI/
├── SSDT-PLUG.aml         ✅ CPU 电源管理 (XCPM)
├── SSDT-EC.aml           ✅ EC 仿冒 (Kaby Lake 必需)
├── SSDT-PNLF.aml         ✅ 背光控制
├── SSDT-USBX.aml         ✅ USB 电源属性
├── SSDT-Battery.aml      ✅ 电池状态
├── SSDT-Sleep.aml        ✅ 睡眠修复
├── SSDT-ALS0.aml         ✅ 环境光传感器
├── SSDT-PS2.aml          ✅ PS/2 键盘
├── SSDT-FAN.aml          ✅ 风扇控制
├── SSDT-INIT.aml         ✅ 初始化补丁
├── SSDT-Debug.aml        ✅ 调试输出
├── SSDT-SMBus.aml        ✅ SMBus 支持
├── SSDT-RTC0.aml         ✅ RTC 兼容性
├── SSDT-TbtOnPch.aml     ✅ Thunderbolt 兼容
├── SSDT-TPL0.aml         ✅ TPL0 修复
├── SSDT-OsxDetect.aml    ✅ OS 检测
└── SSDT-ALS0.aml         ✅ 环境光
```

### Drivers

| Driver | 说明 |
|:-------|:----:|
| HfsPlus.efi | HFS+ 文件系统支持 |
| OpenRuntime.efi | OpenCore 运行时环境 |
| OpenCanopy.efi | 图形引导界面 |
| ResetNvramEntry.efi | NVRAM 重置入口 |

---

## 🚀 快速开始

### 1️⃣ BIOS 配置

1. 开机按 F10 进入 BIOS
2. 按上述表格配置
3. 保存退出

### 2️⃣ EFI 部署

```bash
# 挂载 USB 的 EFI 分区
diskutil list
sudo diskutil mount diskXs1

# 复制 EFI 文件夹
cp -R EFI /Volumes/EFI/

# 安装到硬盘后同样复制到硬盘 EFI 分区
```

### 3️⃣ 生成三码（重要！）

使用 GenSMBIOS 或 OCAT 生成自己的 SMBIOS 序列号，不要直接使用本仓库的三码。

### 4️⃣ 安装 macOS

1. 制作 macOS 安装 U 盘
2. 替换 U 盘 EFI 分区中的 EFI 文件夹
3. 从 USB 启动 → 选择「Install macOS」
4. 按提示完成安装（约 2-3 次重启）
5. 安装完成后将 EFI 复制到硬盘 EFI 分区

---

## 📸 截图

| 关于本机 | 显示信息 | 系统信息 |
|:--------:|:--------:|:--------:|
| ![关于本机](./Screenshots/about-this-mac.png) | ![显示](./Screenshots/display.png) | ![neofetch](./Screenshots/neofetch.png) |

---

## 🔧 注意事项

- **HP Elite X2 1012 G2** 是二合一平板笔记本，2736×1824 3:2 比例屏幕，支持 Wacom 手写笔
- Intel AC 8265 Wi-Fi 使用 **AirportItlwm** (需 ContinuousIntegration 构建版本)
- Conexant CX8200 声卡可能需要尝试多个 AppleALC layout-id
- Wacom 触控屏 (WCOM483E) 通过 I2C 连接，需配合 VoodooI2C + 正确 GPIO 引脚配置
- 键盘通过底部 Pogo Pin 连接，确保启动后键盘功能正常
- 本机仅有一个 USB-C 接口（同时用于充电和数据），请仔细核对 USB 映射
- ⚠️ **自行生成三码后再使用，不要直接使用本仓库的序列号**

---

## 📄 许可证

MIT License — 仅供学习和研究

> ⚠️ 在非 Apple 硬件上安装 macOS 可能违反 EULA

---

<p align="center">
  <b>为 Hackintosh 社区贡献 ❤️</b><br/>
  <sub>HP Elite X2 1012 G2 · OpenCore 1.0.x · 2026年</sub>
</p>
