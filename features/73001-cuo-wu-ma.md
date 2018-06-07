#错误码
##连接错误码
```java
private IConnectListener mConnectListener = new IConnectListener() {

        @Override
        public void onConnect(LelinkServiceInfo serviceInfo, int extra) {
            Logger.d(TAG, "onConnect:" + serviceInfo.getName());
            if (null != mUIHandler) {
                String type = extra == TYPE_LELINK ? "Lelink" : extra == TYPE_DLNA ? "DLNA" : "IM";
                String text = serviceInfo.getName() + "连接" + type + "成功";
                mUIHandler.sendMessage(buildTextMessage(text));
                mUIHandler.sendMessage(buildStateMessage(IUIUpdateListener.STATE_CONNECT_SUCESS, text));
            }
        }

        @Override
        public void onDisconnect(LelinkServiceInfo serviceInfo, int what, int extra) {
            Logger.d(TAG, "onDisconnect:" + serviceInfo.getName()
                    + " disConnectType:" + what + " extra:" + extra);
            if (what == IConnectListener.CONNECT_INFO_DISCONNECT) {
                if (null != mUIHandler) {
                    String text = serviceInfo.getName() + "连接断开";
                    mUIHandler.sendMessage(buildTextMessage(text));
                    mUIHandler.sendMessage(buildStateMessage(IUIUpdateListener.STATE_DISCONNECT));
                }
            } else if (what == IConnectListener.CONNECT_ERROR_FAILED) {
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