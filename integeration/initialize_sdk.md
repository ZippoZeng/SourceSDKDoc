#2、SDK初始化

```java
LelinkSetting lelinkSetting = new LelinkSetting.LelinkSettingBuilder(APPKEY, APPSECRET).build();
ILelinkServiceManager lelinkServiceManager = LelinkServiceManager.getInstance(context);
lelinkServiceManager.setLelinkSetting(lelinkSetting);
```

SDK初始化需要传入三个参数：
第一个参数为应用程序的context；
第二个参数是在开发者中心申请的APPKEY；
第三个参数是在开发者中心申请的APPSECRET

关于APPKEY & APPSECRET 的获取，[1、申请APPKEY & APPSECRET](introduction/register.md)