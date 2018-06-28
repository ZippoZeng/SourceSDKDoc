#错误码
##连接错误码
```java
private IConnectListener mConnectListener = new IConnectListener() {

    @Override
    public void onConnect(LelinkServiceInfo serviceInfo, int what) {
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

        }

        /**
         * 音量变化回调
         *
         * @param percent 当前音量
         */
        @Override
        public void onVolumeChanged(float percent) {

        }

        /**
         * 进度更新回调
         *
         * @param duration 媒体资源总长度
         * @param position 当前进度
         */
        @Override
        public void onPositionUpdate(long duration, long position) {

        }

    };
```
##onError的what取值
- ILelinkPlayerListener.PUSH_ERROR_INIT：推送初始化错误
- ILelinkPlayerListener.PUSH_ERROR_PLAY：推送播放错误
- ILelinkPlayerListener.MIRROR_ERROR_INIT：镜像初始化错误
- ILelinkPlayerListener.MIRROR_ERROR_PREPARE：镜像准备错误
- ILelinkPlayerListener.MIRROR_ERROR_CODEC：镜像编码错误