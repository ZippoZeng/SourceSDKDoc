#镜像相关
##状态监听器
```java
private ILelinkMirrorListener mILelinkMirrorListener = new ILelinkMirrorListener() {

    @Override
    public void onStateChange(int state) {

    }

    @Override
    public void onError(int what, int extra) {
        if (what == ILelinkMirrorListener.MIRROR_ERROR_INIT) {
            if (extra == ILelinkMirrorListener.MIRROR_ERROR_UNSUPPORTED) {
                // 不支持镜像操作：原因可能是版本小于5.0或不支持乐联协议
            } else if (extra == ILelinkMirrorListener.MIRROR_ERROR_REJECT_PERMISSION) {
                // 拒绝了镜像权限
            }
        }
    }
    
};

```


##开始
```java
LelinkMirrorManager lelinkMirrorManager = lelinkPlayer.getLelinkMirror();
lelinkMirrorManager.setMirrorListener();
```
##结束
```java
lelinkPlayer.stopMirror();
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