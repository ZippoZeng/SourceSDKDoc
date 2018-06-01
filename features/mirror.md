#镜像相关
##状态监听器
```java
private ILelinkMirrorListener mMirrorListener= new ILelinkMirrorListener() {
    @Override
    public void onStateChange(int state) {
        
    }

    @Override
    public void onError(int what, int extra) {

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