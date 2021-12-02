
#### setup supersu in oculus go

##### 1、disable selinux
```
adb root 

adb shell

echo 0 > /sys/fs/selinux/enforce

/system/xbin/daemonsu --auto-daemon &
```

##### 2、download supersu zip and apk

##### 3、setup
```
adb root

adb remount

adb push SuperSU.apk /system/app/SuperSU.apk

adb shell chmod 0644 /system/app/SuperSU.apk

adb shell chcon u:object_r:system_file:s0 /system/app/SuperSU.apk

adb push arm64/su /system/xbin/su

adb shell chmod 0755 /system/xbin/su 

adb shell chcon u:object_r:system_file:s0 /system/xbin/su 

adb push arm64/su /system/bin/.ext/.su 

adb shell chmod 0755 /system/bin/.ext/.su 

adb shell chcon u:object_r:system_file:s0 /system/bin/.ext/.su 

adb push arm64/su /system/xbin/daemonsu 

adb shell chmod 0755 /system/xbin/daemonsu 

adb shell chcon u:object_r:system_file:s0 /system/xbin/daemonsu 

adb push arm64/supolicy /system/xbin/supolicy 

adb shell chmod 0755 /system/xbin/supolicy 

adb shell chcon u:object_r:system_file:s0 /system/xbin/supolicy 

adb push arm64/libsupol.so /system/lib64/libsupol.so 

adb shell chmod 0755 /system/lib64/libsupol.so 

adb shell chcon u:object_r:system_file:s0 /system/lib64/libsupol.so 

adb reboot

```

##### 4、disable selinux again
```
adb root 

adb shell

echo 0 > /sys/fs/selinux/enforce

/system/xbin/daemonsu --auto-daemon &
```

##### 5、open the su apk
```
adb shell am start -a android.intent.action.VIEW -d com.oculus.tv -e uri eu.chainfire.supersu/.MainActivity  com.oculus.vrshell/.MainActivity
```

##### 6、enjoy the root for app
