# 1、SDK导入及配置

##1）导入SDK
请将aar到工程中的libs中，
![导入aar](/assets/import_aar.png)

然后在module的build.gradle中添加以下配置

在android节点中添加以下配置

```groovy
repositories {
    flatDir {
        dirs 'libs'
    }
}
```

在dependencies中添加以下配置

```groovy
compile(name: 'source-sdk', ext: 'aar')
```

接下来，您就可以调用我们的api了

##2）配置权限

如果Android系统为6.0以上，则需要动态申请一些权限：

* android.permission.READ\_PHONE\_STATE
* android.permission.WRITE\_EXTERNAL\_STORAGE
* android.permission.ACCESS_FINE_LOCATION

必须要有以上权限，否则会导致SDK功能异常

以下为投屏SDK需要的权限，aar包自带有，无需再次配置

```xml
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
<uses-permission android:name="android.permission.ACCESS_WIFI_STATE"/>
<uses-permission android:name="android.permission.CHANGE_WIFI_MULTICAST_STATE"/>
<uses-permission android:name="android.permission.CHANGE_WIFI_STATE"/>
<uses-permission android:name="android.permission.INTERNET"/>
<uses-permission android:name="android.permission.READ_PHONE_STATE"/>

<!-- mirror -->
<uses-permission android:name="android.permission.WAKE_LOCK" />
<uses-permission android:name="android.permission.RECORD_AUDIO" />
<uses-permission android:name="android.permission.CAPTURE_AUDIO_OUTPUT" />
<uses-permission android:name="android.permission.CAPTURE_VIDEO_OUTPUT" />
<uses-permission android:name="android.permission.CAPTURE_SECURE_VIDEO_OUTPUT" />
```

##3）混淆

当需要编译打包混淆的时候，投屏SDK已混淆过，无需在对投屏SDK及其依赖的第三方jar包进行混淆，请添加以下乐播配置：

```
###jmdns
-keep class javax.jmdns.** { *; }
-dontwarn javax.jmdns.**

###CyberGarage-upnp
-keep class org.cybergarage.** { *; }
-dontwarn org.cybergarage.**

###plist
-keep class com.dd.plist.** { *; }
-dontwarn com.dd.plist.**

###kxml
-keep class org.kxml2.** { *; }
-keep class org.xmlpull.** { *; }
-dontwarn org.kxml2.**
-dontwarn org.xmlpull.**

###Lebo
-keep class com.hpplay.**{*;}
-keep class com.hpplay.**$*{*;}
-dontwarn com.hpplay.**
```