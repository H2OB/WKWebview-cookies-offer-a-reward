悬赏￥2000.00RMB 解决WKWebview 注入多个不同domain的cookie

1.需求：app有一个功能 从接口获取很多不同域的cookie,然后注入到WKWebview中,要求第一次打开不跳转登录。期间网页需要经过多层重定向
例如，从接口获取到3个cookie,分别是 baidu.com、weibo.com、QQ.com。打开后进入wkwebview，第一个页面是baidu.com,然后加载完成他重定向到了weibo，要求微博能正确读取cookie

