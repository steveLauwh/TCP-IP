## Q & A

**1. TCP 和 UDP 区别？**

* TCP 提供面向连接、可靠的字节流服务；UDP 提供无连接、不可靠的数据报服务
* 对系统资源的要求(TCP 较多，UDP 少)
* TCP 保证数据正确性，数据顺序；UDP 不能保证
* TCP 有超时重发、流量控制等机制，而 UDP 没有

具体可看这篇文章：[TCP与UDP差异对比分析](http://www.jianshu.com/p/eb50d2152646)



## 参考

* [TCP协议疑难杂症全景解析](http://blog.csdn.net/dog250/article/details/6612496)
* [UDP协议疑难杂症全景解析](http://blog.csdn.net/dog250/article/details/6896949)
* [从 TCP 三次握手说起：浅析 TCP 协议中的疑难杂症(1)](https://www.qcloud.com/community/article/164816001481011785)
* [从 TCP 三次握手说起–浅析 TCP 协议中的疑难杂症(2)](https://www.qcloud.com/community/article/164816001481011795)
* [TCP 关闭连接(为什么会能 Time_wait, Close_wait)?](https://www.qcloud.com/community/article/164816001481011814)
* [TCP 异常关闭研究分析](https://www.qcloud.com/community/article/164816001481011820)
* [告知你不为人知的 UDP：连接性和负载均衡](https://www.qcloud.com/community/article/812444001486438028)
* [告知你不为人知的 UDP：疑难杂症和使用](https://www.qcloud.com/community/article/848077001486437077)
