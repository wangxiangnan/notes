```
1. HTTP协议是TCP/IP协议族的子集，那么问题是TCP/IP是系统提供，还是客户端（浏览器）提供的？
  答： 我认为只要脱离浏览器，以命令行的方式如果能发送和接收HTTP，就认为是系统提供的，百度一下后，windows可以使用telnet命令（默认没有开启，在windows服务开启）
  步骤如下： 
    1. 打开cmd
    2. 输入telnet 127.0.0.1 8000 // 输入你自己的ip和端口
    3. 输入ctrl+}
    4. 回车
    5. 输入 GET / HTTP/1.1 回车 POST: 127.0.0.1 两下回车
    6. 看到响应的报文如下格式：

    HTTP/1.1 200 OK
    Date: Tue, 13 Aug 2019 01:09:22 GMT
    Server: WSGIServer/0.2 CPython/3.7.4
    Content-Type: text/html
    X-Frame-Options: SAMEORIGIN
    Content-Length: 16348

    <!doctype html>
               <html>
                         <head>
                                       <meta charset="utf-8">
                                                                     <title>Django: the Web framework for perfectionists with deadlines.</title>
                                <meta name="viewport" content="width=device-width, initial-scale=1">
                                                                                                            <link rel="stylesheet" type="text/css" href="/static/admin/css/fonts.css">
                                                                      <style type="text/css">
                                                                                                       body, main {
                                                                                                                               margin: 0 auto;
                                }
    结论：
    1. TCP/IP协议族是由系统原生提供的，当然包括HTTP协议了。
    2. 请求或响应报文格式：返回字符串且报文头和报文主主体以换行符（CRLF：图解HTTP介绍的）分开
```
