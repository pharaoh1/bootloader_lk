### bootloader_lk
LK bootable from Nexus 6P's fastboot, with extra commands for debugging

###How to build
```cd /path/to/cm/sources/
source build/envsetup.sh
lunch aosp_arm-eng
cd /path/to/bootloaderlk/
make msm8994
cd build-msm8994
aarch64-linux-android-objcopy emmc_appsboot.mbn -O binary fastboot-boot.img
```

enter fastboot mode from fastboot.

fastboot boot fastboot-boot.img 

then you are in new fastboot with extra commands.

commands available:

G:\>fastboot oem help
```...
(bootloader) commands:
(bootloader)    download:
(bootloader)    getvar:
(bootloader)    oem help
(bootloader)    oem partition-dump
(bootloader)    oem hardboot-set
(bootloader)    oem jump-to-kernel
(bootloader)    oem hardboot-copy
(bootloader)    oem dump-ram
(bootloader)    oem select-display-panel
(bootloader)    oem off-mode-charge
(bootloader)    oem disable-charger-screen
(bootloader)    oem enable-charger-screen
(bootloader)    oem dump-partitiontable
(bootloader)    preflash
(bootloader)    oem device-info
(bootloader)    flashing get_unlock_ability
(bootloader)    flashing unlock_critical
(bootloader)    flashing lock_critical
(bootloader)    flashing lock
(bootloader)    flashing unlock
(bootloader)    oem lock
(bootloader)    oem unlock-go
(bootloader)    oem unlock
(bootloader)    oem reboot-dload
(bootloader)    oem reboot-recovery
(bootloader)    reboot-bootloader
(bootloader)    reboot
(bootloader)    continue
(bootloader)    boot
(bootloader)    erase:
(bootloader)    flash:
OKAY [  0.329s]
finished. total time: 0.330s
```

