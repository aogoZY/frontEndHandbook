# frontEndHandbook
整理的关于前端的一些知识，不定期更新。

### 关于缓存
#### 为什么要缓存？
- 减少带宽消耗
- 降低服务器压力（用户和爬虫角度）
- 提升用户体验
- https://www.cnblogs.com/btgyoyo/p/6125159.html
#### 有哪些缓存？
- 数据库缓存
- CDN 缓存
- 代理服务器缓存
- 浏览器缓存
- 应用层缓存

#### 怎么做？
#### CDN 和代理服务器的区别是什么？
- CDN 加速静态资源，反向代理做动态资源的负载均衡
- 什么是CDN？如果我在广州访问杭州的淘宝网，跨省的通信必然造成延迟。如果淘宝网能在广东建立一个服务器，静态资源我可以直接从就近的广东服务器获取，必然能提高整个网站的打开速度，这就是CDN。CDN叫内容分发网络，是依靠部署在各地的边缘服务器，使用户就近获取所需内容，降低网络拥塞，提高用户访问响应速度。
- 反向代理，代理服务器，降低用户对系统的理解复杂度。
#### 缓存和304 的关系 
304 表示未修改，意思就是自从上次缓存过后页面未被修改过。那么这个未修改是如何定义的，可以通过以下两种方式：Last-modified & ETag

- Last-modified 的意思就是说每次服务器有修改的时候会告诉客户端修改时间是多少，客户端下次请求的时候会携带这个数据让服务器检查从这个时间以后是否有发生过修改，如果没有则返回304，如果有修改则返回200 以及请求的内容。
- ETag 是请求内容的一个hash 值，服务器返回给客户端请求内容的同时会返回一个ETag，客户端下次请求同样的内容时会携带ETag，服务器端通过对比这个ETag 和目前做的ETag 来判断资源是否被修改。如未被修改则返回304，否则返回200.
- ETag 相对于Last-modified 的优势
![youshi](leanote://file/getImage?fileId=5b093207cf1ac45c75000010)
- http://web.jobbole.com/85243/
#### CDN 和DNS 的关系
网页打开的时候先去找DNS 拿到最近的CDN 服务器地址，然后去请求CDN 服务器，CDN 服务器去请求真正的服务器拿数据并缓存。
#### 强缓存和协商缓存
- 强缓存：直接读缓存
- 协商缓存：先确定缓存是否有效（304）
- https://www.cnblogs.com/wonyun/p/5524617.html 
