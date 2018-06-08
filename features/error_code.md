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
###onDisconnect的what取值
- IConnectListener.CONNECT_INFO_DISCONNECT：断开连接
- IConnectListener.CONNECT_ERROR_FAILED：连接错误

###onDisconnect的extra取值
- IConnectListener.CONNECT_ERROR_IO：IO错误
- IConnectListener.CONNECT_ERROR_IM_WAITTING：IM等待确认
- IConnectListener.CONNECT_ERROR_IM_REJECT：IM拒绝
- IConnectListener.CONNECT_ERROR_IM_TIMEOUT：IM连接超时
- IConnectListener.CONNECT_ERROR_IM_BLACKLIST：IM黑名单

##播控错误码
```java
ILelinkPlayerListener mLelinkPlayerListener = new ILelinkPlayerListener() {

        @Override
        public void onStart() {

        }

        @Override
        public void onPause() {
   
        }

        @Override
        public void onCompletion() {

        }

        @Override
        public void onStop() {

        }

        @Override
        public void onSeekComplete(int pPosition) {

        }

        @Override
        public void onInfo(int what, int extra) {

        }

        @Override
        public void onError(int what, int extra) {
            if (what == ILelinkPlayerListener.PUSH_ERROR_INIT) {
                if (extra == ILelinkPlayerListener.PUSH_ERRROR_FILE_NOT_EXISTED) {
                    // 文件不存在
                } else if (extra == ILelinkPlayerListener.PUSH_ERROR_IM_OFFLINE) {
                    // IM TV不在线
                } else if (extra == ILelinkPlayerListener.PUSH_ERROR_IMAGE) {
                    // 推送图片失败
                } else if (extra == ILelinkPlayerListener.PUSH_ERROR_IM_UNSUPPORTED_MIMETYPE) {
                   // 公网推送不支持此媒体类型
                } else {
                  // text = "未知";
                }
            } else if (what == ILelinkPlayerListener.MIRROR_ERROR_INIT) {
                if (extra == ILelinkPlayerListener.MIRROR_ERROR_UNSUPPORTED) {
                    if (null != mUIHandler) {
                        text = "不支持镜像";
                        mUIHandler.sendMessage(buildTextMessage(text));
                        mUIHandler.sendMessage(buildStateMessage(IUIUpdateListener.STATE_STOP_MIRROR, text));
                    }
                } else if (extra == ILelinkPlayerListener.MIRROR_ERROR_REJECT_PERMISSION) {
                    // 镜像权限拒绝
                }
            }
            mUIHandler.sendMessage(buildTextMessage(text));
            mUIHandler.sendMessage(buildStateMessage(IUIUpdateListener.STATE_PLAY_ERROR, text));
        }

        /**
         * 音量变化回调
         *
         * @param percent 当前音量
         */
        @Override
        public void onVolumeChanged(float percent) {
            Logger.d(TAG, "onVolumeChanged percent:" + percent);
        }

        /**
         * 进度更新回调
         *
         * @param duration 媒体资源总长度
         * @param position 当前进度
         */
        @Override
        public void onPositionUpdate(long duration, long position) {
            Logger.d(TAG, "onPositionUpdate duration:" + duration + " position:" + position);
            long[] arr = new long[] { duration, position };
            if (null != mUIHandler) {
                mUIHandler.sendMessage(buildStateMessage(IUIUpdateListener.STATE_POSITION_UPDATE, arr));
            }
        }

    };
```

int PUSH_ERROR_INIT = 800;
int PUSH_ERRROR_FILE_NOT_EXISTED = 801;
int PUSH_ERROR_IMAGE = 802;// 图片推送失败
int PUSH_ERROR_IM_UNSUPPORTED_MIMETYPE = 803;// 公网推送不支持该推送类型
int PUSH_ERROR_IM_OFFLINE = 804;
int PUSH_ERROR_IO = 830;