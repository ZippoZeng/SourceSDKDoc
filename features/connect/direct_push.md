#直接推送
```java
LelinkPlayerInfo lelinkPlayerInfo = new LelinkPlayerInfo();
lelinkPlayerInfo.setLelinkServiceInfo(mLelinkServiceInfo);
lelinkPlayerInfo.setType(LelinkPlayerInfo.TYPE_VIDEO);
lelinkPlayerInfo.setUrl(url);
//lelinkPlayerInfo.setLocalPath(url);
leLinkPlayer.setDataSource(lelinkPlayerInfo);
leLinkPlayer.start();
```

如果您想断开连接
```java
leLinkPlayer.disConnect(mLelinkServiceInfo);
```

PS:SDK中关于两种模式的区别是判断是否设置了**setLelinkServiceInfo()**，如果mLelinkServiceInfo不为空，则认为是直接推送，如果为空，则认为是先连接了后在推送