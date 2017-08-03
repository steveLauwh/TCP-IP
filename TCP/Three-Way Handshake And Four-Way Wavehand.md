## Three-Way Handshake

![](https://github.com/steveLauwh/TCP-IP/raw/master/TCP/image/tcp_open_close.jpg)

**TCP 建立连接，需要经过三次握手操作**

第一次握手：由 Client 向 Server (对于 Server 来说，处于 `LISTEN` 态)发送连接请求报文段，将 SYN 标志位置为 1，`Sequence Number` 为 `x`；然后，然后客户端处于 `SYN_SEND` 态，等待 Server 确认。

第二次握手：Server 收到 Client 的 SYN 报文段，需要对这个 SYN 报文段进行确认，设置 `Acknowledgement Number` 为 `x+1`(对 Client 的 Sequence Number 加1)；同时 Server 自己还要发送 SYN 请求信息，将 SYN 标志位置为 1，`Sequence Number 为 y`；然后 Server 将上述所有信息放到一个报文段(即 SYN+ACK 报文段)中，一起发送给 Client，此时 Server 处于 `SYN_RECV` 态。

第三次握手：Client 收到 Server 的 SYN+ACK 报文段，然后将 `Acknowledgement Number` 设置为 `y+1`(对 server 的 Sequence Number 加1)，向 Server 发送 ACK 报文段，这个报文段发送完毕后，Client 和 Server 都进入 `ESTABLISHED` 态。

## Four-Way Wavehand

** TCP 断开连接，需要经过四次挥手操作 **

第一次挥手：


当客户端和服务器通过三次握手建立了TCP连接以后，当数据传送完毕，肯定是要断开TCP连接的啊。那对于TCP的断开连接，这里就有了神秘的“四次分手”。
第一次分手：主机1（可以使客户端，也可以是服务器端），设置Sequence Number和Acknowledgment Number，向主机2发送一个FIN报文段；此时，主机1进入FIN_WAIT_1状态；这表示主机1没有数据要发送给主机2了；
第二次分手：主机2收到了主机1发送的FIN报文段，向主机1回一个ACK报文段，Acknowledgment Number为Sequence Number加1；主机1进入FIN_WAIT_2状态；主机2告诉主机1，我也没有数据要发送了，可以进行关闭连接了；
第三次分手：主机2向主机1发送FIN报文段，请求关闭连接，同时主机2进入CLOSE_WAIT状态；
第四次分手：主机1收到主机2发送的FIN报文段，向主机2发送ACK报文段，然后主机1进入TIME_WAIT状态；主机2收到主机1的ACK报文段以后，就关闭连接；此时，主机1等待2MSL后依然没有收到回复，则证明Server端已正常关闭，那好，主机1也可以关闭连接了。
至此，TCP的四次分手就这么愉快的完成了。当你看到这里，你的脑子里会有很多的疑问，很多的不懂，感觉很凌乱；没事，我们继续总结。
