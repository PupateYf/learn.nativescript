# 平台区分
一套代码要做到在两端同时使用，不可避免需要对平台作出区分

### 在js中进行区分 

```xml
<Page loaded="init">
```

```js
exports.loaded = function (args) {
    page = args.object;
    if (page.ios) {
        //针对ios平台的操作
    }
}
```

### 在xml中进行区分

```xml
<Page>
    <Button ios:text="IOS" android:text="ANDROID" />
</Page>
```
