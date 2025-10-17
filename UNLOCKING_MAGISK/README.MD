# Lenovo TB330XU Bootloader Unlock + Root (ReliveDVD_6) [TB330XU_ROW_OPEN_USER_V5_V_ZUI_17.0.125_ST_250613]

### Boot into relivedvd_6
Use the live environment to avoid driver issues.
https://androidfilehost.com/?fid=1109791587270922802
---

### Copy required files into /opt/mtkclient
Place these:
- `auth_sv5.auth`
- `MTK_AllInOne_DA-resign.bin`

They must sit next to `mtk.py`.

---

### Test handshake (confirm BROM connectivity)
```bash
python /opt/mtkclient/mtk.py payload --auth /opt/mtkclient/auth_sv5.auth --da /opt/mtkclient/MTK_AllInOne_DA-resign.bin
````

Hold **Vol+ + Vol-**, then plug the tablet in while the command waits.
If it shows `[BOOT] BootROM mode detected` → connection OK.

---

### Unlock bootloader

```bash
python /opt/mtkclient/mtk.py da seccfg unlock --auth /opt/mtkclient/auth_sv5.auth
```

When it completes:

* Bootloader is unlocked.
* Next boot will show *dm-verity corruption* warning — normal.
* Press **Power** when prompted → tablet enters **Orange State** (unlocked, permissive).

---

### Flash Magisk-patched vendor_boot

```bash
fastboot flash vendor_boot magisk_patched-30400_vox4A.img
```

If Magisk shows “not installed” later, open the Magisk app → *Install → Direct Install* to finish patching live.

---

### Behavior after patch

* First boot = dm-verity “corrupt” message.
  Press **Power** once → boots fine.
* Root verified:

  ```bash
  adb shell
  su
  whoami
  # → root
  ```

---

### Known non-working fastboot disable commands

These do *not* suppress Lenovo’s AVB check:

```bash
fastboot --disable-verity --disable-verification flash vbmeta vbmeta.img
fastboot --disable-verity --disable-verification flash vbmeta_system vbmeta_system.img
fastboot --disable-verity --disable-verification flash vbmeta_vendor vbmeta_vendor.img
```

Bootloader still shows “dm-verity corruption” and pauses.
Bypass is harmless — press **Power** to continue.

---

### Final state

* Bootloader unlocked (`Orange State`)
* Root via Magisk functional
* dm-verity warning bypassable

```
