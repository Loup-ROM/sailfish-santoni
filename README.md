## SailfishOS for Redmi 4X (santoni)

After months of trial and error, finally booted SailfishOS.

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

### How to install ?

1. Download [LOS 14.1](https://sourceforge.net/projects/loup-rom/files/latest/download)
2. Download SailfishOS (Download link will be here)
3. Copy both files to your phone
4. Reboot to TWRP
5. Flash LOS
6. Flash SailfishOS
7. Reboot!

### Sources

- Kernel: https://github.com/bitrvmpd/msm-3.18/tree/hybris-14.1
- Device Tree: https://github.com/bitrvmpd/android_device_xiaomi_santoni/tree/hybris-14.1
- Vendor Tree: https://github.com/bitrvmpd/android_vendor_xiaomi_santoni/tree/cm-14.1

- SailfishOS stuff:
  * droid-config-santoni: https://github.com/bitrvmpd/droid-config-santoni
  * droid-hal-version-santoni: https://github.com/bitrvmpd/droid-hal-version-santoni
  * droid-hal-santoni: https://github.com/bitrvmpd/droid-hal-santoni
