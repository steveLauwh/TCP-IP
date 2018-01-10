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

**6. FTP 协议**

FTP 21 端口用于连接(认证)，20 端口用于传输数据。

FTP 是基于 TCP 的，所以先要进行三次握手。

FTP 文件传输的两种模式：被动模式和主动模式。

FTP 传输过程：TCP 握手，FTP 认证(信令)，请求连接(信令)，TCP 握手(数据)，文件传输，TCP 挥手(数据)，FTP 断开(信令)，TCP 挥手。

**7. SCTP 协议**

SCTP 流控制传输协议，是一个传输层协议，是提供基于不可靠传输业务的协议之上的可靠的数据传输协议。

SCTP 的设计用于通过 IP 网传输 SCN(信令通信网) 窄带信令消息。

SCTP 的特性：面向连接、需要握手、提供重传确认机制、有拥塞控制机制；修复了 TCP 的诸多缺陷。

SCTP 的主要改进：四次握手，从根源上杜绝 SYN 泛洪攻击；多宿主连接(同时配置多条偶联)；多流特性。

**8. ICMP 协议**

ICMP 是 Internet 控制协议；用于在 IP 主机、路由器之间传递控制消息。控制消息是网络通不通、主机是否可达、路由是否可用等网络本身的消息。

ICMP 的两大核心功能：查询和差错。

**9. DNS 协议**

DNS 域名系统，因特网上作为域名和 IP 地址相互映射的一个分布式数据库。

DNS 协议运行在 UDP 协议之上，使用端口 53.

DNS 两大功能：网址解析；域控制器解析。

DNS 的两个查询方式：递归查询，迭代查询。

DNS 的 round-robin 工作模式(一个网址指向多个 IP，负载均衡)。

## 参考

* [TCP协议疑难杂症全景解析](http://blog.csdn.net/dog250/article/details/6612496)
* [UDP协议疑难杂症全景解析](http://blog.csdn.net/dog250/article/details/6896949)
* [从 TCP 三次握手说起：浅析 TCP 协议中的疑难杂症(1)](https://www.qcloud.com/community/article/164816001481011785)
* [从 TCP 三次握手说起–浅析 TCP 协议中的疑难杂症(2)](https://www.qcloud.com/community/article/164816001481011795)
* [TCP 关闭连接(为什么会能 Time_wait, Close_wait)?](https://www.qcloud.com/community/article/164816001481011814)
* [TCP 异常关闭研究分析](https://www.qcloud.com/community/article/164816001481011820)
* [告知你不为人知的 UDP：连接性和负载均衡](https://www.qcloud.com/community/article/812444001486438028)
* [告知你不为人知的 UDP：疑难杂症和使用](https://www.qcloud.com/community/article/848077001486437077)
