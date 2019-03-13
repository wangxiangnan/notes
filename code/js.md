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
    function fib(n) {
      if (n < 1) return 0
      if (n <= 2) return 1
      return fib(n - 1) + fib(n - 2)
    }

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


