## 解决大量 TIME_WAIT

查看 TCP 的状态连接：`netstat -ant`

TIME_WAIT 是个很重要的状态，当在大并发的短连接下，TIME_WAIT 就会太多，这也会消耗很多系统资源。

当发现系统存在大量 TIME_WAIT 状态的连接，通过调整内核参数解决：  `vim /etc/sysctl.conf` 加入以下内容

```
net.ipv4.tcp_syncookies = 1 
net.ipv4.tcp_tw_reuse = 1
net.ipv4.tcp_tw_recycle = 1
net.ipv4.tcp_fin_timeout = 30
```

然后执行 /sbin/sysctl -p 让参数生效。

注释：

`net.ipv4.tcp_syncookies = 1` 表示开启 SYN Cookies。当出现 SYN 等待队列溢出时，启用 cookies 来处理，可防范少量 SYN 攻击，默认为 0，表示关闭。

`net.ipv4.tcp_tw_reuse = 1` 表示开启重用。允许将 TIME-WAIT sockets 重新用于新的TCP连接，默认为 0，表示关闭。

`net.ipv4.tcp_tw_recycle = 1` 表示开启TCP连接中 TIME-WAIT sockets 的快速回收，默认为 0，表示关闭。

`net.ipv4.tcp_fin_timeout` 表示修改系統默认的 TIMEOUT 时间



