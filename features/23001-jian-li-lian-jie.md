# 2、建立连接

## 1) 实例化LelinkPlayer
```java
LelinkPlayer leLinkPlayer = new LelinkPlayer(context);
```
## 2) 设置连接监听器
```java
IConnectListener connectListener = new IConnectListener() {

    @Override
    void onConnect(LelinkServiceInfo serviceInfo, int extra) {
    
    }
    
    @Override
    void onDisconnect(LelinkServiceInfo serviceInfo, int what, int extra) {
    
    }
};
```