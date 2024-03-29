# Cordova Baidu ASR 语音识别插件
================================

百度云ASR语音识别的cordova插件，支持iOS和android，仅在线识别。

由于iOS的静态库太大，仅保留 arm64 部分，删掉了 armv7, i386, x86_64，故只能在真机上调试。


## Installation

    cordova plugin add cordova-baidu-asr --variable APP_ID=<百度云提供> --variable API_KEY=<百度云提供> --variable SECRET_KEY=<百度云提供>


### Usage

在线识别:
```js
BaiduASR.startOnline((result)=>{
    console.log(JSON.stringify(result));
});
```

开始长语音:
```js
BaiduASR.startLong((res) => {
    var resultTxt = document.getElementById('result');
    var oldVal = resultTxt.value;
    resultTxt.value = res.result + '\n' + oldVal;
});
```

结束长语音:
```js
BaiduASR.stopLong();
```

### 注意

1. iOS的bundleID与Android的package名一样，百度云只需创建一个语音识别项目，在包名处输入该值。

2. 确保 AndroidManifest.xml 的 Application 中有三个参数，某些情况会被其他配置覆盖掉

```html
<meta-data android:name="com.baidu.speech.APP_ID" android:value="<百度云提供>" />
<meta-data android:name="com.baidu.speech.API_KEY" android:value="<百度云提供>" />
<meta-data android:name="com.baidu.speech.SECRET_KEY" android:value="<百度云提供>" />
```
