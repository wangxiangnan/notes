## 开发遇到的问题

#### about js

      1. 一次请求，有可能登录失败，登录成功再次调用，原来的函数不能接收数据
      解决方法： 
        (1) 使用Promise