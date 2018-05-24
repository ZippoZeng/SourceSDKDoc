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
lelinkPlayerInfo.setUrl(url);
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
progress的单位为秒

<!--
##音量控制
```java
leLlinkPlayer.setVolume(percent);
```
percent（百分比，float类型）的取值范围为0~1
-->


<!--
##是否支持弹幕
```java
leLinkPlayer.isSupportDanmuku();
```
-->

<!--
##发送弹幕
```java
DanmukuInfo danmukuInfo = new DanmukuInfo();
danmukuInfo.setAplha(aplha);
danmukuInfo.setContent(text);
danmukuInfo.setFontsize(size);
leLinkPlayer.sendDanmuku(danmukuInfo);
```
-->
##增加音量
```java
leLinkPlayer.addVolume();
```
##减少音量
```java
leLinkPlayer.subVolume()
```

##释放
```java
leLinkPlayer.release();
```

##播放控制回调
```java
ILelinkPlayerListener playerListener = new ILelinkPlayerListener() {

        @Override
        public void onPlayStart(int linkType) {

        }

        @Override
        public void onPlayPause() {

        }

        @Override
        public void onPlayStop() {

        }

        @Override
        public void onSeek(int pPosition) {

        }

        @Override
        public void onInfo(int what, int extra) {

        }

        @Override
        public void onError(int what, int extra) {
            
        }

        @Override
        public void onVolumeChanged(float percent) {

        }

        @Override
        public void onPositionUpdate(long duration, long position) {

        }
    };
```
###onError(int what, int extra)
####what取值
- LelinkPlayer.TYPE_PLAYER = 1

####extra取值
- LelinkPlayer.CODE_TV_OFFLINE = -100,公网推送检测到接收端不在线
- LelinkPlayer.CODE_FILE_NOT_EXISTET = -200,推送本地文件不存在
- LelinkPlayer.CODE_DISCONNECT = -300,连接断开
- LelinkPlayer.CODE_CONNECT_FAILED = -400,连接失败
- LelinkPlayer.CODE_IM_NONSUPPORT = -500,公网推送不支持该推送类型
- LelinkPlayer.CODE_IMAGE_SEND_FAILED = -600,图片推送失败
- LelinkPlayer.CODE_NOT_CONNECTED_DEVICES = -700,没有设备















