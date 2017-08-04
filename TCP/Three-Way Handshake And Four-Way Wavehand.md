## Three-Way Handshake

![](https://github.com/steveLauwh/TCP-IP/raw/master/TCP/image/tcp_open_close.jpg)

**TCP 建立连接，需要经过三次握手操作**

**第一次握手**：由 Client 向 Server (对于 Server 来说，处于 `LISTEN` 态)发送连接请求报文段，将 SYN 标志位置为 1，`Sequence Number` 为 `x`；然后，然后客户端处于 `SYN_SEND` 态，等待 Server 确认。

**第二次握手**：Server 收到 Client 的 SYN 报文段，需要对这个 SYN 报文段进行确认，设置 `Acknowledgement Number` 为 `x+1`(对 Client 的 Sequence Number 加1)；同时 Server 自己还要发送 SYN 请求信息，将 SYN 标志位置为 1，`Sequence Number 为 y`；然后 Server 将上述所有信息放到一个报文段(即 SYN+ACK 报文段)中，一起发送给 Client，此时 Server 处于 `SYN_RECV` 态。

**第三次握手**：Client 收到 Server 的 SYN+ACK 报文段，然后将 `Acknowledgement Number` 设置为 `y+1`(对 server 的 Sequence Number 加1)，向 Server 发送 ACK 报文段，这个报文段发送完毕后，Client 和 Server 都进入 `ESTABLISHED` 态。

## Four-Way Wavehand

**TCP 断开连接，需要经过四次挥手操作**

**第一次挥手**：主机 A (既可以是 Client，也可以是 Server)，设置 `Sequence Number` 和 `Acknowledgement Number`，向主机 B 发送一个 `FIN` 报文段，此时，主机 A 进入`FIN_WAIT_1` 态；表示主机 A 没有数据要发送给主机 B。

**第二次挥手**：主机 B 收到了主机 A 发送的 FIN 报文段，然后向主机 A 回复一个 ACK 报文段，该 `Acknowledgement Number = Sequence Number+1`；主机 A 进入 `FIN_WAIT_2` 态；主机 B 告诉主机 A，也没有数据要发送，可以进行关闭连接。

**第三次挥手**：主机 B 向主机 A 发送 FIN 报文段，设置 `Sequence Number`，请求关闭连接，同时主机 B 进入 CLOSE_WAIT 态。

**第四次挥手**：主机 A 收到主机 B 发送 FIN 报文段，向主机 B 发送 ACK 报文段，该 `Acknowledgement Number = Sequence Number+1`，然后主机 A 进入 `TIME_WAIT` 态，主机 B 收到主机 A 的 ACK 报文段后，就关闭连接。此时，主机 A 等待 2MSL后依然没有收到回复，则证明主机 B 已正常关闭，那么，主机 A 也可以关闭连接。

## 为什么需要三次握手建立连接？

通信双方要互相通知对方自己的初始化 Sequence Number(Inital Sequence Number)，所以叫 SYN(Synchronize Sequence Number)。Sequence Number 是以后的数据通信的序号，用来保证应用层接收到的数据不会因为网络上的传输问题而乱序。

在谢希仁著《计算机网络》第四版中讲 “三次握手” 的目的是“为了防止已失效的连接请求报文段突然又传送到了服务端，因而产生错误”。

怎么理解上面这句话？ 

假设采用两次握手，当 Client 发出第一个连接请求报文段并没有丢失，只是在某个网络节点滞留，以致延误到**连接释放以后的某个时间**才到达 Server。本来这是一个早已失效的报文段。但是 Server 收到此失效的连接请求报文段后，就误以为是 Client 再次发出的一个新的连接请求；于是就向 Client 发出确认报文段，同意建立连接，但是对于 Client 来说，它并没有发出建立连接请求，所以不会理睬 Server 的确认，也不会向 Server 发送数据。这样就造成 Server 一直在等待。

所以采用 三次握手建立连接 主要目的是防止 Server 端一直等待，浪费资源。

## 为什么需要四次挥手断开连接？

因为 TCP 是一种面向连接的、可靠的、**全双工模式**，所以**发送方和接收方都需要 FIN 和 ACK**。只不过由一方发起，另一方是被动的，所以看上去是四次挥手。如果两边同时断开连接，那就会进入到 CLOSING 态，然后都到达 TIME_WAIT 态。

当主机 A 发出 FIN 报文段时，只是表示主机 A 已经没有数据要发送，但是还可以接收主机 B 的数据。

当主机 B 回复 ACK 报文段时，表示已经知道主机 A 没有数据要发送，那么主机 B 也应该告诉主机 A 没有数据要发送，所以需要给主机 A 发送 FIN 报文段。

当主机 A 收到主机 B 发送的 FIN 报文段，就给主机 B 发送 ACK 报文段，这样才能真正地断开连接。
