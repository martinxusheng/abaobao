# abaobao
爱宝宝支付

<p><b>#1：页面引入js方法</b></p>
<pre>
function abaobaPay(callback) {
	if (window.WebViewJavascriptBridge) {
		callback(WebViewJavascriptBridge)
	} else {
		document.addEventListener('WebViewJavascriptBridgeReady', function() {
			callback(WebViewJavascriptBridge)
		}, false)
	}
};

//通过 abaobaPay 处理事件
abaobaPay(function(bridge) {
	//do something
})
</pre>

<b>#2：页面触发支付按钮</b>
<p><b>参数说明</b></p>
<pre>
<b>参数</b>        <b>参数类型</b>        <b>说明</b>
proid       String          商品编号
price       Float           商品价格

var data = {
	'proid': 'P001',
	'price': 100
};
bridge.send(data, function(responseData) {
	//如果调用成功返回data
	console.log(JSON.stringif(responseData));
})
</pre>

<b>#3：支付成功返回信息</b>
<p><b>返回说明</b></p>
<pre>
<b>参数</b>        <b>参数类型</b>        <b>说明</b>
orderid	   String      订单编号

bridge.callHandler('testObjcCallback', function(response) {
	//客户端返回信息
	console.log(JSON.stringif(response));
})
</pre>
