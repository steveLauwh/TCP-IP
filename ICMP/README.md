## ICMP 知识点

### ICMP 含义

ICMP(INTERNET CONTROL MESSAGE PROTOCOL) 网络控制报文协议

ICMP 报文是 IP 报文的一部分；一个 IP 报文是由 IP 头部和 ICMP 报文组成。

ICMP 协议号为 1。

### ICMP 的两大功能

ICMP 报文两大功能：查询报文和差错报文。

IP 协议是不可靠协议，不能保证 IP 数据报能够成功的到达目的主机，无法进行差错控制，那么 ICMP 协议能够协助 IP 协议完成这些功能。

### ICMP 报文格式

ICMP 包有一个 8 字节长的包头，其中前 4 个字节是固定的格式，包含 8 位类型字段，8 位代码字段和 16 位的校验和；后 4 个字节根据 ICMP 包的类型而取不同的值。

### Destination Unreachable Message(目的不可达)

当路由器收到一个无法传递下去的 IP 报文时，会发送 ICMP 目的不可达报文（Type为3）给 IP 报文的源发送方。

报文中的 Code 就表示发送失败的原因:

* 0 = net unreachable;
* 1 = host unreachable;
* 2 = protocol unreachable;
* 3 = port unreachable;
* 4 = fragmentation needed and DF set;
* 5 = source route failed.

Codes 0, 1, 4, and 5 may be received from a gateway. Codes 2 and 3 may be received from a host.

### Time Exceeded Message(超时)

网络传输 IP 数据报的过程中，如果 IP 数据包的 TTL 值逐渐递减为 0 时，需要丢弃数据报。这时，路由器需要向源发送方发送 ICMP 超时报文(Type为11)，Code为 0，表示传输过程中超时了。

一个 IP 数据报可能会因为过大而被分片，然后在目的主机侧把所有的分片重组。如果主机迟迟没有等到所有的分片报文，就会向源发送方发送一个 ICMP 超时报文，Code为 1，表示分片重组超时了。

### Parameter Problem Message(参数错误报文)

当路由器或主机处理数据报时，发现因为报文头的参数错误而不得不丢弃报文时，需要向源发送方发送参数错误报文(Type为12)。当 Code 为 0 时，报文中的 Pointer 表示错误的字节位置。

### Source Quench Message(源冷却)

路由器在处理报文时会有一个缓存队列。如果超过最大缓存队列，将无法处理，从而丢弃报文。并向源发送方发一个 ICMP 源冷却报文(Type为4)。

### Redirect Message(重定向)

当路由器收到 IP 数据报，发现数据报的目的地址在路由表上没有，它就会发 ICMP 重定向报文(Type为5)给源发送方。

### Echo or Echo Reply Message(请求回显或回显应答)

Type(8) 是请求回显报文(Echo)

Type(0) 是回显应答报文(Echo Reply)

请求回显或回显应答报文属于查询报文。ping 就是用这种报文进行查询和回应。

### Timestamp or Timestamp Reply Message(时间戳或时间戳回复)

时间戳报文是用来记录收发以及传输时间的报文。

Originate Timestamp 记录的是发送方发送报文的时刻

Receive Timestamp 记录的是接收方收到报文的时刻

Transmit Timestamp 表示回显这最后发送报文的时刻

Type(13) 是 timestamp message

Type(14) 是 timestamp reply message

### Information Request or Information Reply Message(信息请求或信息响应)

Type(15) 是 information request message

Type(16) 是 information reply message

### ICMP 的应用 - ping

ping 使用的是 ICMP 协议，它发送 ICMP 回送请求消息给目的主机。

ICMP 协议规定：目的主机必须返回 ICMP 回送应答消息给源主机。如果源主机在一定时间内收到应答，则认为主机可达。

## 参考

* [ICMP-RFC792](https://www.rfc-editor.org/info/rfc792)

