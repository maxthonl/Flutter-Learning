# WebView_Flutter
> 这是官方的webview插件, Android这一块底层是WebView, IOS则是WKWebView.

## 实现原理
### 1. WebView 主要参数
>+ onWebViewCreated   
WebView创建后的回调函数, 参数是实例化后的WebViewController
>+ initialUrl   
初始Url地址，存在自定义scheme不支持的情况
>+ javascriptMode = JavascriptMode.disabled  
目前只有两类, `disabled`, `unrestricted`
>+ javascriptChannels   
JS通道, 由 `name`, `onMessageReceived` 组成, 相当于在webview内创建了一个指定名称的可以postMessage的JS对象, 所以命名是有严格限制的,验证表达式为`^[a-zA-Z_][a-zA-Z0-9_]*\$`
>+ navigationDelegate  
Url跳转委托，控制是否跳转, 返回值是 `prevent`, `navigate`
>+ gestureRecognizers  
手势集合
>+ onPageStarted  
页面加载事件
>+ onPageFinished  
页面加载完成事件
>+ debuggingEnabled = false  
Android下参数, 调试开关
>+ gestureNavigationEnabled = false  
IOS下参数，是否支持水平滑动控制back-forward
>+ userAgent,
>+ initialMediaPlaybackPolicy = AutoMediaPlaybackPolicy.require_user_action_for_all_media_types  
媒体自动播放权限

### 2. WebViewController
> 使用MethodChannel封装VebView控制操作. 列举如下:  
>+ updateSettings
>+ loadUrl
>+ canGoBack
>+ canGoForward
>+ goBack
>+ goForward
>+ reload
>+ currentUrl
>+ evaluateJavascript
>+ addJavascriptChannels
>+ removeJavascriptChannels
>+ clearCache
>+ getTitle
