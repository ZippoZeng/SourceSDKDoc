#ChangeLog

##3.0.6
1. 连接接口：
`ILelinkService.IServiceListener`变为`IConnectListener`
2. 连接方法：
```java
connect(lelinkServiceInfo,connectListener)
```
变为
```java
connect(lelinkServiceInfo)
```
3. ILelinkPlayerListener方法修改