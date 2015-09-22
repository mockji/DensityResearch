# 管理App Android端接口文档
## 1. 使用说明
管理App为web端提供的服务与接口使用Cordova框架.把Cordva.js引入即可调用响应接口。  

* 引用js `<script type="text/javasscript" src="../cordova.js"></script>`
* 等待Ready事件*  

```
	var app = {
	// Application Constructor
	initialize: function() {
		this.bindEvents();
	},
	// Bind Event Listeners
	//
	// Bind any events that are required on startup. Common events are:
	// 'load', 'deviceready', 'offline', and 'online'.
	bindEvents: function() {
		document.addEventListener('deviceready', this.onDeviceReady, false);
	},
    // deviceready Event Handler
    //
    // The scope of 'this' is the event. In order to call the 'receivedEvent'
    // function, we must explicitly call 'app.receivedEvent(...);'
    onDeviceReady: function() {
        app.receivedEvent('deviceready');
    },
    // Update DOM on a Received Event
    receivedEvent: function(id) {
        var parentElement = document.getElementById(id);
        var listeningElement = parentElement.querySelector('.listening');
        var receivedElement = parentElement.querySelector('.received');
        listeningElement.setAttribute('style', 'display:none;');
        receivedElement.setAttribute('style', 'display:block;');
        console.log('Received Event: ' + id);
    }
};
app.initialize();
```
* 设备初始化完毕后,便可以调用相应接口,以打开相机为例  

```
function openCamera(){
    navigator.camera.getPicture(onSuccess, onFail, { quality: 50,
        destinationType: Camera.DestinationType.FILE_URI });
}

function onSuccess(imageURI) {
    var image = document.getElementById('myImage');
    image.src = imageURI;
}

function onFail(message) {
    alert('Failed because: ' + message);
}
``` 

##2.插件的概念 
cordova 把移动端提供的各种服务都拆分成插件，因此，响应服务的接口调用只有在移动端支持的情况下才会有作用。  

###2.1.目前支持的插件 
* Camera
* Sms
* Zbar（二维码扫描）
* NetworkInformation

###3. 以上内容大多来自Cordova,具体可参见http://cordova.apache.org/  

There are many different ways to style code with GitHub's markdown. If you have inline code blocks, wrap them in backticks: `var example = true`.  If you've got a longer block of code, you can indent with four spaces:

    if (isAwesome){
      return tr

GitHub also supports something called code fencing, which allows for multiple lines without indentation:

```
if (isAwesome){
  return true
}
```

And if you'd like to use syntax highlighting, include the language:

```javascript
if (isAwesome){
  return true
}
```
