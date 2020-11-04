### 缓存的作用

缓解服务器端的压力，提升性能，对一个资源的缓存应截止到其下一次发生改变（不能缓存过期的资源）

### 缓存的种类

两大类：私有和共享缓存

![](E:\learn\blog\Blog\images\http-cache.png)

浏览器缓存（HTTP缓存）--私有

代理缓存--共享

网关缓存，CDN，反向代理缓存，负载均衡--部署在服务器上的缓存方式

### 缓存操作的目标

常见的HTTP缓存只能存储GET响应，缓存的关键包括request method和URL

普遍的缓存案例：

1. GET请求，响应状态码200
2. 永久重定向301
3. 错误响应 404
4. 不完全响应，响应状态码206，只返回局部的信息
5. 除GET请求外，如果匹配到作为一个已被定义的cache key的响应

### 缓存控制

Cache-control头

> HTTP/1.1定义的Cache-Control头，通用头部，根据该都不提供的值来定义缓存策略

##### 没有缓存

~~~
Cache-Control: no-store
~~~

##### 缓存但重新验证

~~~
Cache-Control: no-cache
~~~

##### 私有缓存和公共缓存

~~~~
Cache-Control: private
Cache-Control: public
~~~~

##### 过期

~~~
Cache-Control: max-age=31536000
~~~

##### 验证方式

~~~
Cache-Control: must-revalidate
~~~



根据特定header，计算缓存寿命优先级Cache-Control: max-age=N > Expires: Date > Last-Modified ((Date - Last-Modified)/10 )



缓存校验：（强校验）ETag --->> If-None-Match 是个hash值

​					（弱校验）Last-Modified --->> If-Modified-Since 

### Vary 响应

Vary 响应头决定了对于后续的请求头，如何判断是请求一个新的资源还是使用缓存的文件，当缓存服务器收到一个请求时，只有当前请求和原始（缓存）的请求跟缓存的响应头里的Vary都匹配，才能使用缓存的响应



使用vary都有利于内容服务的动态多样性，例如，Vary：User-Agent，缓存服务器需要通过UA判断是否使用缓存的页面，在需要区分移动端和桌面端的展示内容时，利用这种方式就能避免在不同的终端展示错误的布局





