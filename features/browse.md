# 1、服务搜索

## 1) 设置搜索监听
```java
mLelinkServiceManager.setOnBrowseListener(mBrowseListener);
```

mBrowseListener 为服务状态监听

```java
private IBrowseListener BrowserListener = new IBrowseListener() {

       @Override
       public void onBrowse(int resultCode, List<LelinkServiceInfo> list) {

       }

};
```

其中list为搜索出来的结果信息，请根据这个结果信息来显示搜索到的设备列表。

**PS：onBrowse是在子线程工作，以下接口回调，如无特殊说明，都是在子线程回调**

## 2) 开始搜索