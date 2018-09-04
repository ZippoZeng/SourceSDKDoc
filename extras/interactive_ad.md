# 1、互动广告
如果您想要使用互动广告的功能，首先必须得注册监听器

## 1) 设置监听
```java
InteractionAdListener interactionAdListener = new InteractionAdListener() {

    @Override
    public void onAdLoaded(AdInfo adInfo) {

    }

};
```
interactionAdListener 为互动广告监听
```java
mLelinkPlayer.setInteractionAdListener(interactionAdListener);
```

## 2) 广告播放上报
```java
mLelinkPlayer.onAdShow(mAdInfo, status);
```
AdInfo为onAdLoaded方法返回来的值

status的取值为
- LelinkPlayer.STATUS_SUCCESS
- LelinkPlayer.STATUS_FAILURE

## 3) 广告播放完成上报
```java
mLelinkPlayer.onAdClosed(mAdInfo, duration, status);
```
- AdInfo为onAdLoaded方法返回来的值
- duration：广告播放时长
- status：的取值为
    - LelinkPlayer.STATUS_SUCCESS
    - LelinkPlayer.STATUS_FAILURE

## 4) 关于AdInfo参数说明