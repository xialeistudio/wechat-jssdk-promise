#微信JSSDK Promise版本
微信JSSDK使用回调函数进行异步处理，但是某些接口会存在“回调嵌套”的问题，比如【播放一个服务器的录音文件】，需要：   
1. wx.downloadVoice
2. wx.playVoice
本程序对微信JSSDK进行的一层Promise包装，配合ES7的**async/await**可以解决此类问题
##注意   
1. 本程序依旧依赖微信JSSDK的js，请提前加载   
2. 微信原始JSSDK中的方法依旧可以使用  
##异步接口   
+ wx.config => wx.configAsync
+ wx.checkJsApi => wx.checkJsApiAsync
+ wx.onMenuShareTimeline => wx.onMenuShareTimelineAsync
+ wx.onMenuShareQQ => wx.onMenuShareQQAsync
+ wx.onMenuShareWeibo => wx.onMenuShareWeiboAsync
+ wx.onMenuShareQZone => wx.onMenuShareQZoneAsync
+ wx.chooseImage => wx.chooseImageAsync
+ wx.previewImage => wx.previewImageAsync
+ wx.uploadImage => wx.uploadImageAsync
+ wx.downloadImage => wx.downloadImageAsync
+ wx.startRecord => wx.startRecordAsync
+ wx.stopRecord => wx.stopRecordAsync
+ wx.onVoiceRecordEnd => wx.onVoiceRecordEndAsync
+ wx.playVoice => wx.playVoiceAsync
+ wx.pauseVoice => wx.pauseVoiceAsync
+ wx.stopVoice => wx.stopVoiceAsync
+ wx.onVoicePlayEnd => wx.onVoicePlayEndAsync
+ wx.uploadVoice => wx.uploadVoiceAsync
+ wx.downloadVoice => wx.downloadVoiceAsync
+ wx.translateVoice => wx.translateVoiceAsync
+ wx.getNetworkType => wx.getNetworkTypeAsync
+ wx.getLocation => wx.getLocationAsync
+ wx.startSearchBeacons => wx.startSearchBeaconsAsync
+ wx.stopSearchBeacons => wx.stopSearchBeaconsAsync
+ wx.onSearchBeacons => wx.onSearchBeaconsAsync
+ wx.scanQRCode => wx.scanQRCodeAsync
+ wx.chooseCard => wx.chooseCardAsync
+ wx.addCard => wx.addCardAsync
+ wx.chooseWXPay => wx.chooseWXPayAsync
##使用方法   
以 wx.chooseImage 为例   
```javascript
//使用wx.config
wx.config({
  //...
});
wx.ready(function() {
  //ready
});
wx.error(function(res) {
  //error
});
//可以看到非常繁琐
//使用wx.configAsyn
async function config() {
  try{
    await wx.configAsync({
      //...
    });
  }catch (e){
    //console.error(e.message);    
  }
}
```
##授权协议   
[MIT License](https://mit-license.org/)
##博客   
[每天进步一点点](https://www.ddhigh.com)