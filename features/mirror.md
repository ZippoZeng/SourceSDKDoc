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
                // 不支持镜像操作
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