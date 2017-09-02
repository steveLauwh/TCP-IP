## HTTP 报文首部

HTTP 报文首部字段是构成 HTTP 报文的要素之一。使用首部字段是为了给浏览器和服务器提供报文主体大小、所使用的语言、认证信息等内容。

HTTP 首部字段有 4 种类型：通用首部字段、请求首部字段、响应首部字段、实体首部字段。

### 通用首部字段

请求报文和响应报文都会使用的首部。

> `Cache-Control`

首部字段 Cache-Control 能够控制缓存的行为。

如 `Cache-Control: max-age=0` 表示缓存服务器通常需要将请求转发给源服务器。

> `Connection`

* 控制不再转发给代理的首部字段
* 管理持久连接

如 `Connection: Keep-Alive` 持续连接。

> `Date`

首部字段 Date 表明创建 HTTP 报文的日期和时间。

> `Pragma`

`Prama: no-cache` 客户端要求所有的中间服务器不返回缓存的资源。

> `Trailer`

首部字段 `Trailer` 会事先说明在报文主体后记录哪些首部字段。

> `Transfer-Encoding`

首部字段 `Transfer-Encoding` 规定了传输报文主体时采用的编码方式。

`Transfer-Encoding: chunked` 分块传输编码。

> `Upgrade`

首部字段 `Upgrade` 用于检测 HTTP 协议及其它协议是否可使用更高的版本进行通信。

> `Via`

首部字段 `Via` 是为了追踪客户端与服务器之间的请求和响应报文的传输路径。

> `Warning`

通知用户一些与缓存相关的问题的警告。
