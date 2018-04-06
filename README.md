## SailfishOS for Redmi 4X (santoni)

After months of trial and error, finally booted SailfishOS. 

> SailfishOS is a general purpose Linux distribution used commonly as a mobile operating system combining the Linux kernel for a particular hardware platform, the open-source Mer core stack of middleware, a proprietary UI contributed by Jolla or an open source UI, and other third-party components.

**THIS IS NOT ANDROID**. it's *SailfishOS* a **Community Port**, what does it mean? = **No APK Support**.



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

### How to install (Updated download links are here):

1. Download [LOS 14.1](https://sourceforge.net/projects/sailfishos-santoni/files/Loup-ROM-v7.1.2-Sailfish/lineage-14.1-20180401-UNOFFICIAL-santoni.zip/download)
2. Download [SailfishOS](https://sourceforge.net/projects/sailfishos-santoni/files/sailfishos-santoni-release-2.1.4.13-alpha-04042018.zip/download)
3. Reboot to TWRP
4. Make sure /data and /cache are in **ext4** format. (f2fs is NOT supported and will never be).
5. Perform a full wipe
6. Copy both files to your phone
7. Flash LOS 14.1
8. Flash SailfishOS
9. Reboot!

If it's not clear: **For the sake of simplicity, I'll only support ext4 partitions while testing Sailfish. If you use f2fs, please understand is on your risk only.**

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

### Changelog

```
- sailfishos-santoni-release-2.1.4.13-alpha-XXXXXXXX:
  * Magnetic Sensor (was already) fixed. Tested with "Messwerk".
  * Bluetooth fixed.
  * FM Radio fixed.
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

### Reporting Bugs

Only if the **Todo** list says a **feature is complete** and you faced a **bug**, please open an [issue here](https://github.com/bitrvmpd/sailfish-santoni/issues/new) attaching dmesg, logcat and systemctl logs.
**Give as much detail as possible.**

You can connect to your device in Developer Mode using telnet via usb:
``` 
telnet [Your USB IP] 2323 
```
or setting up the ssh server in `Settings > Developer Tools > Remote Connection`.
```
ssh nemo@[Your phone's Wifi IP]
>enter the password.
```
Or directly in your phone using the terminal app
```
devel-su
>enter the password.
```
#### Get the logs:

```
/usr/libexec/droid-hybris/system/bin/logcat > /home/nemo/logcat.log
dmesg > /home/nemo/dmesg.log
journalctl > /home/nemo/journalctl.log
```

Grab them using MTP Mode, they will be at your root of the internal storage.

**Logcat is located here `/usr/libexec/droid-hybris/system/bin/logcat`**

**Remember to change Default USB Mode in `Settings > USB > Default USB Mode` to "Always Ask"**

### Todo

- [X] WLAN
- [X] Display
- [ ] Web Browser (crashes) - Use [WebPirate](#webpirate)
- [X] Audio
- [X] Video playback
- [X] Calls
- [X] SMS
- [ ] Bluetooth
- [X] MicroSD
- [ ] Sensors
  * [X] Ambient
  * [X] Accel
  * [X] Proximity
  * [ ] Magnetic
  * [ ] Fingerprint (not supported until sailfish v3)
- [X] Vibration motor / Haptic
- [X] Buttons
  * [X] Vol+
  * [X] Vol-
  * [X] Power
- [X] Notification LED
- [X] Screen Backlight
- [X] Battery indicator
- [ ] FM Radio
- [X] Mobile Data
- [X] Camera
  * [X] Flashlight
  * [X] Take Pictures
  * [X] Record video
- [ ] VoLTE (not supported until sailfish v3)

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
