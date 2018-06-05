# 1\) 先连接，后推送

1. 先连接，连接状态可以在mConnectListener获得

   ```java
   leLinkPlayer.connect(mLelinkServiceInfo, mConnectListener);
   ```

2. 连接成功后推送

   ```java
   LelinkPlayerInfo lelinkPlayerInfo = new LelinkPlayerInfo();
   lelinkPlayerInfo.setType(LelinkPlayerInfo.TYPE_VIDEO);
   //lelinkPlayerInfo.setLocalPath(url);
   lelinkPlayerInfo.setUrl(url);
   leLinkPlayer.setDataSource(lelinkPlayerInfo);
   leLinkPlayer.start();
   ```

   3、断开连接

   ```java
   leLinkPlayer.disConnect(mLelinkServiceInfo);
   ```

## 二维码连接

您还可以通过我们乐播投屏电视版提供的二维码来连接电视

```java
LelinkServiceInfo lelinkServiceInfo = mLelinkServiceManager.addQRServiceInfo(qrCodeStr);
leLinkPlayer.connect(lelinkServiceInfo, mConnectListener);
```