G:\>fastboot  oem partition-dump
```...
(bootloader) p00:N:       modem S:    163840 T:0 F:   16384 L:   180223
(bootloader) p01:N:        sbl1 S:      2048 T:0 F:  180224 L:   182271
(bootloader) p02:N:         sdi S:       192 T:0 F:  182272 L:   182463
(bootloader) p03:N:          tz S:      2048 T:0 F:  182464 L:   184511
(bootloader) p04:N:         rpm S:      1000 T:0 F:  184512 L:   185511
(bootloader) p05:N:         hyp S:      1024 T:0 F:  185512 L:   186535
(bootloader) p06:N:        pmic S:       256 T:0 F:  186536 L:   186791
(bootloader) p07:N:         DDR S:      2048 T:0 F:  186792 L:   188839
(bootloader) p08:N:         sec S:       256 T:0 F:  188840 L:   189095
(bootloader) p09:N:       aboot S:      8760 T:0 F:  189096 L:   197855
(bootloader) p10:N:     pmicbak S:       256 T:0 F:  197856 L:   198111
(bootloader) p11:N:     sbl1bak S:      2048 T:0 F:  198112 L:   200159
(bootloader) p12:N:       tzbak S:      2048 T:0 F:  200160 L:   202207
(bootloader) p13:N:      rpmbak S:      1000 T:0 F:  202208 L:   203207
(bootloader) p14:N:      hypbak S:      1024 T:0 F:  203208 L:   204231
(bootloader) p15:N:    abootbak S:      8760 T:0 F:  204232 L:   212991
(bootloader) p16:N:     devinfo S:         2 T:0 F:  212992 L:   212993
(bootloader) p17:N:         fsg S:      8192 T:0 F:  229376 L:   237567
(bootloader) p18:N:      limits S:         2 T:0 F:  245760 L:   245761
(bootloader) p19:N:    modemst1 S:      8192 T:0 F:  262144 L:   270335
(bootloader) p20:N:    modemst2 S:      8192 T:0 F:  270336 L:   278527
(bootloader) p21:N:        apdp S:       512 T:0 F:  278528 L:   279039
(bootloader) p22:N:       msadp S:       512 T:0 F:  279040 L:   279551
(bootloader) p23:N:   keymaster S:       512 T:0 F:  279552 L:   280063
(bootloader) p24:N:      cmnlib S:       512 T:0 F:  280064 L:   280575
(bootloader) p25:N:keymasterbak S:       512 T:0 F:  280576 L:   281087
(bootloader) p26:N:   cmnlibbak S:       512 T:0 F:  281088 L:   281599
(bootloader) p27:N:         dpo S:         2 T:0 F:  281600 L:   281601
(bootloader) p28:N:         fsc S:         2 T:0 F:  281602 L:   281603
(bootloader) p29:N:         ssd S:        16 T:0 F:  281604 L:   281619
(bootloader) p30:N:     oeminfo S:     13292 T:0 F:  281620 L:   294911
(bootloader) p31:N:     persist S:     16384 T:0 F:  294912 L:   311295
(bootloader) p32:N:    metadata S:     32768 T:0 F:  311296 L:   344063
(bootloader) p33:N:        boot S:     65536 T:0 F:  344064 L:   409599
(bootloader) p34:N:    recovery S:     65536 T:0 F:  409600 L:   475135
(bootloader) p35:N:         oem S:    131072 T:0 F:  475136 L:   606207
(bootloader) p36:N:      vendor S:    409600 T:0 F:  606208 L:  1015807
(bootloader) p37:N:       cache S:    204800 T:0 F: 1015808 L:  1220607
(bootloader) p38:N:        misc S:      2048 T:0 F: 1220608 L:  1222655
(bootloader) p39:N:    keystore S:      1024 T:0 F: 1222656 L:  1223679
(bootloader) p40:N:         frp S:      1024 T:0 F: 1223680 L:  1224703
(bootloader) p41:N:  persistent S:      1000 T:0 F: 1224704 L:  1225703
(bootloader) p42:N:      system S:   6291456 T:0 F: 1225704 L:  7517159
(bootloader) p43:N:    userdata S: 236760055 T:0 F: 7517160 L:244277214
OKAY [  0.448s]
finished. total time: 0.449s
```
G:\>fastboot oem dump-partitiontable
```...
(bootloader) 0: modem sz:163840 (16384-180223) type:0
(bootloader) 1: sbl1 sz:2048 (180224-182271) type:0
(bootloader) 2: sdi sz:192 (182272-182463) type:0
(bootloader) 3: tz sz:2048 (182464-184511) type:0
(bootloader) 4: rpm sz:1000 (184512-185511) type:0
(bootloader) 5: hyp sz:1024 (185512-186535) type:0
(bootloader) 6: pmic sz:256 (186536-186791) type:0
(bootloader) 7: DDR sz:2048 (186792-188839) type:0
(bootloader) 8: sec sz:256 (188840-189095) type:0
(bootloader) 9: aboot sz:8760 (189096-197855) type:0
(bootloader) 10: pmicbak sz:256 (197856-198111) type:0
(bootloader) 11: sbl1bak sz:2048 (198112-200159) type:0
(bootloader) 12: tzbak sz:2048 (200160-202207) type:0
(bootloader) 13: rpmbak sz:1000 (202208-203207) type:0
(bootloader) 14: hypbak sz:1024 (203208-204231) type:0
(bootloader) 15: abootbak sz:8760 (204232-212991) type:0
(bootloader) 16: devinfo sz:2 (212992-212993) type:0
(bootloader) 17: fsg sz:8192 (229376-237567) type:0
(bootloader) 18: limits sz:2 (245760-245761) type:0
(bootloader) 19: modemst1 sz:8192 (262144-270335) type:0
(bootloader) 20: modemst2 sz:8192 (270336-278527) type:0
(bootloader) 21: apdp sz:512 (278528-279039) type:0
(bootloader) 22: msadp sz:512 (279040-279551) type:0
(bootloader) 23: keymaster sz:512 (279552-280063) type:0
(bootloader) 24: cmnlib sz:512 (280064-280575) type:0
(bootloader) 25: keymasterbak sz:512 (280576-281087) type:0
(bootloader) 26: cmnlibbak sz:512 (281088-281599) type:0
(bootloader) 27: dpo sz:2 (281600-281601) type:0
(bootloader) 28: fsc sz:2 (281602-281603) type:0
(bootloader) 29: ssd sz:16 (281604-281619) type:0
(bootloader) 30: oeminfo sz:13292 (281620-294911) type:0
(bootloader) 31: persist sz:16384 (294912-311295) type:0
(bootloader) 32: metadata sz:32768 (311296-344063) type:0
(bootloader) 33: boot sz:65536 (344064-409599) type:0
(bootloader) 34: recovery sz:65536 (409600-475135) type:0
(bootloader) 35: oem sz:131072 (475136-606207) type:0
(bootloader) 36: vendor sz:409600 (606208-1015807) type:0
(bootloader) 37: cache sz:204800 (1015808-1220607) type:0
(bootloader) 38: misc sz:2048 (1220608-1222655) type:0
(bootloader) 39: keystore sz:1024 (1222656-1223679) type:0
(bootloader) 40: frp sz:1024 (1223680-1224703) type:0
(bootloader) 41: persistent sz:1000 (1224704-1225703) type:0
(bootloader) 42: system sz:6291456 (1225704-7517159) type:0
(bootloader) 43: userdata sz:236760055 (7517160-244277214) type:0
OKAY [  0.440s]
finished. total time: 0.441s

```
thanks all.

