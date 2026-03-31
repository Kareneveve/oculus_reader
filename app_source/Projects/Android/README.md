# App编译方法
使用`~/Android/gradle/gradle-8.3/bin/gradle`来编译，不要用系统的`gradle`来编译，系统的`gradle`版本不符合

```bash
cd app_source/Projects/Android
~/Android/gradle/gradle-8.3/bin/gradle clean
~/Android/gradle/gradle-8.3/bin/gradle assembleDebug
```

编译完后,`teleop-debug.apk`在`app_source/Projects/Android/build/outputs/apk/debug/`目录之下。

# App下载方法
先使用USB线连接上VR头显

检查是否连接上头显设备
```bash
adb devices
```

若显示出类似于以下信息，则说明连接成功
```bash
List of devices attached
340YC10G980B01  device
```

然后执行：
```bash
adb uninstall com.rail.oculus.teleop # 若已经下载了，先删除

cd oculus_reader/APK
adb install teleop-debug.apk
```

