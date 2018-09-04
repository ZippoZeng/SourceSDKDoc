# 1、互动广告

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
