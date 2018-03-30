## SailfishOS for Redmi 4X (santoni)

After months of trial and error, finally booted SailfishOS.

### Before we start, the classic disclaimer:

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

### How to install ?

1. Download [LOS 14.1](https://sourceforge.net/projects/loup-rom/files/latest/download)
2. Download [SailfishOS](https://sourceforge.net/projects/sailfishos-santoni/files/latest/download)
3. Reboot to TWRP
4. Perform a full wipe
5. Copy both files to your phone
6. Flash LOS 14.1
7. Flash SailfishOS
8. Reboot!

### Changelog
```
- sailfishos-santoni-release-2.1.4.13-alpha-30032018:
  * Alpha - Initial Release 
```

### Reporting Bugs

Only if the **Todo** list says a **feature is complete** and you faced a **bug**, please open an [issue here](https://github.com/bitrvmpd/sailfish-santoni/issues/new) attaching dmesg, logcat and systemctl logs.
Give as much detail as possible.
You can connect to your device using telnet via usb:
``` 
telnet 192.168.2.15 2323 
```
or setting up the ssh server in `Settings > Developer Tools > Remote Connection`.

**Logcat is located here `/usr/libexec/droid-hybris/system/bin/logcat`**

### Todo

- [X] WLAN
- [X] Display
- [ ] Web Browser (crashes)
- [X] Audio
- [ ] Calls
- [X] SMS
- [ ] Bluetooth
- [ ] MicroSD
- [ ] Sensors
  * [X] Ambient
  * [ ] Accel
  * [ ] Proximity
  * [ ] Fingerprint
- [X] Vibration motor / Haptic
- [X] Buttons
  * [X] Vol+
  * [X] Vol-
  * [X] Power
- [X] Notification LED
- [X] Screen Backlight
- [X] Battery indicator
- [ ] FM Radio

### Sources

- Kernel: [https://github.com/bitrvmpd/msm-3.18/tree/hybris-14.1](https://github.com/bitrvmpd/msm-3.18/tree/hybris-14.1)
- Device Tree: [https://github.com/bitrvmpd/android_device_xiaomi_santoni/tree/hybris-14.1](https://github.com/bitrvmpd/android_device_xiaomi_santoni/tree/hybris-14.1)
- Vendor Tree: [https://github.com/bitrvmpd/android_vendor_xiaomi_santoni/tree/cm-14.1](https://github.com/bitrvmpd/android_vendor_xiaomi_santoni/tree/cm-14.1)

- SailfishOS stuff:
  * droid-config-santoni: [https://github.com/bitrvmpd/droid-config-santoni](https://github.com/bitrvmpd/droid-config-santoni)
  * droid-hal-version-santoni: [https://github.com/bitrvmpd/droid-hal-version-santoni](https://github.com/bitrvmpd/droid-hal-version-santoni)
  * droid-hal-santoni: [https://github.com/bitrvmpd/droid-hal-santoni](https://github.com/bitrvmpd/droid-hal-santoni)
