#镜像相关


## 1）设置镜像开始回调

## 2）镜像开始
```java
// 先连接
mLelinkPlayer.connect(lelinkServiceInfo);

LelinkPlayerInfo lelinkPlayerInfo = new LelinkPlayerInfo();
lelinkPlayerInfo.setType(LelinkPlayerInfo.TYPE_MIRROR);
lelinkPlayerInfo.setActivity(activity);
lelinkPlayerInfo.setLelinkServiceInfo(lelinkServiceInfo);
// 是否开启录制声音
lelinkPlayerInfo.setMirrorAudioEnable(true);
lelinkPlayerInfo.setResolutionLevel(mResolutionLevel);
lelinkPlayerInfo.setBitRateLevel(mBitrateLevel);
mLelinkPlayer.setDataSource(lelinkPlayerInfo);
mLelinkPlayer.start();
```
- ResolutionLevel的取值
    - ILelinkMirrorManager.RESOLUTION_HIGH：1080p分辨率
    - ILelinkMirrorManager.RESOLUTION_MID：720p分辨率
    - ILelinkMirrorManager.RESOLUTION_AUTO：屏幕分辨率
- MirrorBitrateLevel的取值
    - ILelinkMirrorManager.BITRATE_HIGH：高比特率
    - ILelinkMirrorManager.BITRATE_MID：中比特率
    - ILelinkMirrorManager.BITRATE_LOW：低比特率

## 3）镜像结束
```java
mLelinkPlayer.stop();
```