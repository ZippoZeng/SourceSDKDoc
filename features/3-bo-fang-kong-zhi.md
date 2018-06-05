# 3、播放控制

## 获取连接的设备

```java
leLinkPlayer.getConnectServiceInfos();
```

## 播放

```java
LelinkPlayerInfo lelinkPlayerInfo = new LelinkPlayerInfo();
lelinkPlayerInfo.setType(LelinkPlayerInfo.TYPE_VIDEO);
// lelinkPlayerInfo.setLocalPath(localurl);
lelinkPlayerInfo.setUrl(url);
leLinkPlayer.setDataSource(lelinkPlayerInfo);
leLinkPlayer.start();
```

## 暂停

```java
leLinkPlayer.pause();
```

## 恢复

```java
leLinkPlayer.resume();
```

## 停止

```java
leLinkPlayer.stop();
```

## 播放进度控制

```java
leLinkPlayer.seekTo(progress);
```

progress的单位为秒

## 增加音量

```java
leLinkPlayer.addVolume();
```

## 减少音量

```java
leLinkPlayer.subVolume()
```

## 释放

```java
leLinkPlayer.release();
```

## 播放控制回调

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

### onError\(int what, int extra\)

#### what取值

* LelinkPlayer.TYPE\_PLAYER = 1

#### extra取值

* LelinkPlayer.CODE\_TV\_OFFLINE = -100,公网推送检测到接收端不在线
* LelinkPlayer.CODE\_FILE\_NOT\_EXISTET = -200,推送本地文件不存在
* LelinkPlayer.CODE\_IM\_NONSUPPORT = -500,公网推送不支持该推送类型
* LelinkPlayer.CODE\_IMAGE\_SEND\_FAILED = -600,图片推送失败
* LelinkPlayer.CODE\_NOT\_CONNECTED\_DEVICES = -700,没有设备

