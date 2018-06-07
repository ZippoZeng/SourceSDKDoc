# SDK集成

## 0、依赖

请将aar到工程中的libs中，  
![import\_aar](/assets/import_aar.png)  
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

## 1、初始化SDK

```java
LelinkSetting lelinkSetting = new LelinkSetting.LelinkSettingBuilder(APPKEY, APPSECRET).build();
ILelinkServiceManager mLelinkServiceManager = LelinkServiceManager.getInstance(context);
mLelinkServiceManager.setLelinkSetting(lelinkSetting);
```

SDK初始化需要传入三个参数：  
第一个参数为应用程序的context；  
第二个参数是在开发者中心申请的APPKEY；  
第三个参数是在开发者中心申请的APPSECRET

关于APPKEY & APPSECRET 的获取，[1、申请APPKEY & APPSECRET](http://cdn.hpplay.com.cn/test/don/_book/jie-shou-duan-sdk-kai-fa-zhe-wen-dang/shen.html)

## 2、发现服务

1\) 启动搜索服务

```java
mLelinkServiceManager.browse(int browserType);
```

其中browserType的取值为以下几种类型:

* ILelinkServiceManager.TYPE\_ALL：可以搜索到乐联和DLNA协议
* ILelinkServiceManager.TYPE\_LELINK：仅搜索乐联协议
<!--* ILelinkServiceManager.TYPE\_DLNA：仅搜索DLNA协议-->

2\) 设置搜索服务状态监听

```java
mLelinkServiceManager.setOnBrowseListener(mBrowseListener);
```

mBrowseListener 为服务状态监听

```java
private IBrowseListener BrowserListener = new IBrowseListener() {

       @Override
       public void onBrowse(int resultCode, List<LelinkServiceInfo> list) {

       }

};
```

其中list为搜索出来的结果信息，请根据这个结果信息来显示搜索到的设备列表。

**PS：onBrowse是在子线程工作，以下接口回调，如无特殊说明，都是在子线程回调**

3) 关闭搜索
```java
mLelinkServiceManager.stopBrowse();
```

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
- LelinkPlayer.CONNECT_INFO_DISCONNECT：连接断开
- LelinkPlayer.CONNECT_ERROR_FAILED：连接失败

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