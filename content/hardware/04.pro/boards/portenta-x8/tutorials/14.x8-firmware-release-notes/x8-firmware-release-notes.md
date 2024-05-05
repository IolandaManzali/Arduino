---
title: '14. Portenta X8 Firmware Release Notes'
difficulty: beginner
tags: [Linux, containers, factories, foundries]
description: 'This article contains release notes of the existing Portenta X8 firmwares.'
author: Taddy Ho Chung
hardware:
  - hardware/04.pro/board/portenta-x8

---

# Firmware Release Notes

The present document provides detailed release notes for each firmware version of the Portenta X8. Explore the changes, improvements, and fixes for the released firmware.

## Hardware and Software Requirements

Supported Device:

- [Portenta X8](https://store.arduino.cc/portenta-x8)

Compatible carriers with the supported device:

- [Portenta Breakout board](https://store.arduino.cc/portenta-breakout)
- [Portenta Max Carrier](http://store.arduino.cc/portenta-max-carrier)
- [Portenta Hat Carrier](https://store.arduino.cc/products/portenta-hat-carrier)

# Firmware Versions
The following section highlights the critical updates and enhancements introduced in the latest firmware version. It presents the most significant progress and optimizations implemented to improve performance, enhance user experience, and strengthen security.

## Latest Firmware Version: __822__

The listing herein offers a glimpse into the Portenta X8 firmware's continuous improvement and enhancement. You can expect a concise overview of the integrated key new features, major bug fixes, and critical security patches to ensure the highest level of functionality and performance within the Portenta X8 system.

* **New Features:**
- Added `libgpiod` to enhance functionality across both software images.
- Introduced support for **EC200A-EU** in *ModemManager*, expanding compatibility.

* **Enhancements:**
- Enhanced *ModemManager* scripts to manage USB modem power cycles more effectively using `gpiod`.
- Implemented the `aklite-offline` run command post-update for streamlined offline operations.

* **Bug Fixes:**
- Resolved an issue where the U-Boot environment in RAM was inadvertently modified even when `carrier_custom` was set to **1**.

* **Security Updates:**
- Decided against integrating SE05x support in *lmp-base* to maintain security standards.

* **Additional Notes:**
- Disabled the PCIe connector by default and removed the `sara-r4` overlay to simplify device tree configurations.
- Downgraded CAN and (X8H7) in general to align with arduino-88.91 specifications (tag: 746-portenta-x8) due to regression issues stemming from new Linux driver/firmware updates.

***__You can access the latest version of the firmware [here](https://downloads.arduino.cc/portentax8image/image-latest.tar.gz).__***

## Available Firmware Versions

Below is a list of all available firmware versions with their release notes.

### OS Image 822

<details>
  <summary><strong>OS Image 822: Release arduino-88.94</strong></summary>

#### New Features
  - Added `libgpiod` to enhance functionality across both software images.
  - Introduced support for **EC200A-EU** in *ModemManager*, expanding compatibility.

#### Enhancements
  - Enhanced *ModemManager* scripts to manage USB modem power cycles more effectively using `gpiod`.
  - Implemented the `aklite-offline` run command post-update for streamlined offline operations.

#### Bug Fixes
  - Resolved an issue where the U-Boot environment in RAM was inadvertently modified even when `carrier_custom` was set to **1**.

#### Security Updates
  - Decided against integrating SE05x support in *lmp-base* to maintain security standards.

#### Additional Notes
  - Disabled the PCIe connector by default and removed the `sara-r4` overlay to simplify device tree configurations.
  - Downgraded CAN and (X8H7) in general to align with arduino-88.91 specifications (tag: 746-portenta-x8) due to regression issues stemming from new Linux driver/firmware updates.
  - Based on [LmP v88](https://foundries.io/products/releases/88/). It is based on the Yocto manifest. For docker-compose apps, check out [here](https://github.com/arduino/portenta-containers/tree/release).

</details>
<br></br>

### OS Image 746

<details>
  <summary><strong>OS Image 746: Release arduino-88.91</strong></summary>

#### New Features
  - Added the Portenta HAT Carrier support
  - Added experimental support for Ditto

#### Enhancements
  - Improved bridge implementation (X8H7)

#### Bug Fixes
  - _u-boot env_ accessible in devel images
  - Patches for CAN bus protocol

#### Security Updates
  - Security patches and updates to enhance protection.

#### Additional Notes
  - Based on [LmP v88](https://foundries.io/products/releases/88/). It is based on the Yocto manifest. For docker-compose apps, check out [here](https://github.com/arduino/portenta-containers/tree/release).

</details>
<br></br>


### OS Image 719
<details>
  <summary><strong>OS Image 719: Release arduino-88.7</strong></summary>

#### New Features
  - Added PWM fan support
  - Added Pika Spark support
  - Experimental support for RPi v3.0 (imx708) (V4L2, I2C)
  - Support Bayer bggr 10-bit in bsp, courtesy of NXP (Weiping Liu) (V4L2, GSTREAMER)

#### Enhancements
  - Improved RPi v1.3 (ov5647_mipi) and reaching 30fps (V4L2, I2C)
  - Improved RPi v2.1 (imx219) (V4L2, I2C)

#### Bug Fixes
  - Patches CAN bus TX issues

#### Additional Notes
  - Based on [LmP v88](https://foundries.io/products/releases/88/). This is based on the Yocto manifest. For docker-compose apps, check out [here](https://github.com/arduino/portenta-containers/tree/release).

</details>
<br></br>

For instructions on how to install or upgrade to the latest firmware version, you can use the [Portenta X8 Out-of-the-box](https://docs.arduino.cc/tutorials/portenta-x8/user-manual#out-of-the-box-experience) or [flash it manually](https://docs.arduino.cc/tutorials/portenta-x8/user-manual#update-using-uuu-tool) downloading the newest version directly from this [link](https://downloads.arduino.cc/portentax8image/image-latest.tar.gz).
