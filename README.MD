**_Work In Progress_**
---

# Bootloader Unlocked and Rooted Success
https://github.com/honeybugserial/TB330XU-Unlocking-Rooting/tree/main/UNLOCKING_MAGISK

---

# Lenovo TB-330XU (ROW) Firmware + SP Flash Tool Setup

This repository contains configuration files and extracted metadata for the Lenovo **TB-330XU (ROW)** tablet based on the **MediaTek MT6768** platform.

All firmware and tooling were obtained from Lenovo Smart Assistant during service restoration and preserved for public use.  
These images are **stock**, unmodified dumps suitable for repair or recovery.

---

## 📦 Firmware & Tool Downloads

| Component | Description | Link |
|------------|--------------|------|
| **SP Flash Tool v5 (Pogopin Edition)** | Recommended version tested with TB-330XU Smart Assistant downloads | [Download on Archive.org](https://archive.org/details/sp-flash-tool-v-5-tb-330-pogopin.-7z) |
| **TB-330XU ROW Firmware** | ZUI 17.0.125 (ROW, V5V build) – extracted directly from Smart Assistant | [Download on Archive.org](https://archive.org/details/tb-330-xu-row-open-user-v-5-v-zui-17.0.125-st-250613) |
| **MT6768 Scatter Files** | Matching scatter/XML configuration used by Smart Assistant | [Download on Archive.org](https://archive.org/details/mt-6768-android-scatter) |

---

## 🧩 Configuration Notes

- **Platform:** `MT6768` (Helio G85)
- **Project ID:** `barley_row_lte`
- **Storage:** EMMC
- **DA:** `MTK_AllInOne_DA-resign.bin`
- **Connection Type:** `BromUSB` (without battery, debug UART logging)
- **Verified Partitions Include:**  
  `preloader`, `vbmeta_a`, `boot_a`, `vendor_boot_a`, `dtbo_a`, `tee_a`, `lenovoraw`, `lenovocust`, `logo.bin`, etc.  

---

## ⚙️ Usage

1. Extract all archives with **7-Zip**.  
2. Launch **SP Flash Tool v5** from the `Pogopin` build.  
3. Load the provided `MT6768_Android_scatter.txt`.  
4. Select **Download Only** (not Format + Download).  
5. Connect the tablet while powered off — flashing should begin automatically.  

---

## 🧾 Notes

- Files were automatically deleted by Smart Assistant post-download; these copies were captured before removal.  
- Verified to boot stock ZUI 17.0.125 on ROW variants.  
- Use at your own risk. These are manufacturer-signed images; **no modifications or patches** were applied.

---

<details>
<summary>📄 Partition Index Summary (from MT6768.xml)</summary>

| # | Partition | Type | Offset | Size | Description |
|---|------------|------|---------|-------|-------------|
| 1 | `preloader` | raw | 0x00000000 | 0x0080000 | Boot preloader |
| 2 | `pgpt` | raw | 0x0080000 | 0x0008000 | GPT primary |
| 3 | `vbmeta_a` | raw | 0x00B0000 | 0x0080000 | Verified Boot metadata |
| 4 | `boot_a` | raw | 0x0130000 | 0x2000000 | Boot image |
| 5 | `vendor_boot_a` | raw | 0x2130000 | 0x4000000 | Vendor boot image |
| 6 | `dtbo_a` | raw | 0x6130000 | 0x0800000 | Device tree overlay |
| 7 | `tee_a` | raw | 0x6930000 | 0x0600000 | Trusted execution environment |
| 8 | `logo` | raw | 0x6F30000 | 0x0800000 | Boot logo |
| 9 | `super` | raw | 0x7730000 | 0x2C0000000 | System/Vendor/Super partition |
| 10 | `userdata` | f2fs | 0x2C7730000 | 0x19BC4F8000 | User data |

*(Offsets and sizes confirmed from MT6768.xml extracted from Lenovo Smart Assistant.)*:contentReference[oaicite:0]{index=0}

</details>

---
 
**Date:** 2025-10-16  
**Checksum:** SHA-256 sums included in archive metadata on Archive.org.
