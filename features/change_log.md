#ChangeLog

##3.0.6
###1. 连接
```java
ILelinkService.IServiceListener变为IConnectListener
connect(lelinkServiceInfo,connectListener)-->connect(lelinkServiceInfo)


```
###2. ILelinkPlayerListener方法修改
```java
onPushStart(int linkType)--->onStart()
onPushPause()-->onPause()
onPushStop()-->onStop()
onSeek()-->onSeekComplete()
```


