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
设置屏幕分辨率
- LelinkMirrorManager.RESOLUTION_HIGH：高分辨率
- LelinkMirrorManager.RESOLUTION_MID：低分辨率
- LelinkMirrorManager.RESOLUTION_AUTO：根据屏幕分辨率自动适配
###setBitrateLevel(int level)
###setAudioMirrorOnOff(boolean isOn)
    - true：
    - false