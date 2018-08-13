# Hybrid

- hybrid是什么，为何用hybrid

 hybrid是客户端和前端的混合开发

  * 存在的价值

     无需app审核，快速迭代更新

     体验流畅

     减少开发成本，沟通成本，双端公用一套代码

  * file://协议: 本地文件，快 http(s):网络协议，慢

  * webview-用于加载H5页面，小型浏览器内核，app的一个组件

  * 使用NA：体验要求极致，变化不频繁

  * 使用hybrid： 体验要求高，变化频繁

  * 使用H5：体验要求低，使用频率低

- 介绍一下hybrid更新和上线流程

  掌握流程图

  服务端版本和zip包的维护

  更新zip包之前对比版本号

  zip下载解压和覆盖

- hybrid和H5的区别

  略

- 前端js和客户端如何通讯

  微信JS-SDK

  js和客户端通讯的基本形式

     客户端获取内容，然后js通讯拿到内容，再渲染（客户端获取可以提前获取），类似ajax,jsonp

  schema协议简介和使用

     前端和客户端的通信协议

  schema使用的封装

  ```
   var iframe = document.createElement('iframe');

   iframe.style.display = 'none';
   iframe.src = 'wexin://dl/scan?k1=v1&k1=v2&callback=_wexin_scan_callback'; //iframe访问schema
   var body = document.body || document.getElementByTagName('body');
   body.appendChild(iframe);
   setTimeout(function(){
      body.removeChild(iframe);
      iframe = null;
   });
  
  // 傻瓜式调用，不用再自定义全局函数
  window.invoke.share({title: 'XXX', content:'XXX'}, function(result){
     if(result.error == 0){
        alert('success');
     }else{
        console.lot('fail');
     }
  });

  // 封装
  window.invoke = {
    share: invokeShare
  };

  function invokeShare(data, callback) {
     _invoke('share', data, callback)
  };

  _invoke(action, data, callback){
     var schema='myapp://utils';
     schema += '/' + action;

     schema += '?a=a';
     var key;
     for (key in data) {
        if (data.hasOwnProperty(key)) {
           schema += '&' + key + '=' + data[key]
        }
      }
   }
  
  var callbackName = '';
  if (typeof callback === 'string') {
      callbackName = callback;
  } else {
     callbackName = action + Date.now();
     window[callBackName] = callback
  }

  schema += '&callback=' + callbackName;
  // iframe 中调用schema --- 省略N行

  ```

- 内置上线

 将以上封装的代码打包，叫做invoke.js,内置到客户端

 客户端每次启动webview,都默认执行invoke.js

 本地加载，免去网络加载的时间更快

 本地加载，没有网络请求，黑客看不到schema协议，更安全

- 通讯的基本形式：调用能力，传递参数，监听回调




