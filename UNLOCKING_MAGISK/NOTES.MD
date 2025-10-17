# Boot relivedvd_6
https://androidfilehost.com/?fid=1109791587270922802

# copy to /opt/mtkclient
- auth_sv5.auth
- MTK_AllInOne_DA-resign.bin

# test handshake
```
python /opt/mtkclient/mtk.py payload --auth /opt/mtkclient/auth_sv5.auth --da /opt/mtkclient/MTK_AllInOne_DA-resign.bin
```

# unlock bootloader
```
python /opt/mtkclient/mtk.py da seccfg unlock --auth /opt/mtkclient/auth_sv5.auth
```

# reboot into bootloader
- WILL HAVE DM-VERITY CORRUPTION
- Bypassable with power button -> orange state

# flash vendor_boot
```
fastboot flash vendor_boot magisk_patched-30400_vox4A.img
```

# notes
does not work:
fastboot --disable-verity --disable-verification flash vbmeta vbmeta.img
fastboot --disable-verity --disable-verification flash vbmeta_system vbmeta_system.img
fastboot --disable-verity --disable-verification flash vbmeta_vendor vbmeta_vendor.img


