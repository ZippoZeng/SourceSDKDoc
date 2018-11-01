#5、透传功能

## 1）播放媒资信息

 创建一个MediaAssetBean对象然后通过LelinkPlayerInfo的setMediaAsset方法设置进去SDK会自动完成透传

```java
public void playNetMediaWithAsset(String url, int type) {
    LelinkPlayerInfo lelinkPlayerInfo = new LelinkPlayerInfo();
    lelinkPlayerInfo.setType(type);
    lelinkPlayerInfo.setUrl(url);
    MediaAssetBean mediaAssetBean = new MediaAssetBean();
    mediaAssetBean.setActor("Actor name");
    mediaAssetBean.setDirector("Director name");
    mediaAssetBean.setId("id");
    mediaAssetBean.setName("media name");
    lelinkPlayerInfo.setMediaAsset(mediaAssetBean);
    mLelinkPlayer.setDataSource(lelinkPlayerInfo);
    mLelinkPlayer.start();
}
 ```

 ## 2）播放含防盗链header的url

 直接通过LelinkPlayerInfo的setHeader方法将数据设置进去SDK会自动完成透传

```java
public void playNetMediaWithHeader(String url, int type) {
    LelinkPlayerInfo lelinkPlayerInfo = new LelinkPlayerInfo();
    lelinkPlayerInfo.setType(type);
    lelinkPlayerInfo.setUrl(url);
    lelinkPlayerInfo.setHeader("{\"header\":\"header data\"}");
    mLelinkPlayer.setDataSource(lelinkPlayerInfo);
    mLelinkPlayer.start();
}
 ```

 ## 3）第三方应用直接使用透传接口发数据

  第三方APP可以直接通过LelinkPlayer对象中的sendRelevantInfo接口将数据直接透传给接收端

```java
mLelinkPlayer.sendRelevantInfo(ILelinkPlayerListener.RELEVANCE_DATA, "{\"data\":\"pass through\"}", appId, isSdk);
 ```

  -接口参数说明
      int option 透传类型  
      Object... values 第三方传递数据必须依次传递3个参数， 依次是：需要透传的数据、接收端的appid、透传给接收端SDK还是APP


 ## 4）透传数据回调接口设置

```java

        mLelinkPlayer.setRelevantInfoListener(new IRelevantInfoListener() {
            @Override
            public void onSendRelevantInfoResult(int option, String result) {
                LeLog.d(TAG, "option : " + option + " result: " + result);
            }

        });

```

不管是主动发起的透传回调还是被动接收的透传数据都会通过onSendRelevantInfoResult方法回调出来

 -接口参数说明
      int option 透传类型  
      String result  透传的返回结果或者收到的接收端数据
