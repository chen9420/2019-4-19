#ajax对象的常用属性和事件

> onerror  请求失败  比如断网 *
```
xhr.onerror = function () {
    console.log('失败');//一般是传输的时候有问题
}
```
> onload  请求成功 *
```
xhr.onload = function () {
    console.dir(xhr);
    console.log(xhr.responseText);
}
```
> onprogress 进度
```
xhr.onprogress = function(ev){
    console.log(ev);
}
```

> upload 上传相关 *

> onreadystatechange 监听状态的变化  所有浏览器都兼容 *
注意：事件绑定在send之前，能够监听建立连接，也就是在异步的情况下，能够多监听一步

> readyState *  状态进行到了哪一步0-4 一共有5步，只是状态值为4的时候说明请求完成，0是监听不到的


```
0: 请求未初始化
1: 服务器连接已建立
2: 请求已接收
3: 请求处理中
4: 请求已完成，且响应已就绪
```

> responseText   后端返回的数据
> responseXML    XML的document对象
> status        HTTP状态码 

```
比如:200,404
1-6开头状态码
1 消息
2 成功  200-207为成功
3 重定向  
    301 永久重定向

    302 请求的资源临时从不同的 URI响应请求。由于这样的重定向是临时的，客户端应当继续向原有地址发送以后的请求。只有在Cache-Control或Expires中进行了指定的情况下，这个响应才是可缓存的

    304 如果客户端发送了一个带条件的 GET 请求且该请求已被允许，而文档的内容（自上次访问以来或者根据请求的条件）并没有改变，则服务器应当返回这个状态码。304响应禁止包含消息体，因此始终以消息头后的第一个空行结尾。

    305 需要代理

    307 请求的资源临时从不同的URI 响应请求


4 请求错误
    前端的锅
    400 Bad Request
        1、语义有误，当前请求无法被服务器理解。除非进行修改，否则客户端不应该重复提交这个请求。
        2、请求参数有误。
    401 Unauthorized
        当前请求需要用户验证。

    403 Forbidden
        服务器已经理解请求，但是拒绝执行它
    404 请求失败


5、6 服务器错误
    只要出现5后端的问题


```

> timeout     超时  设置时间毫秒 比如: xhr.timeout = 3000
> ontimeout 超时回调
```
xhr.timeout = 3000;
xhr.ontimeout = function(){
    console.log('超时');
    img.style.display = 'none';
}
```



