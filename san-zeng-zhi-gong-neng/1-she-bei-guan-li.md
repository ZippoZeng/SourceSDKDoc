# 1、设备管理

如果您需要使用我们的设备管理服务，请在传入lelinkSetting的时候设置您的用户的唯一标识，则会自动开启设备管理的功能。

```java
lelinkSetting.setUserId(userId);
```

## 添加常用设备

```java
lelinkManager.addFavoriteDevice(lelinkServiceInfo);
```

## 更新常用设备

```java
lelinkManager.updateFavoriteDevice(lelinkServiceInfo);
```

## 删除常用设备

```java
lelinkManager.removeFavoriteDevice(lelinkServiceInfo);
```

当常用设备列表改变之后，我们会通过`IBrowseListener`的onBrowse\(\)方法将最新的设备列表的状态返回给你，你可以通过这个api

```java
lelinkServiceInfo.isFavorite();
```

来判断是否是您的常用设备

