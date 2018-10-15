#2、SDK初始化

```java
LelinkSetting lelinkSetting = new LelinkSetting.LelinkSettingBuilder(APPID, APPSECRET).build();
ILelinkServiceManager lelinkServiceManager = LelinkServiceManager.getInstance(context);
lelinkServiceManager.setLelinkSetting(lelinkSetting);
```

SDK初始化需要传入三个参数：
第一个参数为应用程序的context；

第二个参数是在开发者中心申请的AppId；

第三个参数是在开发者中心申请的AppSecrect

**投屏SDK引入了Auth机制，当SDK初始化和browse方法同时进行时，由于Auth请求是异步线程，请求需要时间，故可能会导致第一次搜索失败第二次搜索成功。**

**解决办法：初始化和browse方法不能同时进行，可将初始化放在application**

关于AppId & AppSecrect 的获取，[1、申请AppId & AppSecrect](../introduction/register.md)