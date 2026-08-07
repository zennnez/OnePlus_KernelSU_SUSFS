# Compatibility Information: OnePlus Pad 3 / Pad 2 Pro

## 1. Primary Supported Devices

| Device Name | Platform / Codename | SoC | Kernel Version | Supported OS Versions |
|---|---|---|---|---|
| **OnePlus Pad 3** | `SM8750` / `sun` | Snapdragon 8 Elite | `6.6.x` | Android 15 (OxygenOS 15) <br> Android 16 (OxygenOS 16) |
| **OnePlus Pad 2 Pro** (CN) | `SM8750` / `sun` | Snapdragon 8 Elite | `6.6.x` | Android 15 (ColorOS 15) <br> Android 16 (ColorOS 16) |
| **OnePlus 12** (custom ROM) | `SM8650` / `pineapple` | Snapdragon 8 Gen 3 | `6.1.x` | Android 15 (LineageOS 22.2) <br> Android 16 (LineageOS 23.2) |

> [!NOTE]
> All kernels are compiled directly using official [OnePlusOSS](https://github.com/OnePlusOSS) kernel source manifests (`android_kernel_common_oneplus_sm8750` & `android_kernel_modules_and_devicetree_oneplus_sm8750`), using the device-specific `pad_3` / `pad_2_pro` source branches.
>
> The OnePlus Pad 2 Pro (CN) is the same SM8750/"sun" hardware later sold globally as the OnePlus Pad 3, but ships its own OnePlusOSS kernel source branch (ColorOS-based) rather than sharing the Pad 3 branch — so it is built as a separate config/manifest pair.
>
> The **OnePlus 12 (custom ROM)** entry is different from every other device here: instead of the official
> [OnePlusOSS](https://github.com/OnePlusOSS) source, it builds from the community
> [OnePlus-12-Development](https://github.com/OnePlus-12-Development) fork (`android_kernel_qcom_sm8650` for the
> common/GKI kernel, `android_kernel_oneplus_sm8650-modules` for vendor modules/devicetree), on the `lineage-22.2`
> branch (A15) or the monolithic `android_kernel_oneplus_sm8650` repo on `lineage-23.2` (A16, which already
> bundles the vendor modules, so no separate modules project is needed for that branch). It is meant for
> flashing on **custom AOSP-based ROMs** (LineageOS-family), not on stock OxygenOS/ColorOS.

---

## 2. Integrated Feature Matrix & Compatibility

The kernel for OnePlus Pad 3 includes the following built-in optimizations and features:

| Feature / Patch | Status | Details |
|---|---|---|
| **KernelSU / KernelSU-Next** | ✅ Integrated | Full inline KernelSU support |
| **SUSFS** | ✅ Integrated | Kernel-level root hiding mechanisms (`v2.2.0` patch set) |
| **HMBIRD SCX (Fengchi)** | ✅ Enabled | SM8750-tuned scheduler extensions |
| **BBR & BBRv3** | ✅ Enabled | Advanced TCP congestion control algorithms |
| **Baseband Guard (BBG)** | ✅ Enabled | Critical partition protection |
| **NTSync** | ✅ Enabled | Low-latency synchronization primitives |
| **Droidspaces** | ✅ Enabled | Support for running full Linux containers |
| **LZ4 ARMv8 Acceleration** | ✅ Enabled | NEON SIMD accelerated LZ4 compression/decompression |
| **Workqueue Lock Reduction** | ✅ Enabled | Improved I/O throughput on multi-threaded workqueues |
| **ZRAM Priority Reads** | ✅ Enabled | Prioritized ZRAM read BIO handling (`REQ_PRIO`) |
| **reduce_pelt** | ✅ Enabled | 16ms PELT half-life tuning for fast CPU frequency ramp-up |

---

## 3. Important Flashing Guidelines

1. **Stock ROM Requirement**: Flashing is recommended on stock OxygenOS / ColorOS firmware.
2. **Major Version OTAs**: Before updating across major Android releases (e.g. A15 → A16), ensure you flash the matching kernel build variant (`OP-PAD-3-SM8750` A15 vs A16).
3. **Backup Recommendation**: Always keep a backup of your stock `boot.img` / `init_boot.img` before applying any custom kernel zip via recovery or KernelFlasher.
