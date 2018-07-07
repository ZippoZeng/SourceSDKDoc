# 1、SDK导入及配置

请将aar到工程中的libs中，
![import\_aar](/assets/import_aar.png)
然后在module的build.gradle中添加以下配置

在android节点中添加以下配置

```groovy
repositories {
    flatDir {
        dirs 'libs'
    }
}
```

在dependencies中添加以下配置

```groovy
compile(name: 'source-sdk', ext: 'aar')
```

接下来，您就可以调用我们的api了

