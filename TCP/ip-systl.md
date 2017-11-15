## Linux 下 TCP/IP 核心参数

在 Linux 下查看 TCP/IP 参数：

* `man tcp` 或 `man udp`
* `cd /proc/sys/net/ipv4` 
* 如果修改或新增参数：`vim /etc/sysctl.conf`，然后让内核参数生效：`/sbin/sysctl -p`

查看当前 TCP/IP 连接的状态和对应的个数：`netstat -n | awk '/^tcp/ {++S[$NF]} END {for(a in S) print a, S[a]}'`

> **net.ipv4.tcp_syncookies**

net.ipv4.tcp_syncookies = 1，表示开启 SYN Cookies。当出现 SYN 等待队列溢出时，启用 cookies 来处理，可防范少量 SYN 攻击，默认为 0，表示关闭。

> **net.ipv4.tcp_tw_reuse**

net.ipv4.tcp_tw_reuse = 1，表示开启重用。允许将 TIME-WAIT 态的 socket 重新用于新的 TCP 连接，默认为 0，表示关闭。

> **net.ipv4.tcp_tw_recycle**

net.ipv4.tcp_tw_recycle = 1，表示打开快速 TIME-WAIT sockets 回收，默认为 0，表示关闭。

> **net.ipv4.tcp_fin_timeout**

修改系統默认的 TIMEOUT 时间，默认为 60 秒。

> **net.ipv4.tcp_keepalive_time**

当 keepalive 打开的情况下，TCP 发送 keepalive 消息的频率，即每隔多长时间发送一次。

默认为 7200 秒(2小时)。

> **net.ipv4.tcp_max_syn_backlog**

表示 SYN 队列最大长度(半连接队列长度)，默认为 1024。

> **net.ipv4.tcp_max_tw_buckets**

表示系统同时保持 TIME_WAIT 的最大数量，如果超过这个数字，TIME_WAIT将立刻被清除并打印警告信息。

为了抵御那些简单的 DoS 攻击。

> **net.ipv4.ip_local_port_range**

表示用于向外连接的端口范围。

> **net.ipv4.tcp_syn_retries**

对于一个新建连接，内核要发送多少个 SYN 连接请求才决定放弃。

> **net.ipv4.tcp_synack_retries**

对于远端的连接请求 SYN，内核会发送 SYN ＋ ACK 数据报，以确认收到上一个 SYN 连接请求包。

> **net.ipv4.tcp_abort_on_overflow**

当守护进程太忙而不能接受新的连接，就向对方发送 reset 消息，默认值是 false。

## 典型应用

### 如何 预防 SYN flood 攻击

linux内核参数调优主要有下面三个：

* 增大 tcp_max_syn_backlog
* 减小 tcp_synack_retries
* 开启 tcp_syncookies

### 解决大量 TIME_WAIT 消息

linux内核参数调优主要有下面四个：

* 开启 tcp_syncookies
* 开启 tcp_tw_reuse
* 开启 tcp_tw_recycle 
* 修改 tcp_fin_timeout

## 参考

* [官方文档](https://www.kernel.org/doc/Documentation/networking/ip-sysctl.txt)
* [TCP SYN flood 洪水攻击](http://blog.csdn.net/hengyunabc/article/details/24934529)
