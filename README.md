<div align="center">

# 🔥 Wild Kernel for OnePlus Pad 3 / Pad 2 Pro (SM8750) + OnePlus 12 (SM8650, custom ROM)

[![KernelSU-Next](https://img.shields.io/badge/KernelSU_Next-Supported-green)](https://kernelsu-next.github.io/webpage/)
[![KernelSU](https://img.shields.io/badge/KernelSU-Supported-green)](https://kernelsu.org/)
[![SUSFS](https://img.shields.io/badge/SUSFS-Integrated-orange?logo=gitlab)](https://gitlab.com/simonpunk/susfs4ksu)
[![Device](https://img.shields.io/badge/Device-OnePlus_Pad_3_%2F_Pad_2_Pro-blue)](https://github.com/WildKernels/OnePlus_KernelSU_SUSFS)
[![SoC](https://img.shields.io/badge/SoC-Snapdragon_8_Elite_(SM8750)-red)](https://www.qualcomm.com/products/mobile/snapdragon/smartphones/snapdragon-8-series-mobile-platforms/snapdragon-8-elite-mobile-platform)

</div>

---

## ⚠️ Disclaimer

Flashing this kernel will not void your warranty, but there is always a risk of bricking your device. Please make sure to:
- 💾 Back up your data
- 🧠 Understand the risks before proceeding

- I am **not responsible** for bricked devices, damaged hardware, or any issues that arise from using this kernel.

- **Please** do thorough research and fully understand the features added in this kernel before flashing it!

- By flashing this kernel, **YOU** are choosing to make these modifications. If something goes wrong, **do not blame me**!

<div align="center">
  
# **🚨 Proceed at your own risk!**

</div>

---

## 📱 Supported Device

<div align="center">

| Device | SoC | Kernel | Android |
|--------|-----|--------|---------|
| **OnePlus Pad 3** | Snapdragon 8 Elite (SM8750) | `6.6` | A15 / A16 |
| **OnePlus Pad 2 Pro** (CN) | Snapdragon 8 Elite (SM8750) | `6.6` | A15 / A16 |
| **OnePlus 12** (custom ROM source) | Snapdragon 8 Gen 3 (SM8650) | `6.1` | A15 / A16 |

</div>

> [!IMPORTANT]
> This builder targets the **OnePlus Pad 3 / OnePlus Pad 2 Pro (CN) (SM8750 / "sun" platform)**, plus an
> **OnePlus 12 (SM8650 / "pineapple") custom-ROM build** sourced from the community
> [OnePlus-12-Development](https://github.com/OnePlus-12-Development) kernel fork (`android_kernel_oneplus_sm8650` +
> `android_kernel_oneplus_sm8650-modules`) instead of the official OnePlusOSS source. This is intended for use on
> **custom AOSP-based ROMs** (LineageOS-family), not stock OxygenOS/ColorOS. A15 builds from the `lineage-22.2`
> split (common + modules) source; A16 builds from `lineage-23.2` on the monolithic
> `android_kernel_oneplus_sm8650` repo, which already bundles the OPlus/NXP vendor modules internally (no
> separate modules repo needed for that branch).
> The Pad 2 Pro is the China-market variant of the same hardware later released globally as the Pad 3.
> It is built from [OnePlus Official Source](https://github.com/OnePlusOSS/) and is expected to work only on **stock OxygenOS ROMs**.
> Do not flash after a major Android OTA (e.g., A15 → A16) unless verified.

---

## 🔗 Additional Resources

- 🩹 [Kernel Patches](https://github.com/zennnez/kernel_patches)
- ⚡ [Kernel Flasher](https://github.com/fatalcoder524/KernelFlasher)
- 📋 [Device Compatibility](https://github.com/zennnez/OnePlus_KernelSU_SUSFS/blob/main/compatibility.md)

---

## ✨ Features

| Feature | Description |
|---------|-------------|
| 🔐 **KernelSU / KernelSU-Next** | Root solution working in kernel mode, grants root directly in kernel space |
| 🥷 **SUSFS** | Root hiding kernel patches and userspace module for KernelSU |
| 🛡️ **BBG** | LSM-based Baseband Guard security to protect critical device partitions |
| 🛠️ **HMBIRD SCX (Fengchi)** | Scheduler extensions tuned for SM8750 (Snapdragon 8 Elite) |
| 🖧 **BBRv1 & BBRv3** | Improved TCP congestion control |
| 🚦 **CAKE and PIE qdisc** | Better network schedulers |
| ✅ **LTO (Thin)** | Link Time Optimisation for reduced binary size and improved performance |
| 🌐 **TTL Target** | Network packet TTL manipulation |
| 🧱 **IP Set & IPv6 NAT** | Advanced firewall and IPv6 NAT support |
| ⚡️ **TMPFS XATTR / POSIX ACL** | Extended TMPFS support for meta modules and Mountify |
| </> **Unicode Bypass Fix** | Prevent path traversal and Unicode detection bypasses [Experimental] |
| 🖥️ **Droidspaces** | Portable Linux container support — run full Linux environments |
| 🔃 **NTSync** | High-performance, low-latency Windows NT-compatible sync primitives |
| 🚀 **LZ4 ARMv8 NEON** | LZ4 1.10.0 with ARMv8 SIMD acceleration for ZRAM decompression |
| ⚡ **reduce_pelt** | Scheduler PELT half-life reduced 32ms → 16ms for faster CPU ramp-up (Sultan Alsawaf) |
| 🔄 **Workqueue Optimization** | Reduced lock contention on unbound workqueues — major I/O throughput gains |
| 🗜️ **ZRAM Priority Reads** | Xiaomi ZRAM optimization: read BIOs use `REQ_PRIO` for prioritized scheduling |

---

## 📦 Build Variants

<div align="center">

| Variant | Android | Kernel | Manifest |
|---------|---------|--------|----------|
| **OP-PAD-3-SM8750** (A16) | Android 16 | 6.6 (latest) | `oneplus_pad_3_sm8750_w.xml` |
| **OP-PAD-3-SM8750** (A15) | Android 15 | 6.6 (latest) | `oneplus_pad_3_sm8750_v.xml` |
| **OP-PAD-3-SM8750-6.6.30** (A15) | Android 15 | 6.6.30 | `oneplus_pad_3_sm8750_6.6.30_v.xml` |
| **OP-PAD-2-PRO** (A16) | Android 16 | 6.6 (latest) | `oneplus_pad_2_pro_w.xml` |
| **OP-PAD-2-PRO** (A15) | Android 15 | 6.6 (latest) | `oneplus_pad_2_pro_v.xml` |
| **OP12-CUSTOM** (A15, custom ROM) | Android 15 | 6.1 (`lineage-22.2`) | `oneplus_12_custom_v.xml` |
| **OP12-CUSTOM** (A16, custom ROM) | Android 16 | 6.1 (`lineage-23.2`) | `oneplus_12_custom_w.xml` |

</div>

---

## 📋 Installation Instructions

For GKI installation, please follow the official guide:

📖 **[KernelSU Installation Guide](https://kernelsu.org/guide/installation.html)**

You can also find installation instructions in the release notes.

---

## 🌟 Special Thanks

**These amazing people help make this project possible! ❤️**

<div align="center">

| 🔧 **Project** | 👨‍💻 **Developer** | 🔗 **Link** |
|:---------------:|:----------------:|:-----------:|
| **KernelSU** | tiann | [![GitHub](https://img.shields.io/badge/GitHub-tiann-blue?style=flat-square&logo=github)](https://github.com/tiann/KernelSU) |
| **KernelSU-Next** | rifsxd | [![GitHub](https://img.shields.io/badge/GitHub-rifsxd-blue?style=flat-square&logo=github)](https://github.com/KernelSU-Next/KernelSU-Next) |
| **Magic-KSU** | 5ec1cff | [![GitHub](https://img.shields.io/badge/GitHub-5ec1cff-blue?style=flat-square&logo=github)](https://github.com/5ec1cff/KernelSU) |
| **SUSFS** | simonpunk | [![GitLab](https://img.shields.io/badge/GitLab-simonpunk-orange?style=flat-square&logo=gitlab)](https://gitlab.com/simonpunk/susfs4ksu.git) |
| **SUSFS Module** | sidex15 | [![GitHub](https://img.shields.io/badge/GitHub-sidex15-blue?style=flat-square&logo=github)](https://github.com/sidex15) |
| **Sultan Kernels** | kerneltoast | [![GitHub](https://img.shields.io/badge/GitHub-kerneltoast-blue?style=flat-square&logo=github)](https://github.com/kerneltoast) |
| **Baseband Guard** | vc-teahouse | [![GitHub](https://img.shields.io/badge/GitHub-vc--teahouse-blue?style=flat-square&logo=github)](https://github.com/vc-teahouse/Baseband-guard.git) |
| **Droidspaces** | ravindu644 | [![GitHub](https://img.shields.io/badge/GitHub-ravindu644-blue?style=flat-square&logo=github)](https://github.com/ravindu644/Droidspaces-OSS.git) |
| **reduce_pelt patch** | Sultan Alsawaf | [![GitHub](https://img.shields.io/badge/GitHub-kerneltoast-blue?style=flat-square&logo=github)](https://github.com/kerneltoast) |
| **LZ4 ARMv8 patch** | DogEZ | [![GitHub](https://img.shields.io/badge/GitHub-DogEZ-blue?style=flat-square&logo=github)](https://github.com/dogez) |

</div>

*If you have contributed and are not listed here, please remind me!* 🙏

---

## 💬 Support

If you encounter any issues or need help, feel free to:
- 🐛 Open an issue in this repository
- 💬 Reach out via Telegram

---

## 📱 Connect With Us

<div align="center">
  
[![Telegram](https://img.shields.io/badge/Telegram-zennnez-blue?logo=telegram)](https://t.me/zennnez)
[![WildKernels Telegram Group](https://img.shields.io/badge/Telegram-WildKernels-blue?logo=telegram)](https://t.me/WildKernelsTG)

</div>

---

## 💝 Donations

Any and all donations are appreciated!

PayPal: [paypal.me/fatalcoder524](https://paypal.me/fatalcoder524) | [paypal.me/zebrazenpai](https://paypal.me/zebrazenpai)

DM on Telegram for UPI donations!
