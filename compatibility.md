# Knockout Kernels — Compatibility Guide

> Based on the [WildKernels](https://github.com/WildKernels/OnePlus_KernelSU_SUSFS) pipeline, extended with ZeroMount VFS, enhanced SUSFS, KSU safety patches, and more.

---

## 1. Supported Devices

| Device | Platform / Codename | SoC | Kernel | Supported OS |
|--------|---------------------|-----|--------|-------------|
| **OnePlus Pad 3** | `SM8750` / `sun` | Snapdragon 8 Elite | `6.6.x` | Android 15 (OxygenOS 15) · Android 16 (OxygenOS 16) |
| **OnePlus Pad 2 Pro** (CN) | `SM8750` / `sun` | Snapdragon 8 Elite | `6.6.x` | Android 15 (ColorOS 15) · Android 16 (ColorOS 16) |
| **OnePlus 12** (custom ROM) | `SM8650` / `pineapple` | Snapdragon 8 Gen 3 | `6.1.x` | Android 15 (LineageOS 22.2) · Android 16 (LineageOS 23.2) |

> [!NOTE]
> **OnePlus Pad 3 / Pad 2 Pro** are built from official [OnePlusOSS](https://github.com/OnePlusOSS) kernel source
> manifests (`android_kernel_common_oneplus_sm8750` + `android_kernel_modules_and_devicetree_oneplus_sm8750`).
> The Pad 2 Pro (CN) is the same SM8750/"sun" hardware shipped as the Pad 3 globally, but with its own
> ColorOS-based kernel branch — built as a separate config/manifest pair.
>
> **OnePlus 12 (custom ROM)** builds from the community [OnePlus-12-Development](https://github.com/OnePlus-12-Development)
> fork. A15 uses `lineage-22.2` (split: common + modules repos). A16 uses the monolithic `lineage-23.2`
> branch (vendor modules are bundled — no separate modules repo needed). Flash **only on LineageOS-family custom ROMs**.

---

## 2. Feature Matrix by Device & OS

### Legend
| Symbol | Meaning |
|--------|---------|
| ✅ | Enabled in all builds of this device |
| 🔵 | Enabled in A16 builds only |
| ❌ | Not applicable / disabled for this device |
| ⚠️ | Present but experimental |

### OnePlus Pad 3 (SM8750 / `sun`)

| Feature | A15 | A16 | Notes |
|---------|-----|-----|-------|
| KernelSU / KernelSU-Next | ✅ | ✅ | Inline GKI hooks |
| SUSFS | ✅ | ✅ | Full `sus_path`, `sus_mount`, `sus_kstat`, `open_redirect`, `sus_map` |
| Enhanced SUSFS (51_) | ✅ | ✅ | Kstat redirect, unicode filter, buffer hardening |
| ZeroMount VFS | ❌ | ✅ | VFS path injection, bloom filter ioctl engine |
| KSU Safety (70_) | ✅ | ✅ | Null-termination, UID range, zygote guard fixes |
| HMBIRD SCX (Fengchi) | ✅ | ✅ | SM8750 SCHED_EXT scheduler extensions |
| Baseband Guard (BBG) | ✅ | ✅ | Critical partition LSM protection |
| BBRv1 & BBRv3 | ✅ | ✅ | TCP congestion control |
| TTL Target | ✅ | ✅ | Packet TTL iptables target |
| IP_SET & IPv6 NAT | ✅ | ✅ | Advanced firewall ruleset support |
| Droidspaces | ✅ | ✅ | Linux namespace containers |
| Droidspaces Extended | ✅ | ✅ | EVDI DRM + cgroup fixes |
| NTSync | ✅ | ✅ | NT sync primitives for Wine/Proton |
| Unicode Bypass Fix | ✅ | ✅ | Path traversal / Unicode detection block |
| reduce_pelt | ✅ | ✅ | 32ms → 16ms CPU ramp-up |
| ZRAM Priority Reads | ✅ | ✅ | ZRAM BIO `REQ_PRIO` scheduling |
| Workqueue Lock Reduction | ✅ | ✅ | Unbound workqueue I/O gains |
| LLVM POLLY | ❌ | ✅ | Polyhedral loop optimiser |
| ZRAM Writeback | ❌ | ✅ | Cold-page writeback to flash |
| KALLSYMS_ALL | ✅ | ✅ | Full kernel symbol export |
| LTO Thin | ✅ | ✅ | Link-Time Optimisation |

### OnePlus Pad 2 Pro (CN) (SM8750 / `sun`)

| Feature | A15 | A16 | Notes |
|---------|-----|-----|-------|
| KernelSU / KernelSU-Next | ✅ | ✅ | |
| SUSFS | ✅ | ✅ | |
| Enhanced SUSFS (51_) | ✅ | ✅ | |
| ZeroMount VFS | ❌ | ✅ | |
| KSU Safety (70_) | ✅ | ✅ | |
| HMBIRD SCX (Fengchi) | ✅ | ✅ | |
| Baseband Guard (BBG) | ✅ | ✅ | |
| BBRv1 & BBRv3 | ✅ | ✅ | |
| Droidspaces / DS Extended | ✅ | ✅ | |
| NTSync | ✅ | ✅ | |
| reduce_pelt | ✅ | ✅ | |
| LLVM POLLY | ❌ | ✅ | |
| ZRAM Writeback | ❌ | ✅ | |
| KALLSYMS_ALL | ✅ | ✅ | |
| LTO Thin | ✅ | ✅ | |

### OnePlus 12 — Custom ROM (SM8650 / `pineapple`)

| Feature | A15 | A16 | Notes |
|---------|-----|-----|-------|
| KernelSU / KernelSU-Next | ✅ | ✅ | |
| SUSFS | ✅ | ✅ | |
| Enhanced SUSFS (51_) | ✅ | ✅ | |
| ZeroMount VFS | ❌ | ✅ | |
| KSU Safety (70_) | ✅ | ✅ | |
| HMBIRD SCX (Fengchi) | ❌ | ❌ | SM8750-specific — not on SM8650 |
| Baseband Guard (BBG) | ✅ | ✅ | |
| BBRv1 & BBRv3 | ✅ | ✅ | |
| Droidspaces / DS Extended | ✅ | ✅ | |
| NTSync | ✅ | ✅ | |
| reduce_pelt | ✅ | ✅ | |
| Unicode Bypass Fix | ✅ | ✅ | |
| LLVM POLLY | ❌ | ✅ | |
| ZRAM Writeback | ❌ | ✅ | |
| KALLSYMS_ALL | ✅ | ✅ | |
| LTO Thin | ✅ | ✅ | |

---

## 3. Build Config Reference

| Config File | Device | OS | Kernel | Source | uname |
|-------------|--------|-----|--------|--------|-------|
| `configs/a15/OP-PAD-3-SM8750.json` | Pad 3 | A15 | 6.6 latest | OnePlusOSS | `knockout` |
| `configs/a15/OP-PAD-3-SM8750-6.6.30.json` | Pad 3 | A15 | 6.6.30 (pinned) | OnePlusOSS | `knockout` |
| `configs/a15/OP-PAD-2-PRO.json` | Pad 2 Pro | A15 | 6.6 latest | OnePlusOSS | `knockout` |
| `configs/a15/OP12-CUSTOM.json` | OnePlus 12 | A15 | 6.1 `lineage-22.2` | OnePlus-12-Dev | `knockout` |
| `configs/a16/OP-PAD-3-SM8750.json` | Pad 3 | A16 | 6.6 latest | OnePlusOSS | `knockout` |
| `configs/a16/OP-PAD-2-PRO.json` | Pad 2 Pro | A16 | 6.6 latest | OnePlusOSS | `knockout` |
| `configs/a16/OP12-CUSTOM.json` | OnePlus 12 | A16 | 6.1 `lineage-23.2` | OnePlus-12-Dev | `knockout` |

---

## 4. Kernel Source Branches

| Device | Android | Branch / Repo |
|--------|---------|---------------|
| Pad 3 | A15 | `OnePlusOSS/android_kernel_common_oneplus_sm8750` · manifest `oneplus_pad_3_sm8750_v.xml` |
| Pad 3 | A16 | Same, manifest `oneplus_pad_3_sm8750_w.xml` |
| Pad 2 Pro | A15 | `OnePlusOSS` · manifest `oneplus_pad_2_pro_v.xml` |
| Pad 2 Pro | A16 | Same, manifest `oneplus_pad_2_pro_w.xml` |
| OnePlus 12 | A15 | `OnePlus-12-Development/android_kernel_oneplus_sm8650` `lineage-22.2` + modules |
| OnePlus 12 | A16 | Same, `lineage-23.2` (monolithic, no separate modules) |

---

## 5. Flashing Guidelines

1. **ROM compatibility**: Pad 3 / Pad 2 Pro → stock OxygenOS / ColorOS only. OnePlus 12 → custom AOSP ROMs only.
2. **Android version**: Always flash the build matching your current Android version. Do not flash an A16 kernel on an A15 ROM.
3. **Backup**: Keep a backup of your stock `boot.img` / `init_boot.img` before any kernel flash.
4. **KernelFlasher**: The recommended tool is [KernelFlasher](https://github.com/fatalcoder524/KernelFlasher) — it provides backup/restore of the boot slot before patching.
5. **Modules**: ZeroMount and SUSFS userspace features require the [SUSFS Module](https://github.com/sidex15) to be installed via KernelSU Manager.

---

## 6. Patch Attribution

| Patch Layer | Source | Credit |
|-------------|--------|--------|
| Build pipeline & manifests | [WildKernels](https://github.com/WildKernels/OnePlus_KernelSU_SUSFS) | zennnez |
| SUSFS `50_` base patches | [susfs4ksu](https://gitlab.com/simonpunk/susfs4ksu) | simonpunk |
| Enhanced SUSFS `51_` | [Super-Builders](https://github.com/Enginex0/Super-Builders) | Enginex0 |
| ZeroMount `60_` | [zeromount](https://github.com/Enginex0/zeromount) / Super-Builders | Enginex0 |
| KSU Safety `70_` | [Super-Builders](https://github.com/Enginex0/Super-Builders) | Enginex0 |
| SUSFS compat helpers | [Super-Builders build-helpers](https://github.com/Enginex0/Super-Builders) | Enginex0 |
| reduce_pelt | [Sultan Kernels](https://github.com/kerneltoast) | Sultan Alsawaf |
| LZ4 ARMv8 NEON | [DogEZ](https://github.com/dogez) | DogEZ |
| Baseband Guard | [Baseband-guard](https://github.com/vc-teahouse/Baseband-guard) | vc-teahouse |
| Droidspaces | [Droidspaces-OSS](https://github.com/ravindu644/Droidspaces-OSS) | ravindu644 |
| Kernel patches misc | [kernel_patches](https://github.com/zennnez/kernel_patches) | zennnez |
