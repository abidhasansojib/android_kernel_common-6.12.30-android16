# Android 16 GKI Common Kernel (6.12.30-android16)

[![Android](https://img.shields.io/badge/Android-16-blue?logo=android&logoColor=white)](https://android.googlesource.com/)
[![Kernel Version](https://img.shields.io/badge/Kernel-6.12.30-red?logo=linux&logoColor=white)](https://kernel.org/)
[![Sublevel](https://img.shields.io/badge/Sublevel-30-orange)](https://kernel.org/)
[![Patch Level](https://img.shields.io/badge/SPL-2025--07-success)](https://source.android.com/docs/security/bulletin)
[![Tag](https://img.shields.io/badge/Tag-v6.12.30--android16-brightgreen?logo=git)](https://github.com/abidhasansojib/android_kernel_common-6.12.30-android16/releases/tag/v6.12.30-android16)
[![Builder](https://img.shields.io/badge/Built_With-gki__kernel__builder-purple?logo=github)](https://github.com/abidhasansojib/gki_kernel_builder)

This repository provides the standalone Android 16 Generic Kernel Image (GKI) common kernel source tree based on Linux **6.12.30** (`6.12.30-android16`, OS Patch Level `2025-07`), designed for development, inspection, and compilation workflows with [gki_kernel_builder](https://github.com/abidhasansojib/gki_kernel_builder).

---

## 🎯 Target Kernel Specifications

| Specification | Value | Details |
| :--- | :--- | :--- |
| **Android Version** | `Android 16` (`android16`) | AOSP Generic Kernel Image (GKI) architecture |
| **Linux Kernel Version** | `6.12.30` | Linux LTS base release |
| **Release Target** | `6.12.30-android16` | Canonical GKI release string |
| **Kernel Sublevel** | `30` | Validated against OEM vendor module sublevel checks |
| **OS Patch Level (SPL)** | `2025-07` | Synchronized with July 2025 AOSP security bulletins |
| **AOSP Superproject Branch** | `common-android16-6.12-2025-07` | Upstream AOSP kernel manifest branch |
| **Upstream Base Commit** | [`eed0fa659bd0`](https://android.googlesource.com/kernel/common/+/eed0fa659bd00244386a3cfaa70b680a8b04c59f) | Pinned `kernel/common` upstream revision |
| **Upstream Source** | [`https://android.googlesource.com/kernel/common`](https://android.googlesource.com/kernel/common) | Official Google Android Common Kernel repository |
| **Target Architecture** | `arm64` (`aarch64`) | 64-bit ARM architecture |
| **Primary Tested Device** | **Redmi Note 14 4G (`tanzanite`)** | MediaTek Helio G99 (`MT6789`) on Xiaomi HyperOS 3 |

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

## 🏗️ Integration with `gki_kernel_builder`

This kernel source tree matches the configuration expected by [gki_kernel_builder](https://github.com/abidhasansojib/gki_kernel_builder), which automates:
* **Root Flavors**: SukiSU-Ultra (Default), KernelSU-Next, and ReSukiSU.
* **Stealth & Isolation**: In-tree SUSFS v2.3.0 and NoMount metamodule.
* **Kali NetHunter**: Monitor mode, packet injection, BadUSB HID (`/dev/hidg1` keyboard, `/dev/hidg2` mouse), SDR, and SocketCAN.
* **Vendor Version Bypass**: Integrated vendor module version-check bypass hack (`bad_version: return 1;`).

---

<details>
<summary><b>📜 Upstream Android Common Kernel Patch Guidelines (Click to Expand)</b></summary>
<br>

### How do I submit patches to Android Common Kernels

1. BEST: Make all of your changes to upstream Linux. If appropriate, backport to the stable releases.
   These patches will be merged automatically in the corresponding common kernels. If the patch is already
   in upstream Linux, post a backport of the patch that conforms to the patch requirements below.
   - Do not send patches upstream that contain only symbol exports. To be considered for upstream Linux,
     additions of `EXPORT_SYMBOL_GPL()` require an in-tree modular driver that uses the symbol -- so include
     the new driver or changes to an existing driver in the same patchset as the export.
   - When sending patches upstream, the commit message must contain a clear case for why the patch
     is needed and beneficial to the community. Enabling out-of-tree drivers or functionality is not
     a persuasive case.

2. LESS GOOD: Develop your patches out-of-tree (from an upstream Linux point-of-view). Unless these are
   fixing an Android-specific bug, these are very unlikely to be accepted unless they have been
   coordinated with kernel-team@android.com. If you want to proceed, post a patch that conforms to the
   patch requirements below.

### Common Kernel patch requirements

- All patches must conform to the Linux kernel coding standards and pass `scripts/checkpatch.pl`
- Patches shall not break gki_defconfig or allmodconfig builds for arm, arm64, x86, x86_64 architectures
- If the patch is not merged from an upstream branch, the subject must be tagged with the type of patch:
  `UPSTREAM:`, `BACKPORT:`, `FROMGIT:`, `FROMLIST:`, or `ANDROID:`.
- All patches must have a `Change-Id:` tag
- If an Android bug has been assigned, there must be a `Bug:` tag.
- All patches must have a `Signed-off-by:` tag by the author and the submitter

</details>
