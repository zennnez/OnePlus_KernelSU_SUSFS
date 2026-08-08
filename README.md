<div align="center">

# ⚡ Knockout Kernels — OnePlus GKI Kernel Builder

### For OnePlus Pad 3 · Pad 2 Pro (SM8750) · OnePlus 12 (SM8650, custom ROM)

[![SukiSU-Ultra](https://img.shields.io/badge/SukiSU_Ultra-Supported-blueviolet?logo=github)](https://github.com/SukiSU-Ultra/SukiSU-Ultra)
[![ReSukiSU](https://img.shields.io/badge/ReSukiSU-Supported-blue?logo=github)](https://github.com/ReSukiSU/ReSukiSU)
[![KernelSU-Next](https://img.shields.io/badge/KernelSU_Next-Supported-brightgreen?logo=github)](https://kernelsu-next.github.io/webpage/)
[![KernelSU](https://img.shields.io/badge/KernelSU-Supported-green?logo=github)](https://kernelsu.org/)
[![SUSFS](https://img.shields.io/badge/SUSFS-Integrated-orange?logo=gitlab)](https://gitlab.com/simonpunk/susfs4ksu)
[![ZeroMount](https://img.shields.io/badge/ZeroMount-Enabled-purple)](https://github.com/Enginex0/zeromount)
[![SoC](https://img.shields.io/badge/SoC-SM8750_%2F_SM8650-red)](https://www.qualcomm.com/)

*Based on the [WildKernels](https://github.com/WildKernels/OnePlus_KernelSU_SUSFS) build pipeline — extended, enhanced, and rebranded as Knockout Kernels.*

</div>

---

## ⚠️ Disclaimer

Flashing this kernel will not void your warranty, but there is always a risk of bricking your device. Please make sure to:

- 💾 Back up your data before flashing
- 🧠 Fully read and understand what each feature does

**I am not responsible for bricked devices, data loss, or any damage caused by using this kernel. By flashing, YOU accept all responsibility.**

<div align="center">

# 🚨 Proceed at your own risk!

</div>

---

## 📱 Supported Devices

<div align="center">

| Device | SoC / Platform | Kernel | Android |
|--------|---------------|--------|---------|
| **OnePlus Pad 3** | SM8750 / `sun` | `6.6.x` | A15 · A16 |
| **OnePlus Pad 2 Pro** (CN) | SM8750 / `sun` | `6.6.x` | A15 · A16 |
| **OnePlus 12** (custom ROM) | SM8650 / `pineapple` | `6.1.x` | A15 · A16 |

</div>

> [!IMPORTANT]
> **OnePlus Pad 3 / Pad 2 Pro** are built from the official [OnePlusOSS](https://github.com/OnePlusOSS) kernel source
> manifests and are intended for **stock OxygenOS / ColorOS** firmware. The Pad 2 Pro is the CN-market
> hardware identical to the Pad 3 but ships under its own ColorOS branch.
>
> **OnePlus 12 (custom ROM)** builds from the community [OnePlus-12-Development](https://github.com/OnePlus-12-Development)
> fork (`android_kernel_oneplus_sm8650` + `android_kernel_oneplus_sm8650-modules`). A15 uses `lineage-22.2`
> (common + modules split); A16 uses the monolithic `lineage-23.2` branch. Intended for **LineageOS-family custom ROMs only** — **do not** flash on stock OxygenOS.
>
> Do **not** flash across major Android versions (e.g. A15 → A16) without using the matching build variant.

---

## ✨ Features

| Feature | Description | Devices |
|---------|-------------|---------|
| 🔐 **KernelSU / KernelSU-Next** | Kernel-mode root with full GKI inline hooks | All |
| 🥷 **SUSFS** | Kernel-level root hiding — `sus_path`, `sus_mount`, `sus_kstat`, `open_redirect`, `sus_map` | All |
| 🥷 **Enhanced SUSFS (51_)** | Additional SUSFS extensions: kstat redirect, unicode filter, buffer overread hardening | All |
| 👻 **ZeroMount VFS** | Mountless VFS file injection and path redirection via bloom-filter ioctl engine | A16 (OP12, Pad2Pro) |
| 🛡️ **BBG** | LSM-based Baseband Guard — protects critical partitions (`efisp`, `abl`) from modification | All |
| 🛠️ **HMBIRD SCX (Fengchi)** | SM8750-tuned scheduler extensions (`SCHED_EXT`) for elite core scheduling | SM8750 only |
| 🖧 **BBRv1 & BBRv3** | Google's Bottleneck Bandwidth and RTT TCP congestion control | All |
| 🌐 **TTL Target** | iptables TTL manipulation for tethering and VPN bypass setups | All |
| 🧱 **IP_SET & IPv6 NAT** | Advanced firewall with IP sets and full IPv6 NAT support | All |
| 🖥️ **Droidspaces** | Portable Linux namespace containers — run full Linux distros on device | All |
| 🖥️ **Droidspaces Extended** | EVDI DRM + cgroup fixes for desktop-grade Linux container workloads | All |
| 🔃 **NTSync** | Windows NT-compatible sync primitives for Wine/Proton/DXVK compatibility | All |
| ⚡ **reduce_pelt** | PELT half-life tuned 32ms → 16ms for faster CPU frequency ramp-up (Sultan Alsawaf) | All |
| 🔄 **Workqueue Optimisation** | Reduced lock contention on unbound workqueues for I/O throughput | All |
| 🗜️ **ZRAM Priority Reads** | ZRAM read BIOs issued with `REQ_PRIO` for scheduler priority | All |
| 🚀 **LZ4 ARMv8 NEON** | LZ4 1.10.0 with ARMv8 SIMD acceleration for ZRAM decompression | All |
| ✅ **LTO Thin** | Link Time Optimisation — smaller binary, improved inlining across translation units | All |
| 🔮 **LLVM POLLY** | Polyhedral loop optimisation for compute-heavy kernel paths (A16) | A16 |
| 💾 **ZRAM Writeback** | Writeback cold ZRAM pages to flash to reclaim DRAM (A16) | A16 |
| 🔧 **Unicode Bypass Fix** | Prevents path traversal and Unicode detection bypasses | All |
| 🔑 **KALLSYMS_ALL** | Full kernel symbol export for advanced KSU/SUSFS/ZeroMount internals | All |

---

## 📦 Build Variants

<div align="center">

| Config | Device | Android | Kernel | Source | Features |
|--------|--------|---------|--------|--------|----------|
| **OP-PAD-3-SM8750** | OnePlus Pad 3 | A16 | 6.6 (latest) | OnePlusOSS | Full (+ POLLY, ZRAM WB) |
| **OP-PAD-3-SM8750** | OnePlus Pad 3 | A15 | 6.6 (latest) | OnePlusOSS | Full |
| **OP-PAD-3-SM8750-6.6.30** | OnePlus Pad 3 | A15 | 6.6.30 (pinned) | OnePlusOSS | Full |
| **OP-PAD-2-PRO** | OnePlus Pad 2 Pro (CN) | A16 | 6.6 (latest) | OnePlusOSS | Full + ZeroMount |
| **OP-PAD-2-PRO** | OnePlus Pad 2 Pro (CN) | A15 | 6.6 (latest) | OnePlusOSS | Full |
| **OP12-CUSTOM** | OnePlus 12 (custom ROM) | A16 | 6.1 (`lineage-23.2`) | OnePlus-12-Dev | Full + ZeroMount |
| **OP12-CUSTOM** | OnePlus 12 (custom ROM) | A15 | 6.1 (`lineage-22.2`) | OnePlus-12-Dev | Full |

</div>

---

## 🔗 Resources

- 🩹 [Kernel Patches](https://github.com/zennnez/kernel_patches)
- ⚡ [Kernel Flasher](https://github.com/fatalcoder524/KernelFlasher)
- 📋 [Device Compatibility](compatibility.md)
- 👻 [ZeroMount](https://github.com/Enginex0/zeromount)
- 🔧 [Super-Builders Patch Suite](https://github.com/Enginex0/Super-Builders)

---

## 📋 Installation

For GKI installation, follow the official guide:

📖 **[KernelSU Installation Guide](https://kernelsu.org/guide/installation.html)**

Release notes for each build contain flash instructions specific to that device/variant.

---

## 🌟 Credits & Special Thanks

**Knockout Kernels is built on the shoulders of giants. ❤️**

> [!NOTE]
> The build pipeline, manifest infrastructure, and patch framework are **based on [WildKernels](https://github.com/WildKernels/OnePlus_KernelSU_SUSFS)** by **zennnez**. Without their foundational work this project would not exist. Full credit and thanks go to them.

<div align="center">

| 🔧 Project | 👨‍💻 Author | 🔗 Link |
|:----------:|:---------:|:-------:|
| **WildKernels** *(base pipeline)* | zennnez | [![GitHub](https://img.shields.io/badge/GitHub-zennnez-blue?style=flat-square&logo=github)](https://github.com/WildKernels/OnePlus_KernelSU_SUSFS) |
| **KernelSU-Next** | rifsxd | [![GitHub](https://img.shields.io/badge/GitHub-rifsxd-blue?style=flat-square&logo=github)](https://github.com/KernelSU-Next/KernelSU-Next) |
| **KernelSU** | tiann | [![GitHub](https://img.shields.io/badge/GitHub-tiann-blue?style=flat-square&logo=github)](https://github.com/tiann/KernelSU) |
| **SUSFS** | simonpunk | [![GitLab](https://img.shields.io/badge/GitLab-simonpunk-orange?style=flat-square&logo=gitlab)](https://gitlab.com/simonpunk/susfs4ksu) |
| **SUSFS Module** | sidex15 | [![GitHub](https://img.shields.io/badge/GitHub-sidex15-blue?style=flat-square&logo=github)](https://github.com/sidex15) |
| **ZeroMount** | Enginex0 | [![GitHub](https://img.shields.io/badge/GitHub-Enginex0-blue?style=flat-square&logo=github)](https://github.com/Enginex0/zeromount) |
| **Super-Builders** | Enginex0 | [![GitHub](https://img.shields.io/badge/GitHub-Enginex0-blue?style=flat-square&logo=github)](https://github.com/Enginex0/Super-Builders) |
| **Baseband Guard** | vc-teahouse | [![GitHub](https://img.shields.io/badge/GitHub-vc--teahouse-blue?style=flat-square&logo=github)](https://github.com/vc-teahouse/Baseband-guard) |
| **Droidspaces** | ravindu644 | [![GitHub](https://img.shields.io/badge/GitHub-ravindu644-blue?style=flat-square&logo=github)](https://github.com/ravindu644/Droidspaces-OSS) |
| **Sultan Kernels** | kerneltoast | [![GitHub](https://img.shields.io/badge/GitHub-kerneltoast-blue?style=flat-square&logo=github)](https://github.com/kerneltoast) |
| **LZ4 ARMv8 patch** | DogEZ | [![GitHub](https://img.shields.io/badge/GitHub-DogEZ-blue?style=flat-square&logo=github)](https://github.com/dogez) |
| **Kernel Patches** | zennnez | [![GitHub](https://img.shields.io/badge/GitHub-zennnez-blue?style=flat-square&logo=github)](https://github.com/zennnez/kernel_patches) |

</div>

*If you've contributed and aren't listed, please open an issue or reach out!* 🙏

---

## 💬 Support

- 🐛 Open an issue in this repository
- 💬 Reach out via Telegram

<div align="center">

[![Telegram](https://img.shields.io/badge/Telegram-zennnez-blue?logo=telegram)](https://t.me/zennnez)

</div>

---

## 💝 Donations

Any and all donations are appreciated!

PayPal: [paypal.me/zebrazenpai](https://paypal.me/zebrazenpai)

DM on Telegram for UPI donations!
