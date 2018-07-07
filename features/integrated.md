## 4、播控服务

播控服务监听

```java
leLinkPlayer.setPlayerListener(playerListener);
```

playerListener为播控服务状态监听

```java
ILelinkPlayerListener playerListener = new ILelinkPlayerListener() {

        @Override
        public void onStart() {

        }

        @Override
        public void onPause() {

        }

        @Override
        public void onCompletion() {
            // 播放完成
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
         * @param percent 当前音量
         */
        @Override
        public void onVolumeChanged(float percent) {

        }

        /**
         * 进度更新回调
         * @param duration 媒体资源总长度
         * @param position 当前进度
         */
        @Override
        public void onPositionUpdate(long duration, long position) {

        }

    };
```

## 4、释放资源

当你想释放我们的sdk的时候，可以调用该方法进行释放

```java
if (null != mLelinkServiceManager) {
    mLelinkServiceManager.release();
}
```