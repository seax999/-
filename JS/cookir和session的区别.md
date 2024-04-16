### Cookie 和 Session 的区别



- Cookie 存储在客户端，而 Session 存储在服务端
- Cookie 是针对网状的一些信息的存储，而 Session 是针对所有用户的
- Cookie 存储有大小限制，而 session 可以存储任意数据，只要定时清除就行
- Cookie 的获取有同源限制，session存储在服务端则没有
- Cookie 存储的值是字符串，session 存储的是对象
- Cookie 存储在客户端，有被篡改的可能，而 session 则没有



扩展：

#### Cookie、 sessionStrange、localstrange 的区别

- Cookie、sessionStrange、localstrange 全部存储在客户端
- Cookie 存储的容量有效只有4k左右，而 sessionStrange 和 localstrange 没有限制
- Cookie 存储的数据有时间限制，localstrange 可以长期存储，sessionStrange 页面关闭即清除
- 三者都有同源访问限制
- Cookie 会在http请求中携带，另外两者则不会



#### Cookie 存储的弊端

- 每个域名下的Cookie存储有上限
- Cookie 的存储容量有限
- Cookie 会因为有效时间而被清除，而且浏览器会清除过期或是不常用的Cookie
- Cookie 存储在客户端，有被篡改或是拦截的可能
- Cookie 的获取有同源限制
- Cookie 会额外占用请求的带宽，对于网络请求花费有一定影响