## Q & A

**1. TCP 和 UDP 区别？**

* TCP 提供面向连接、可靠的字节流服务；UDP 提供无连接、不可靠的数据报服务
* 对系统资源的要求(TCP 较多，UDP 少)
* TCP 保证数据正确性，数据顺序；UDP 不能保证
* TCP 有超时重发、流量控制等机制，而 UDP 没有

具体可看这篇文章：[TCP与UDP差异对比分析](http://www.jianshu.com/p/eb50d2152646)

**2. cookie 机制和 session 机制**

* session 在服务器端，cookie 在客户端（浏览器）
* session 默认被存在在服务器的一个文件里（不是内存）
* 用户验证这种场合一般会用 session 
* session 的运行依赖 session id，而 session id 是存在 cookie 中的

**3. HTTP 和 HTTPS 区别** 

* HTTP 端口80，HTTPS 端口443
* HTTP 是明文传输
* HTTPS 是具有安全性 SSL 加密传输协议
* HTTPS 比较耗性能，需要到 CA 申请证书

**4. POST 和 GET 区别**

* GET 一般用于获取/查询资源信息，而 POST 一般用于更新资源信息。
* GET 请求的数据会附在 URL 之后，不安全，提交数据最多 1024 个字节
* POST 把提交的数据则放置在是 HTTP 包的包体中，安全

**5. 打开网页到页面显示的整个过程**

* 浏览器向 DNS 服务器查找输入 URL 对应的 IP 地址
* DNS 服务器返回网站的 IP 地址
* 浏览器根据 IP 地址与目标 Web 服务器，在 80 端口上建立 TCP 连接，建立一个 socket
* 浏览器获取请求页面的 html
* 浏览器渲染 HTML

**6. FTP 端口**

FTP 21 端口用于连接(认证)，20 端口用于传输数据。



## 参考

* [TCP协议疑难杂症全景解析](http://blog.csdn.net/dog250/article/details/6612496)
* [UDP协议疑难杂症全景解析](http://blog.csdn.net/dog250/article/details/6896949)
* [从 TCP 三次握手说起：浅析 TCP 协议中的疑难杂症(1)](https://www.qcloud.com/community/article/164816001481011785)
* [从 TCP 三次握手说起–浅析 TCP 协议中的疑难杂症(2)](https://www.qcloud.com/community/article/164816001481011795)
* [TCP 关闭连接(为什么会能 Time_wait, Close_wait)?](https://www.qcloud.com/community/article/164816001481011814)
* [TCP 异常关闭研究分析](https://www.qcloud.com/community/article/164816001481011820)
* [告知你不为人知的 UDP：连接性和负载均衡](https://www.qcloud.com/community/article/812444001486438028)
* [告知你不为人知的 UDP：疑难杂症和使用](https://www.qcloud.com/community/article/848077001486437077)
