#### 微信小程序的after设置宽高，只是设置了一半，为什么？并且显示不出来

    答：微信小程序的button边框是使用after实现的，存在默认样式，所以要重置样式，transform: scale(1), border: none;
    显示不出来是因为我自己不知何时将after设置为none！！！

#### 父级元素高度没有浮动元素高时，浮动元素如何展示？

    答：正常显示，元素会溢出父级元素。


#### 苹果部分型号，navigationStyle: custom，隐藏不掉导航样式， 为什么？

    待解决


#### mpvue如何全局引入sass配置文件，避免每个页面都得引入，增加开发难度和维护难度？

    答：
      1. 安装依赖： npm install sass-loader node-sass --save-dev 
      以下都是修改build/utils.js文件。
      2. 添加
      var sassResourceLoader = {
        loader: 'sass-resources-loader',
        options: {
          resources: [
            path.resolve(__dirname, '../src/styles/base.scss'),
          ]
        }
      }
      3. generateLoaders函数添加形参anotherLoader
      4. 添加if (!!anotherLoader) loaders.push(anotherLoader)
      5. 把自定义的loader加上去
        sass: generateLoaders('sass', { indentedSyntax: true },sassResourceLoader),
        scss: generateLoaders('sass',{},sassResourceLoader),

    附： https://blog.csdn.net/mate_ge/article/details/81179521


#### 现有的mpvue架构是否合理，边界是否恰当？如不合理？不合理的地方和如何优化？




#### 在mpvue使用vnode2canvas时，store修改后不能同步更新视图层，为什么？

    [官方参考文档](https://github.com/muwoo/vnode2canvas/blob/master/examples/mpvue/README.md)  
    分析： 
      1. 新建一个mpvue项目，同时使用vuex和store是否还出现类似问题  
      答： 还是出现这个问题
      具体问题是： store的action和mutation都可以触发，state也可以改变，但是多个页面有可能不能及时更新视图


#### 每一个请求没有登录都会跳入登录页，如果请求很多就会跳入多次，如何阻止？

    1. 首先所有发起的action都是从minxin公共方法中发起以及跳入登录页，和状态显示 
    2. 设置全局变量isLogging 
    3. 当isLogging是false时将其设为true，并跳入登录页。 
    4. 跳出登录页将其设为false

#### 每个页面都要导航栏，mpvue在minxin中导入，不能渲染出来



#### 深入理解js是单线程的，也就是两个事件不可能同时触发，必定是一个一个执行

    !isLogging? that.$router.push("/pages/login/main"): console.log('已阻止重复跳入登录页!');
    !isLogging && (isLogging = true); // 未正在登录才会改为正在登录
    这个实现才成为可能

#### LF和CRLF的区别

  CRLF： "\r\n", windows系统的换行的方式。
  LF："\n", linux系统的换行的方式

  在你使用git拉取代码的时候，git会自动将代码当中与你当前系统不同的换行方式转化成你当前系统的换行方式，从而造成这种冲突。 
  1. 修改git全局配置，禁止git自动将lf转换成crlf,  命令： 
  git config --global core.autocrlf false

  2. 修改编辑器的用户配置，例如vscode 
  "files.eol": "\n", // 文件换行使用lf方式 

#### 添加worker代码文件， 微信多线程实例：canvas
  初始化：
    1. 创建worker线程
    2.初始化


#### 研究一下方法
  ``` javascript
    function fib(n) {
      if (n < 1) return 0
      if (n <= 2) return 1
      return fib(n - 1) + fib(n - 2)
    }
  ```

#### vue-cli 放在服务器子文件夹下

  vue项目放置服务器子文件夹，改三处，config/index, build/utils, vueRouter

#### vue mode = history && hash的优缺点

  history: 路径和正常一样，看着好看，但是后台服务器必须支持，如返回404时，返回设定的index文件

  hash： 不好看， 但只需服务器支持一次，刷新无影响

#### JS小数运算不对

  例如： 5 - 3.2 = 1.7999999999999998
        1.6 * 3 = 4.800000000000001
  产生原因： java和javascript中计算小数运算时，都会将十进制的小数换算为对应的二进制，一部分小数并不能完整的换算为二进制，这里就出现了第一次误差。
  解决方法： js之间的整数运算都是正常的，所以先换算为整数，之后再换算为小数

#### 乘性操作符的不同之处

  1. NaN和任意数据运算都会返回NaN。
  2. Infinity * 0 = NaN.
  3. Infinity / Infinity = NaN.
  4. 0 / 0 = NaN.
  5. anyNumber / Infinity = 0.
  6. anyNumber / 0 = Infinity.

  主要注意，0为除数时的情况。

#### 阿姨简历构思

  问题：

    1. 把一个整数据拆分为每个页面
    2. 每个页面的完成可以校验，最后一个页面可以提交
    3. 获取技能等列表标签，并且可以识别哪些是选中的
    4. 使用一个完成按钮， 如何区分什么时候该跳到下一个tab，什么时候该提交数据
    5. 上面的tab页什么时候可以切换，什么时候不可以？

  解决方法：
  
    1. 所有数据都挂载在store上
    2. 使用store的getter，把整个数据拆分成单个tab页面
    3. store创建required必需对象，字段必填为true
    4. 使用页面的computed把数组选中的选项使用isChecked进行区分
    5. 页面有一个当前tab页的索引，可以判断下一步的动作


#### js小技巧

  1. 使用~~代替parseInt(只针对字符串都是数字的情况)
  2. while(i--){}
  3. eventBus是组件间进行解耦通信的工具
  4. 从模块机制，理解映射的含义(mapping: one to one)
  5. 数据分为服务器数据和本地数据，两者结合才能发挥最佳的体验。


#### js语句(一个语句代表一段完整的执行情况，一条一条的去执行)

  1. 语句以分号结束
  2. 以花括号来包含多条语句
  3. 独立的语句有if else; for; for in; while; do while; with;

#### js执行环境和事件循环机制

  1. 首先javascript在浏览器是单线程的，也就是在同一时间只能做一件事
  2. 对于其他的事件，把他们排队在执行栈中
  3. 当浏览器第一次加载你的script时，它默认进入了全局执行环境
  4. 如果你在全局环境调用了一个函数，会创建一个新的执行环境，并添加在执行栈的顶部
  5. 执行栈是同步执行的，而事件循环队列是异步回调的

#### js垃圾回收

  1. 垃圾回收分为标记清除和引用计数
  2. 对于函数内的局部变量，函数执行完毕会自动回收该值所占的内存，而对于全局变量，再不使用时，应该手动
  清除，以便下次垃圾收集器将其回收

#### js表达式和语句

  1. 表达式就是使用操作符
  2. 语句就是一句话的表达
  3. 语句使用;号结束
  4. 也可以使用{}包含多条语句

#### js对象生命周期函数理解

  1. 自定义canvas对象，完成渲染，输出图片临时路径


#### 使用google查找内存泄露，内存膨胀， 频繁的垃圾回收机制

  [跳转到谷歌开发者文档](https://developers.google.com/web/tools/chrome-devtools/memory-problems/?hl=zh-cn)