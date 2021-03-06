﻿## TCP 知识点

* [TCP 头格式](https://github.com/steveLauwh/TCP-IP/blob/master/TCP/TCP%20Header%20Format.md)
* [TCP 三次握手和四次挥手](https://github.com/steveLauwh/TCP-IP/blob/master/TCP/Three-Way%20Handshake%20And%20Four-Way%20Wavehand.md)
* [TCP 状态机](https://github.com/steveLauwh/TCP-IP/blob/master/TCP/TCP%20FSM.md)
* [MSL 和 TIME_WAIT态的作用](https://github.com/steveLauwh/TCP-IP/blob/master/TCP/MSL%20And%20TIME_WAIT.md)
* [TCP 同时打开和同时关闭](https://github.com/steveLauwh/TCP-IP/blob/master/TCP/Open%20and%20Closed%20at%20the%20same%20time.md)
* [解决大量 TIME_WAIT](https://github.com/steveLauwh/TCP-IP/blob/master/TCP/Resolve%20a%20lot%20of%20TIME_WAIT.md)
* [TCP 超时和重传](https://github.com/steveLauwh/TCP-IP/blob/master/TCP/TCP%20Retransmission%20Mechanism.md)
* [TCP 滑动窗口](https://github.com/steveLauwh/TCP-IP/blob/master/TCP/TCP%20Sliding%20Window.md)
* [TCP 拥塞控制](https://github.com/steveLauwh/TCP-IP/blob/master/TCP/TCP%20Congestion%20Control.md)
* [Linux 下 TCP/IP 核心参数](https://github.com/steveLauwh/TCP-IP/blob/master/TCP/ip-systl.md)
* [TCP 疑问和解答](https://github.com/steveLauwh/TCP-IP/blob/master/TCP/TCP%20Q%26A.md)

![](https://github.com/steveLauwh/TCP-IP/raw/master/TCP/image/TCP.png)

## TCP 协议传输

当应用程序用 TCP 传送数据时，数据被送入协议栈，然后逐个通过每一层直到被当作一串比特流送入网络，其中每一层对收到的数据都要增加一些首部信息。

![](https://github.com/steveLauwh/TCP-IP/raw/master/TCP/image/tcptransfer.png)


## 参考资料

* (RFC 973) Transmission Control Protocol：https://tools.ietf.org/html/rfc793
* TCP 的那些事儿(上)：http://coolshell.cn/articles/11564.html
* TCP 的那些事儿(下)：http://coolshell.cn/articles/11609.html
* https://nmap.org/book/tcpip-ref.html
* http://www.tcpipguide.com/free/index.htm
