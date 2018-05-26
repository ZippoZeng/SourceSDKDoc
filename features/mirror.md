#镜像相关
##准备
```java
mLelinkPlayer.prepareMirror(activity, mMirrorListener);
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



```java

```
##结束