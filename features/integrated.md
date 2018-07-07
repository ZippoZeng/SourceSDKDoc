## 3、连接服务

1\) 建立连接

```java
LelinkPlayer leLinkPlayer = new LelinkPlayer(this);
leLinkPlayer.connect(mLelinkServiceInfo);
```

2\) 连接服务状态监听

```java
IConnectListener connectListener = new IConnectListener() {

    @Override
    void onConnect(LelinkServiceInfo serviceInfo, int extra) {

    }

    @Override
    void onDisconnect(LelinkServiceInfo serviceInfo, int what, int extra) {

    }
};
```
其中onDisconnect()的取值为：
what取值
- IConnectListener.CONNECT_INFO_DISCONNECT：连接断开
- IConnectListener.CONNECT_ERROR_FAILED：连接失败

3\) 关闭连接

```java
leLinkPlayer.disConnect();
```

4\) 获得正在连接的设备

```java
leLinkPlayer.getConnectLelinkServiceInfos();
```

## 4、播控服务

播控服务监听

```java
leLinkPlayer.setPlayerListener(playerListener);
```

playerListener为播控服务状态监听

```java
ILelinkPlayerListener playerListener = new ILelinkPlayerListener() {

        @Override
        public void onStart() {

        }

        @Override
        public void onPause() {

        }

        @Override
        public void onCompletion() {
            // 播放完成
        }

        @Override
        public void onStop() {

        }

        @Override
        public void onSeekComplete(int pPosition) {

        }

        @Override
        public void onInfo(int what, int extra) {

        }

        @Override
        public void onError(int what, int extra) {

        }

        /**
         * 音量变化回调
         * @param percent 当前音量
         */
        @Override
        public void onVolumeChanged(float percent) {

        }

        /**
         * 进度更新回调
         * @param duration 媒体资源总长度
         * @param position 当前进度
         */
        @Override
        public void onPositionUpdate(long duration, long position) {

        }

    };
```

## 4、释放资源

当你想释放我们的sdk的时候，可以调用该方法进行释放

```java
if (null != mLelinkServiceManager) {
    mLelinkServiceManager.release();
}
```

## 5、配置权限

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

## 6、混淆

当需要编译打包混淆的时候，投屏SDK已混淆过，无需在对投屏SDK及其依赖的第三方jar包进行混淆，请添加以下乐播配置：

```
###jmdns
-keep class javax.jmdns.** { *; }
-dontwarn javax.jmdns.**

###CyberGarage-upnp
-keep class org.cybergarage.** { *; }
-dontwarn org.cybergarage.**

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