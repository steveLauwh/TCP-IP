## TCP 同时打开

![](https://github.com/steveLauwh/TCP-IP/raw/master/TCP/image/tcpopensimul.PNG)

两个应用程序同时执行打开的情况是可能的，虽然发生的可能性较低。每一端都发送一个 SYN，并传递给对方，且每一端都使用对端所知的端口作为本地端口。

例如：

主机 A 中有一应用程序使用 8888 作为本地端口，连接到主机 B 上的 9999 端口做主动打开。

主机 B 中有一应用程序使用 9999 作为本地端口，连接到主机 A 上的 8888 端口做主动打开。

TCP 协议遇到这种情况，只会打开一条连接。

这种同时打开的建立过程需要 4 次数据交换，而一个典型的连接建立只需要 3 次交换。

## TCP 同时关闭

![](https://github.com/steveLauwh/TCP-IP/raw/master/TCP/image/tcpclosesimul.png)

当应用程序同时发送 FIN，则在发送后会首先进入 FIN_WAIT_1 态。在收到对端的 FIN 后，回复一个 ACK，会进入 CLOSING 态。
在收到对端的 ACK 后，进入 TIME_WAIT 态。这种情况称为同时关闭。

