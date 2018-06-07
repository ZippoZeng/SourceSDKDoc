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
            String text = null;
            if (extra == IConnectListener.CONNECT_ERROR_IO) {
                text = serviceInfo.getName() + "连接失败";
            } else if (extra == IConnectListener.CONNECT_ERROR_IM_WAITTING) {
                text = serviceInfo.getName() + "等待确认";
            } else if (extra == IConnectListener.CONNECT_ERROR_IM_REJECT) {
                text = serviceInfo.getName() + "连接拒绝";
            } else if (extra == IConnectListener.CONNECT_ERROR_IM_TIMEOUT) {
                text = serviceInfo.getName() + "连接超时";
            } else if (extra == IConnectListener.CONNECT_ERROR_IM_BLACKLIST) {
                text = serviceInfo.getName() + "连接黑名单";
            }
            if (null != mUIHandler) {
                mUIHandler.sendMessage(buildTextMessage(text));
                mUIHandler.sendMessage(buildStateMessage(IUIUpdateListener.STATE_CONNECT_FAILURE, text));
            }
        }
    }

    };
```



##播控错误码