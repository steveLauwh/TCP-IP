## TCP 滑动窗口

### TCP 滑动窗口的作用

TCP 是可靠的传输协议，所以必须要解决可靠的传输以及包乱序的问题。

TCP 滑动窗口主要有两个作用：提供 TCP 可靠性 和 提供 TCP 流控特性。

TCP 滑动窗口默认大小为 4096 个字节。

### TCP 滑动窗口的原理

TCP 滑动窗口分为发送窗口和接收窗口。

> 对于 TCP 会话的发送方，任何时候在其发送缓存内的数据都可以分为 4 类：

* 已经发送并得到对端 ACK
* 已经发送但还未收到对端 ACK
* 未发送但对端允许发送
* 未发送且对端不允许发送

> 对于 TCP 的接收方，某一时刻在它的接收缓存内存分为 3 类：

* 已接收
* 未接收准备接收 (接收窗口)
* 未接收并未准备接收

## 参考资料

* [TCP 的那些事儿(下)](http://coolshell.cn/articles/11609.html)
* [Selective Repeat Protocol](https://media.pearsoncmg.com/aw/ecs_kurose_compnetwork_7/cw/content/interactiveanimations/selective-repeat-protocol/index.html)
