#错误码
##连接错误码
```java
private IConnectListener mConnectListener = new IConnectListener() {

    @Override
    public void onConnect(LelinkServiceInfo serviceInfo, 
    }

    @Override
    public void onDisconnect(LelinkServiceInfo serviceInfo, int what, int extra) {
        if (what == IConnectListener.CONNECT_INFO_DISCONNECT) {
        // 断开连接
        } else if (what == IConnectListener.CONNECT_ERROR_FAILED) {
            // 连接错误
            if (extra == IConnectListener.CONNECT_ERROR_IO) {
                // IO错误
            } else if (extra == IConnectListener.CONNECT_ERROR_IM_WAITTING) {
                // IM等待确认
            } else if (extra == IConnectListener.CONNECT_ERROR_IM_REJECT) {
                // IM连接拒绝
            } else if (extra == IConnectListener.CONNECT_ERROR_IM_TIMEOUT) {
                // IM连接超时
            } else if (extra == IConnectListener.CONNECT_ERROR_IM_BLACKLIST) {
                // IM黑名单
            }
        }
    }

    };
```



##播控错误码