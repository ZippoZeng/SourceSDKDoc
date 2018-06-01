#ChangeLog

##3.0.6
1. 连接接口：
`ILelinkService.IServiceListener`变为`IConnectListener`
2. 连接方法：
```java
connect(lelinkServiceInfo,connectListener);
```
变为
```java
connect(lelinkServiceInfo);
```
3. ILelinkPlayerListener方法修改
start方法
```java
onPushStart(int linkType);
```
变为
```java
onStart();
```
stop方法
```java
onPushStop();
```
变为
```java
onStop();
```


