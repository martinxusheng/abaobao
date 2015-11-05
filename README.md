# abaobao
爱宝宝支付

第一步：页面引入js方法
<pre>
function abaobaPay(callback) {
	if (window.WebViewJavascriptBridge) {
		callback(WebViewJavascriptBridge)
	} else {
		document.addEventListener('WebViewJavascriptBridgeReady', function() {
			callback(WebViewJavascriptBridge)
		}, false)
	}
}
</pre>

第二部：页面触发支付按钮

<pre>
<b>参数</b>        <b>参数类型</b>        <b>说明</b>
proid       String          商品编号
price       Float           商品价格

abaobaPay(function(bridge) {
	var button = document.getElementById('paybtn');
	button.onclick = function(e) {
		e.preventDefault();
		//产品明细
		var data = {
			'proid': 'P001',
			'price': 100
		};
		bridge.send(data, function(responseData) {
			log('JS got response', responseData)
		})
	}
})
</pre>
