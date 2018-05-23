#播放控制
##获取连接的设备
```java
leLinkPlayer.getConnectServiceInfos();
```
##播放
```java
LelinkPlayerInfo lelinkPlayerInfo = new LelinkPlayerInfo();
lelinkPlayerInfo.setType(LelinkPlayerInfo.TYPE_VIDEO);
// lelinkPlayerInfo.setLocalPath(localurl);
leLinkPlayer.setDataSource(lelinkPlayerInfo);
leLinkPlayer.start();
```
##暂停
```java
leLinkPlayer.pause();
```
##恢复
```java
leLinkPlayer.resume();
```
##停止
```java
leLinkPlayer.stop();
```
##播放进度控制
```java
leLinkPlayer.seekTo(progress);
```
##音量控制
```java
leLlinkPlayer.setVolume(percent);
```
percent（百分比，float类型）的取值范围为0~1

##是否支持弹幕
```java
leLinkPlayer.isSupportDanmuku();
```

##发送弹幕
```java
DanmukuInfo danmukuInfo = new DanmukuInfo();
danmukuInfo.setAplha(aplha);
danmukuInfo.setContent(text);
danmukuInfo.setFontsize(size);
leLinkPlayer.sendDanmuku(danmukuInfo);
```

##


##释放
```java
leLinkPlayer.release();
```
