悬赏￥2000.00RMB 解决WKWebview 注入多个不同domain的cookie

1.需求：app有一个功能 从接口获取很多不同域的cookie,然后注入到WKWebview中,要求第一次打开不跳转登录。期间网页需要经过多层重定向
例如，从接口获取到3个cookie,分别是 baidu.com、weibo.com、QQ.com。打开后进入wkwebview，第一个页面是baidu.com,然后加载完成他自动跳转到了weibo.com，期间weibo.com不打开新页面，要求weibo.com能正确读取cookie
2.已试过:
[[WKWebsiteDataStore defaultDataStore].httpCookieStore getAllCookies:^(NSArray<NSHTTPCookie *> * _Nonnull cookies) {

        NSInteger count = cookies.count;
        __block NSInteger deleteCount = 0;
        for (NSHTTPCookie * cookie in cookies) {

            [[WKWebsiteDataStore defaultDataStore].httpCookieStore deleteCookie:cookie completionHandler:^{
                deleteCount++;
                if(deleteCount == count){

                    dispatch_async(dispatch_get_main_queue(), ^{
                        [self fetchHistoryCookies];
                    });

                }
            }];
        }

    }];
    以及在loadRequest时header中加入cookie 和 doucment.cookie 
   3.结果 首次打开网页仍然会跳转登录，但是是偶尔
   
   最后，我的QQ:4799862，跪求各位大佬帮忙解决，说话算话

