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
其中onDisconnect()的what取值为：

- IConnectListener.CONNECT_INFO_DISCONNECT：连接断开
- IConnectListener.CONNECT_ERROR_FAILED：连接失败

## 3) 开始连接