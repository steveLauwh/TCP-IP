## Three-Way Handshake

![Three-Way Handshake]()

** TCP 建立连接，需要经过三次握手操作 **

第一次握手：由 Client 向 Server (对于 Server 来说，处于 `LISTEN` 态)发送连接请求报文段，将 SYN 标志位置为 1，`Sequence Number` 为 `x`；然后，然后客户端处于 `SYN_SEND` 态，等待 Server 确认。

第二次握手：Server 收到 Client 的 SYN 报文段，需要对这个 SYN 报文段进行确认，设置 `Acknowledgement Number` 为 `x+1`(对 Client 的 Sequence Number 加1)；同时 Server 自己还要发送 SYN 请求信息，将 SYN 标志位置为 1，`Sequence Number 为 y`；然后 Server 将上述所有信息放到一个报文段(即 SYN+ACK 报文段)中，一起发送给 Client，此时 Server 处于 `SYN_RECV` 态。

第三次握手：Client 收到 Server 的 SYN+ACK 报文段，然后将 `Acknowledgement Number` 设置为 `y+1`(对 server 的 Sequence Number 加1)，向 Server 发送 ACK 报文段，这个报文段发送完毕后，Client 和 Server 都进入 `ESTABLISHED` 态。

## Four-Way Wavehand

![Four-Way Wavehand]()

** TCP 断开连接，需要经过四次挥手操作 **

第一次挥手：
