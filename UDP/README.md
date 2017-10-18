## UDP 知识点

UDP 是无连接的用户数据报协议，端与端之间不需要建立连接，会发生丢包、乱序等情况。

应用程序必须关心 IP 数据报的长度，如果它超过了 MTU(以太网对数据帧的长度有一个限制，最大值是 1500，最大传输单元)，就要对 IP 数据报进行分片。

### UDP 首部

![](https://github.com/steveLauwh/TCP-IP/raw/master/TCP/image/udpheader.png)

IP 数据报的最大长度时 65535 字节，这是由 IP 首部 16 比特总长度字段所限制的。除去 20 字节的 IP 首部和 8 字节的 UDP 首部，UDP 数据报中用户数据的最长长度为 65507 字节。

## 参考资料

* http://blog.csdn.net/li_ning_/article/details/52117463
* http://www.cnblogs.com/glacierh/p/4854009.html
