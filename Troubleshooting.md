# Troubleshooting SailfishOS
Here are some stuff that I had need to look between a sea of IRC logs. Hope it helps.

- When I tried to compile ngfd-plugin-droid-vibrator it gives an error

go to 
```
hybris/mw/ngfd-plugin-droid-vibrator
```
and run 
```
git reset —hard 3e2b4fb5b03a6d3db9ca5a41c7091e771f99cc4f
``` 
to reset that repo to a healthy point. Then use 
```
rpm/dhd/helpers/build_packages.sh -b hybris/mw/ngfd-plugin-droid-vibrator -s rpm/ngfd-plugin-native-vibrator.spec
``` 
and when you run the whole build_packages.sh script, **skip** the vibrator build process **(say N)**.

- Kickstarter file generation failed

run 
```
rpm2cpio droid-local-repo/$DEVICE/droid-configs/droid-config-$DEVICE-ssu-kickstarts-1-1.armv7hl.rpm | cpio -idmv
```
Then in the sed command use 
```
$ANDROID_ROOT/usr/share/kickstarts/$KS
``` 
instead of 
```
$ANDROID_ROOT/hybris/droid-configs/installroot/usr/share/kickstarts/$KS
```
like this:
```
sed \
"/$HA_REPO/i$HA_DEV —baseurl=file:\/\/$ANDROID_ROOT\/droid-local-repo\/$DEVICE" \
$ANDROID_ROOT/usr/share/kickstarts/$KS \
> $KS
```

- When I'm about to create the flashable .zip file, I execute this:
```
sudo mic create fs --arch=$PORT_ARCH \
--tokenmap=ARCH:$PORT_ARCH,RELEASE:$RELEASE,EXTRA_NAME:$EXTRA_NAME \
--record-pkgs=name,url \
--outdir=sfe-$DEVICE-$RELEASE$EXTRA_NAME \
--pack-to=sfe-$DEVICE-$RELEASE$EXTRA_NAME.tar.bz2 \
$ANDROID_ROOT/Jolla-@RELEASE@-$DEVICE-@ARCH@.ks
```

It gives an error about an unrecognized option, simply check your .ks file. In my case it was an "em dash" — that was causing the issue.
Replace it with two dashes --

- This appears in dmesg, no GUI is displayed
```
kgsl kgsl-3d0: |_load_firmware| request_firmware(a530_pm4.fw) failed: -2
```
Check your defconfig file, for me I needed to enable these flags.
```
CONFIG_FW_LOADER=y
CONFIG_FW_LOADER_USER_HELPER=y
CONFIG_FW_LOADER_USER_HELPER_FALLBACK=y
```

***I will be updating this guide.***
