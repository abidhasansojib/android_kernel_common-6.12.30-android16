# Android 16 GKI Common Kernel (6.12.30-android16)

[![Android](https://img.shields.io/badge/Android-16-blue?logo=android&logoColor=white)](https://android.googlesource.com/)
[![Kernel Version](https://img.shields.io/badge/Kernel-6.12.30-red?logo=linux&logoColor=white)](https://kernel.org/)
[![Sublevel](https://img.shields.io/badge/Sublevel-30-orange)](https://kernel.org/)
[![Patch Level](https://img.shields.io/badge/SPL-2025--07-success)](https://source.android.com/docs/security/bulletin)
[![Tag](https://img.shields.io/badge/Tag-v6.12.30--android16-brightgreen?logo=git)](https://github.com/abidhasansojib/android_kernel_common-6.12.30-android16/releases/tag/v6.12.30-android16)
[![Builder](https://img.shields.io/badge/Built_With-gki__kernel__builder-purple?logo=github)](https://github.com/abidhasansojib/gki_kernel_builder)

This repository contains the standalone Android 16 Generic Kernel Image (GKI) common kernel source tree based on Linux **6.12.30** (`6.12.30-android16`, OS Patch Level `2025-07`).

---

## 🎯 Kernel Specifications

| Specification | Value | Details |
| :--- | :--- | :--- |
| **Android Version** | `Android 16` (`android16`) | AOSP Generic Kernel Image (GKI) standard |
| **Linux Kernel Version** | `6.12.30` | Linux LTS baseline |
| **Target Build Release** | `6.12.30-android16` | Canonical release identifier |
| **Kernel Sublevel** | `30` | Validated against OEM vendor module sublevel checks |
| **OS Patch Level (SPL)** | `2025-07` | Synchronized with July 2025 AOSP security bulletins |
| **Upstream Source (Tree)** | [`kernel/common @ eed0fa659bd0`](https://android.googlesource.com/kernel/common/+/eed0fa659bd00244386a3cfaa70b680a8b04c59f) | Direct GoogleSource source tree for Linux 6.12.30 |
| **AOSP Superproject Branch** | [`common-android16-6.12-2025-07`](https://android.googlesource.com/kernel/superproject/+/refs/heads/common-android16-6.12-2025-07) | Upstream AOSP superproject branch |
| **AOSP Kernel Manifest Branch** | [`kernel/manifest (2025-07)`](https://android.googlesource.com/kernel/manifest/+/refs/heads/common-android16-6.12-2025-07) | Official manifest branch used by `repo init` |
| **AOSP Common Tag** | [`android16-6.12.30_r00`](https://android.googlesource.com/kernel/common/+/refs/tags/android16-6.12.30_r00) | Official Android 16 6.12.30 release tag |
| **Target Architecture** | `arm64` (`aarch64`) | 64-bit ARM architecture |
| **Primary Tested Device** | **Redmi Note 14 4G (`tanzanite`)** | MediaTek MT6789 (Helio G99) on Xiaomi HyperOS 3 |

---

## 📥 Cloning the Kernel Source

To clone the source repository shallowly without ancient commit history:

```bash
# Clone the main branch
git clone --depth=1 https://github.com/abidhasansojib/android_kernel_common-6.12.30-android16.git common

# Or clone the specific release tag
git clone --depth=1 --branch v6.12.30-android16 https://github.com/abidhasansojib/android_kernel_common-6.12.30-android16.git common
```

---

## 🏗️ Usage with `gki_kernel_builder`

This kernel source is designed to be built with [gki_kernel_builder](https://github.com/abidhasansojib/gki_kernel_builder), which provides:
* **Root Flavors**: SukiSU-Ultra (Default), KernelSU-Next, and ReSukiSU.
* **Stealth & Isolation**: In-tree SUSFS v2.3.0 and NoMount metamodule.
* **Kali NetHunter**: Wireless drivers (75+ Wi-Fi adapters), BadUSB HID (`/dev/hidg1` keyboard, `/dev/hidg2` mouse), SDR, and SocketCAN.
* **Vendor Bypass**: Built-in vendor module version-check bypass hack (`bad_version: return 1;`).

---

## 📜 Upstream Patch Guidelines

The original AOSP kernel patch submission requirements and guidelines are preserved in [**SUBMITTING_PATCHES.md**](SUBMITTING_PATCHES.md).
