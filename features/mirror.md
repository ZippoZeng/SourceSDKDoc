#镜像相关

##开始
```java
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

##结束
```java
mLelinkPlayer.stop();
```
##镜像设置
注意：镜像设置需要在startMirror之前
###setResolutionLevel(int level)
设置屏幕分辨率，默认为中等分辨率
- LelinkMirrorManager.RESOLUTION_HIGH：高分辨率
- LelinkMirrorManager.RESOLUTION_MID：中等分辨率
- LelinkMirrorManager.RESOLUTION_AUTO：根据发送端分辨率设置
###setBitrateLevel(int level)
设置比特率，默认为中比特率
- LelinkMirrorManager.BITRATE_HIGH：高比特率
- LelinkMirrorManager.BITRATE_MID：中比特率
- LelinkMirrorManager.BITRATE_LOW：低分辨率
###setAudioOpen(boolean isOn)
是否在镜像的时候录制声音，默认为false
- true：录制声音
- false：不设置声音