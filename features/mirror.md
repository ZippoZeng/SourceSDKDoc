#镜像相关
##准备
```java
mLelinkPlayer.prepareMirror(activity, mMirrorListener);
```
注册镜像状态的监听器
```java
private ILelinkPlayer.IMirrorStateChangeListener mMirrorListener = new ILelinkPlayer.IMirrorStateChangeListener() {

    @Override
    public void onStateChange(int state) {
    
    }

};
```
##开始
然后在Activity中的onActivityResult中做以下配置
```java
 @Override
protected void onActivityResult(int requestCode, int resultCode, Intent data) {
    if (LelinkPlayer.MIRROR_PERMISSION_CODE == requestCode) {
        mLelinkPlayer.startMirror(requestCode, resultCode, data);
        return;
    }
}
```
##结束
```java

```