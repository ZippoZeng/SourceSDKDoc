#ChangeLog
##3.0.6
###连接接口
```java
ILelinkService.IServiceListener变为IConnectListener
其中
onConnect(LelinkServiceInfo serviceInfo)变为onConnect(LelinkServiceInfo serviceInfo,int extra)
onDisconnect(LelinkServiceInfo serviceInfo,int disConnectType)变为onDisconnect(LelinkServiceInfo serviceInfo,int what,int extra)

lelinkPlayer.connect(lelinkServiceInfo,mConnectListener)变为lelinkPlayer.connect(lelinkServiceInfo)
添加方法：
lelinkPlayer.setConnectListener(mConnectListener);
```
###播放状态回调
ILelinkPlayerListener有几个接口变动
```java
onPlayStart(int linkType)变为onStart()
onPlayPause()变为onPause()
onPlayStop()变为onStop()
onSeek(int position)变为onSeekComplete(int position)

```