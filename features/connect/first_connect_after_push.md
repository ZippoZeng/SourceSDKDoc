# 1\) 先连接，后推送

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