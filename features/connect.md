# 2、建立连接

## 1) 实例化LelinkPlayer
```java
LelinkPlayer leLinkPlayer = new LelinkPlayer(context);
```
## 2) 设置连接监听器
```java
IConnectListener connectListener = new IConnectListener() {

    @Override
    public void onConnect(LelinkServiceInfo serviceInfo, int extra) {

    }

    @Override
    public void onDisconnect(LelinkServiceInfo serviceInfo, int what, int extra) {

    }

};
```
LelinkSeviceInfo代表您正在操作的设备信息

其中onDisconnect()的what取值为：

- IConnectListener.CONNECT_INFO_DISCONNECT：连接断开
- IConnectListener.CONNECT_ERROR_FAILED：连接失败

## 3) 搜索开始连接
```java
leLinkPlayer.connect(lelinkServiceInfo);
```
## 4) 二维码连接

您还可以通过我们乐播投屏电视版提供的二维码来连接电视

```java
LelinkServiceInfo lelinkServiceInfo = lelinkServiceManager.addQRServiceInfo(qrCodeStr);
leLinkPlayer.connect(lelinkServiceInfo);
```
## 5) 断开连接
```java
leLinkPlayer.disConnect(lelinkServiceInfo);
```
## 6) 获取正在连接的设备
```java
leLinkPlayer.getConnectLelinkServiceInfos();
```
