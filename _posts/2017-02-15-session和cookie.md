#### cookie

- 浏览器端

  - 大小一般来说允许4kb 不同版本略有不同

  - 当cookie的数量达到上限时的删除方式

    将最近使用最少的cookie删除

    随机删除

  - 数量 各个浏览器会有不同 同一浏览器不同版本也不同

    IE8允许每个域存50个cookie

    firefox允许每个域存50个cookie

- setcookie(string name [,string value [,int expire [,string path [,string domain [,bool,secure]]]]])

  - secure指明cookie是否仅通过安全的HTTPS连接传送 默认值为false
  - path cookie在服务器端的有效路径

#### session

- 服务器端

  - cookie被禁只能通过get
  - 理论上没有大小和数量限制
  - 通常用来保存浏览记录 购物车 登陆信息
  - cookie只有在设置的过期时间之后或者清除cookie失效 session只要关闭浏览器或者清除cookie就失效 session安全性更高

- 开启session

  - session_start() 

    开始一个会话或者返回已经存在的会话 判断客户端有无session_id 如果没有，在服务器端写入SESSION文件（或者通过数据库等完成）发送写session_id的cookie头信息。如果有客户端发来的session_id则找相应session数据

    session_unset()

    释放当前在内存中已经创建的所有$_SESSION变量 但不删除对应的session文件 以及 不释放对应的session id

    session_destroy()

    都删除

  - 什么是垃圾

    没有任何变量指向这个对象是 即为垃圾 PHP会自动从内存中将其销毁 防止内存溢出 当一个PHP线程结束时 当前所有占用的内存都会被销毁

  - 引用计数器

    每个对象都包含一个引用计数器，每个引用连接对象时，计数器+1。当引用离开生存空间或设为NULL时，计数器减1。当某个对象计数器为0时，启动垃圾回收器，释放其所占用的空间