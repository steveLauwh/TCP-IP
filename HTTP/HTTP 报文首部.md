## HTTP 报文首部

HTTP 报文首部字段是构成 HTTP 报文的要素之一。使用首部字段是为了给浏览器和服务器提供报文主体大小、所使用的语言、认证信息等内容。

HTTP 首部字段有 4 种类型：通用首部字段、请求首部字段、响应首部字段、实体首部字段。

### 通用首部字段

请求报文和响应报文都会使用的首部。

> `Cache-Control`

首部字段 Cache-Control 能够控制缓存的行为。

如 Cache-Control: max-age=0 表示缓存服务器通常需要将请求转发给源服务器。

> `Connection`

* 控制不再转发给代理的首部字段
* 管理持久连接

如 Connection: Keep-Alive 持续连接。

> `Date`

首部字段 Date 表明创建 HTTP 报文的日期和时间。

> `Pragma`

Prama: no-cache 客户端要求所有的中间服务器不返回缓存的资源。

> `Trailer`

首部字段 Trailer 会事先说明在报文主体后记录哪些首部字段。

> `Transfer-Encoding`

首部字段 Transfer-Encoding 规定了传输报文主体时采用的编码方式。

Transfer-Encoding: chunked 分块传输编码。

> `Upgrade`

首部字段 Upgrade 用于检测 HTTP 协议及其它协议是否可使用更高的版本进行通信。

> `Via`

首部字段 Via 是为了追踪客户端与服务器之间的请求和响应报文的传输路径。

> `Warning`

通知用户一些与缓存相关的问题的警告。

### 请求首部字段

请求首部字段是从客户端往服务器端发送请求报文中所使用的字段，用于补充请求的附加信息、 客户端信息、 对响应内容相关的优先级等内容。

> `Accept`

Accept 首部字段可通知服务器， 用户代理能够处理的媒体类型及媒体类型的相对优先级。 

> `Accept-Charset`

Accept-Charset 首部字段可用来通知服务器用户代理支持的字符集及字符集的相对优先顺序。

> `Accept-Encoding`

Accept-Encoding 首部字段用来告知服务器用户代理支持的内容编码及内容编码的优先级顺序。 

> `Accept-Language`

首部字段 Accept-Language 用来告知服务器用户代理能够处理的自然语言集（指中文或英文等），以及自然语言集的相对优先级。

> `Authorization`

首部字段 Authorization 是用来告知服务器，用户代理的认证信息（证书值）。 

> `Expect`

客户端使用首部字段 Expect 来告知服务器， 期望出现的某种特定行为。 

> `From`

首部字段 From 用来告知服务器使用用户代理的用户的电子邮件地址。 

> `Host`

虚拟主机运行在同一个 IP 上， 因此使用首部字段 Host 加以区分。首部字段 Host 会告知服务器，请求的资源所处的互联网主机名和端口号。

> `If-Match`

只有当 If-Match 的字段值跟 ETag 值匹配一致时，服务器才会接受请求。

> `If-Modified-Since`

如果在 If-Modified-Since 字段指定的日期时间后，资源发生了更新，服务器会接受请求。

> `If-None-Match`

只有在 If-None-Match 的字段值与 ETag 值不一致时，可处理该请求。 

> `If-Range`

告知服务器若指定的 IfRange 字段值（ETag 值或者时间）和请求资源的 ETag 值或时间相一致时，则作为范围请求处理。

> `If-Unmodified-Since`

告知服务器， 指定的请求资源只有在字段值内指定的日期时间之后，未发生更新的情况下，才能处理请求。

> `Max-Forwards`

每次转发数值减 1。 当数值变 0 时返回响应。

> `Proxy-Authorization`

接收到从代理服务器发来的认证质询时，客户端会发送包含首部字段 Proxy-Authorization 的请求，以告知服务器认证所需要的信息。

> `Range`

对于只需获取部分资源的范围请求，包含首部字段 Range 即可告知服务器资源的指定范围。

> `Referer`

首部字段 Referer 会告知服务器请求的原始资源的 URI。

> `TE`

首部字段 TE 会告知服务器客户端能够处理响应的传输编码方式及相对优先级。

> `User-Agent`

首部字段 User-Agent 会将创建请求的浏览器和用户代理名称等信息传达给服务器。

### 响应首部字段

响应首部字段是由服务器端向客户端返回响应报文中所使用的字段，用于补充响应的附加信息、 服务器信息， 以及对客户端的附加要求等信息。

`Accept-Ranges`

首部字段 Accept-Ranges 是用来告知客户端，服务器是否能处理范围请求，以指定获取服务器端某个部分的资源。

`Age`

首部字段 Age 能告知客户端， 源服务器在多久前创建了响应。 字段值的单位为秒。

`ETag`

首部字段 ETag 能告知客户端实体标识。 它是一种可将资源以字符串形式做唯一性标识的方式。 服务器会为每份资源分配对应的 ETag 值。

`Location`

使用首部字段 Location 可以将响应接收方引导至某个与请求 URI 位置不同的资源。

`Proxy-Authenticate`

首部字段 Proxy-Authenticate 会把由代理服务器所要求的认证信息发送给客户端。

`Retry-After`

首部字段 Retry-After 告知客户端应该在多久之后再次发送请求。 

`Server`

首部字段 Server 告知客户端当前服务器上安装的 HTTP 服务器应用程序的信息。 

`Vary`

当代理服务器接收到带有 Vary 首部字段指定获取资源的请求时，如果使用的 Accept-Language 字段的值相同，那么就直接从缓存返回响应。 

`WWW-Authenticate`

首部字段 WWW-Authenticate 用于 HTTP 访问认证。

### 实体首部字段

实体首部字段是包含在请求报文和响应报文中的实体部分所使用的首部，用于补充内容的更新时间等与实体相关的信息。

`Allow`

首部字段 Allow 用于通知客户端能够支持 Request-URI 指定资源的所有 HTTP 方法。 

`Content-Encoding`

首部字段 Content-Encoding 会告知客户端，服务器对实体的主体部分选用的内容编码方式。

`Content-Language`

首部字段 Content-Language 会告知客户端，实体主体使用的自然语言（指中文或英文等语言）。

`Content-Length`

首部字段 Content-Length 表明了实体主体部分的大小（单位是字节）。 

`Content-Location`

首部字段 Content-Location 给出与报文主体部分相对应的 URI。和首部字段 Location 不同，Content-Location 表示的是报文主体返回资源对应的 URI。

`Content-MD5`

客户端会对接收的报文主体执行相同的 MD5 算法，然后与首部字段 Content-MD5 的字段值比较。

`Content-Range`

针对范围请求，返回响应时使用的首部字段 Content-Range，能告知客户端作为响应返回的实体的哪个部分符合范围请求。字段值以字节为单位，表示当前发送部分及整个实体大小。

`Content-Type`

首部字段 Content-Type 说明了实体主体内对象的媒体类型。

`Expires`

首部字段 Expires 会将资源失效的日期告知客户端。

`Last-Modified`

首部字段 Last-Modified 指明资源最终修改的时间。

###
