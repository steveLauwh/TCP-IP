## TCP 状态机

![](https://github.com/steveLauwh/TCP-IP/raw/master/TCP/image/tcpfsm.png)

通常情况下，一个正常的 TCP 连接，都会有三个阶段：

1. TCP 三次握手

2. 数据传送

3. TCP 四次挥手

## TCP 三次握手的状态

1. LISIEN 态：在连接前，服务端需要打开一个 socket 进行监听。(服务端)

2. SYN_SENT 态：当客户端 socket 执行 connect 连接时，先发送 SYN 报文请求建立连接，然后它会进入 SYN_SENT 态。 (客户端)

3. SYN_RCVD 态：服务端收到客户端发的请求，然后向客户端发出 ACK 确认客户端的 SYN，并且向客户端发送一个 SYN 报文，进入 SYN_RCVD 态。(服务端)

4. ESTABLISHED 态：表示双方连接已经建立。

## TCP 四次挥手的状态

1. FIN_WAIT_1 态：当 socket 在 ESTABLISHED 态时，主动关闭端(active close)要关闭连接，于是向对方发送 FIN 报文请求主动关闭连接，之后进入 FIN_WAIT_1 态。(主动方)

2. CLOSE_WAIT 态：表示在等待关闭，当被动关闭端(passive close)收到 FIN 报文后，就发出 ACK 回应 FIN 请求，之后进入 CLOSE_WAIT 态。注意，主动方发出了 FIN，表示主动方现在没有数据要发送，但是作为被动方自己仍然可以发送数据。(被动方)

3. FIN_WAIT_2 态：表示半连接，当主动关闭端接收到 ACK 后，同时等待被动方发出 close 连接，之后进入 FIN_WAIT_2 态。(主动方)

4. LAST_ACK 态：当被动关闭端一段时间后，接收到文件结束符的应用程序将调用 close 关闭连接，这样被动方也发送一个 FIN 请求，等待对方的 ACK，之后进入 LAST_ACK 态。(被动方)

5. TIME_WAIT 态：当主动关闭端接收到 FIN 报文请求后，就向被动方发送 ACK，之后进入 TIME_WAIT 态。作用是等待足够的时间(2MSL)以确保被动方接收到连接中断请求的确认。(主动方)

6. CLOSING 态：当两边同时断连接，那就会就进入到 CLOSING 态。

7. CLOSED 态：最后一步，当被动关闭端接收 ACK 后，就进入 CLOSED 态，断开连接结束。

## 在四次挥手过程中，收到主动方的 FIN 报文通知后，为什么不一起把 ACK 报文和 FIN 报文发送给主动方？

当被动方收到主动方的 FIN 报文通知，仅仅表示主动方没有数据发送给被动方，作为被动方未必所有的数据都全部发送给主动方，所以先回应 ACK 报文，当没有数据要发送给主动方，就再发送 FIN 报文给主动方来表示可以关闭连接了。
