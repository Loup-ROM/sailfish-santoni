## SailfishOS for Redmi 4X (santoni)

After months of trial and error, finally booted SailfishOS. 

> SailfishOS is a general purpose Linux distribution used commonly as a mobile operating system combining the Linux kernel for a particular hardware platform, the open-source Mer core stack of middleware, a proprietary UI contributed by Jolla or an open source UI, and other third-party components.

<a name="no-apk"></a>**THIS IS NOT ANDROID**. it's *SailfishOS* a **Community Port**, what does it mean? = **No APK Support**.



### The classic disclaimer:

```
 /*
 *
 * I am not responsible for bricked devices, dead SD cards,
 * thermonuclear war, or you getting fired because the alarm app failed. Please
 * do some research if you have any concerns about features included in this ROM
 * before flashing it! YOU are choosing to make these modifications, and if
 * you point the finger at me for messing up your device, I will laugh at you.
 *
 */
 ```

### What's not working?
- Web Browser (crashes) - Use [WebPirate](#webpirate).
- Fingerprint (not supported until sailfish v3).
- VoLTE (not supported until sailfish v3).
- [Android APKs](#no-apk).
- Audio on recorded videos are out of sync.

### What's working?
- Everything else.

### How to install (Updated download links are here):

1. Download [LOS 14.1](https://sourceforge.net/projects/sailfishos-santoni/files/Loup-ROM-v7.1.2-Sailfish/lineage-14.1-20180401-UNOFFICIAL-santoni.zip/download)
2. Download [SailfishOS](https://sourceforge.net/projects/sailfishos-santoni/files/sailfishos-santoni-release-2.1.4.13-beta-06042018.zip/download)
3. Reboot to TWRP
4. Make sure /data and /cache are in **ext4** format. (f2fs is NOT supported and will never be).
5. Perform a full wipe
6. Copy both files to your phone
7. Flash LOS 14.1
8. Flash SailfishOS
9. Reboot!

If it's not clear: **For the sake of simplicity, I'll only support ext4 partitions while testing Sailfish. If you use f2fs, please understand is at your own risk.**

### Changelog

```
- sailfishos-santoni-release-2.1.4.13-beta-06042018:
  * Magnetic Sensor (was already) fixed. Tested with "Messwerk".
  * Bluetooth fixed.
  * FM Radio fixed.
  * All features are working, we're in beta!.
- sailfishos-santoni-release-2.1.4.13-alpha-04042018:
  * Video recording fixed.
  * Calls fixed.
- sailfishos-santoni-release-2.1.4.13-alpha-01042018:
  * microSD Access fixed.
  * Video playback fixed.
  * Accel, Proximity, Gyro fixed.
  * Camera partially fixed, take pictures with frontal and back, record video limited to frontal only.
  * Updated LineageOS 14.1 base, this fixes sensors!.
- sailfishos-santoni-release-2.1.4.13-alpha-30032018:
  * Alpha - Initial Release 
```

###### XXXXXXXX means not released yet

### <a name="webpirate"></a>Browser Partial Fix:
- Install Storeman [download it here](https://openrepos.net/sites/default/files/packages/6416/harbour-storeman-0.0.21-2.armv7hl.rpm)
- Copy it to your device.
- Enable Untrusted Sofwate in settings.
- Navigate to your file (via Settings > Storage), open  and install it.
- Download **WebPirate** from Storeman.

**Known Bug**
Storeman stays in refreshing cache forever, and you can't install new apps.
> Let it refresh for 3 min. then close the app (From recents too!). Reopen it and you'll be able to download stuff

###### Now you have access to more apps :D

### Reporting Bugs

If you faced a **bug** or something is not working at all, please open an [issue here](https://github.com/bitrvmpd/sailfish-santoni/issues/new). Follow the instructions provided there.
**Give as much detail as possible.**

### Troubleshooting (devs)

If you have any error during the compilation/porting process [check this](https://bitrvmpd.github.io/sailfish-santoni/Troubleshooting)

### Sources

- Kernel: [https://github.com/bitrvmpd/msm-3.18/tree/hybris-14.1](https://github.com/bitrvmpd/msm-3.18/tree/hybris-14.1)
- Device Tree: [https://github.com/bitrvmpd/android_device_xiaomi_santoni/tree/hybris-14.1](https://github.com/bitrvmpd/android_device_xiaomi_santoni/tree/hybris-14.1)
- Vendor Tree: [https://github.com/bitrvmpd/android_vendor_xiaomi_santoni/tree/hybris-14.1](https://github.com/bitrvmpd/android_vendor_xiaomi_santoni/tree/cm-14.1)

- SailfishOS stuff:
  * droid-config-santoni: [https://github.com/bitrvmpd/droid-config-santoni](https://github.com/bitrvmpd/droid-config-santoni)
  * droid-hal-version-santoni: [https://github.com/bitrvmpd/droid-hal-version-santoni](https://github.com/bitrvmpd/droid-hal-version-santoni)
  * droid-hal-santoni: [https://github.com/bitrvmpd/droid-hal-santoni](https://github.com/bitrvmpd/droid-hal-santoni)
  
### Credits
 - [Piggz](https://github.com/piggz) (for his awesome port for mido)
 - [Pi3Gey](https://github.com/Pi3Gey) (for helping me improve the bug reporting guide)
 - The Sailfish Community.
 - The Halium Community.
