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

- **build_packages.sh** is not downloading any submodule, so the compilation fails.

Edit this file

```
rpm/dhd/helpers/utils.sh

```

Replace this line

```
git submodule update >>$LOG 2>&1|| die "pulling of updates failed"

```

with this

```
git submodule update --init --recursive >>$LOG 2>&1|| die "pulling of updates failed"
```

rebuild the MW again.

- ERROR: nothing provides gstreamer1.0-omx, gstreamer1.0-libav

Derp error, remember to download and build the desired MW, like this:

```
cd $ANDROID_ROOT/hybris/mw
git clone https://github.com/sailfishos/gst-omx.git
cd gst-omx
git submodule update —init —recursive
cd $ANDROID_ROOT
rpm/dhd/helpers/build_packages.sh —mw=https://github.com/sailfishos/gst-omx.git

cd $ANDROID_ROOT/hybris/mw
git clone https://github.com/sailfishos/gst-libav.git
cd gst-libav
git submodule update —init —recursive
cd $ANDROID_ROOT
rpm/dhd/helpers/build_packages.sh —mw=https://github.com/sailfishos/gst-libav.git
```

- While building [https://github.com/sailfishOS/gst-omx.git](https://github.com/sailfishOS/gst-omx.git) I faced this issue:

```
configure: error: invalid OpenMAX IL target, you must specify one of —with-omx-target={generic,rpi,bellagio}
```

The patches for sailfishOS weren't being applied, to fix this i had to enforce the %prep stage in mb2.

1. Comment out line 930 in /usr/bin/mb2:

```
#BUILD_NOPREP=(--noprep)

```
2. Also remove "--noprep" in line 1128

```
This argument----
                |
rpmbuild -bc --noprep --short-circuit --build-in-place --define "_sourcedir $(readlink -f rpm)" rpm/test.spec \

```

**Remember to revert this. Or it may cause some problems in the future.**

Also, everytime you need to apply a patch in a package, do this to ensure it gets applied.


- autogen.sh git not found

Run this command to fix it 

```
sb2 -t $VENDOR-$DEVICE-$PORT_ARCH -m sdk-install -R zypper in git
```

- When building gstreamer, $ANDROID_ROOT/system/core/rootdir/init.rc doesn't contain "service minimedia" 

The file you're looking for is located here: 

```
frameworks/native/cmds/servicemanager/servicemanager.rc
```


- If your devices uses 32 bits camera binaries. When building gstreamer, this command:

```
rpm/dhd/helpers/pack_source_droidmedia-localbuild.sh $DROIDMEDIA_VERSION
```

says "**Please build droidmedia as per HADK instructions**"

For some reason it didn't created the 32 bit binaries even if it already has "BOARD_QTI_CAMERA_32BIT_ONLY := true" in any of the \*.mk files of your device tree. To fix it run:

```
cd $ANDROID_ROOT
echo DROIDMEDIA_32 := true >> external/droidmedia/env.mk
```

Then try to compile it again with

```
make -jXX libdroidmedia_32 minimediaservice minisfservice
```


***I will be updating this guide. And I know, some thing may be redundant. Will correct them in the future***
