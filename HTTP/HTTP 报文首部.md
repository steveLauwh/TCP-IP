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

### 请求首部字段

请求首部字段是从客户端往服务器端发送请求报文中所使用的字段，用于补充请求的附加信息、 客户端信息、 对响应内容相关的优先级等内容。

> `Accept`

`Accept` 首部字段可通知服务器， 用户代理能够处理的媒体类型及媒体类型的相对优先级。 

> `Accept-Charset`

`Accept-Charset` 首部字段可用来通知服务器用户代理支持的字符集及字符集的相对优先顺序。

> `Accept-Encoding`

`Accept-Encoding` 首部字段用来告知服务器用户代理支持的内容编码及内容编码的优先级顺序。 

> `Accept-Language`

首部字段 `Accept-Language` 用来告知服务器用户代理能够处理的自然语言集（指中文或英文等）， 以及自然语言集的相对优先级。

> `Authorization`

首部字段 `Authorization` 是用来告知服务器， 用户代理的认证信息（证书值）。 

> `Expect`

客户端使用首部字段 `Expect` 来告知服务器， 期望出现的某种特定行为。 

> `From`

首部字段 `From` 用来告知服务器使用用户代理的用户的电子邮件地址。 

> `Host`

虚拟主机运行在同一个 IP 上， 因此使用首部字段 Host 加以区分。首部字段 Host 会告知服务器， 请求的资源所处的互联网主机名和端口号。

> `If-Match`

只有当 If-Match 的字段值跟 ETag 值匹配一致时， 服务器才会接受请求。

> `If-Modified-Since`

如果在 If-Modified-Since 字段指定的日期时间后， 资源发生了更新， 服务器会接受请求。

> `If-None-Match`

只有在 If-None-Match 的字段值与 ETag 值不一致时， 可处理该请求。 

> `If-Range`


