## TCP 滑动窗口

### TCP 滑动窗口的作用

TCP 是可靠的传输协议，所以必须要解决可靠的传输以及包乱序的问题。

TCP 滑动窗口主要有两个作用：提供 TCP 可靠性 和 提供 TCP 流控特性。

TCP 滑动窗口默认大小为 4096 个字节。

在 TCP 头部里有一个字段叫 Advertised-Window（即窗口大小）。这个字段是接收端告诉发送端自己还有多少缓冲区可以接收数据，于是发送端就可以根据这个剩余空间来发送数据，而不会导致接收端处理不过来。

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

### Q & A

**Zero Window：如果接收端处理缓慢，导致发送方的滑动窗口变为 0 了，怎么办？**

这时发送端就不发数据了，但发送端会发 ZWP（即Z ero Window Probe 技术）的包给接收方，让接收方回 ack 更新 Window 尺寸，一般这个值会设置成 3 次，每次大约30-60 秒。如果 3 次过后还是 0 的话，有的 TCP 实现就会发 RST 把连接断了。

**Silly Window Syndrome：即“糊涂窗口综合症”**

当发送端产生数据很慢、或接收端处理数据很慢，导致每次只发送几个字节，也就是我们常说的小数据包 —— 当大量的小数据包在网络中传输，会大大降低网络容量利用率。比如一个 20 字节的 TCP 首部 + 20 字节的 IP 首部+1个字节的数据组成的 TCP 数据报，有效传输通道利用率只有将近 1/40。

为了避免发送大量的小数据包，TCP 提供了 Nagle 算法，Nagle 算法默认是打开的，可以在 Socket 设置 TCP_NODELAY 选项来关闭这个算法。

## 参考资料

* [TCP 的那些事儿(下)](http://coolshell.cn/articles/11609.html)
* [Selective Repeat Protocol](https://media.pearsoncmg.com/aw/ecs_kurose_compnetwork_7/cw/content/interactiveanimations/selective-repeat-protocol/index.html)
