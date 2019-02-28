# 微信小程序的after设置宽高，只是设置了一半，为什么？并且显示不出来
 答：微信小程序的button边框是使用after实现的，存在默认样式，所以要重置样式，transform: scale(1), border: none;
 显示不出来是因为我自己不知何时将after设置为none！！！
---

# 父级元素高度没有浮动元素高时，浮动元素如何展示？
答：正常显示，元素会溢出父级元素。
---

# 苹果部分型号，navigationStyle: custom，隐藏不掉导航样式， 为什么？
  待解决
---

# mpvue如何全局引入sass配置文件，避免每个页面都得引入，增加开发难度和维护难度？
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
---

# 现有的mpvue架构是否合理，边界是否恰当？如不合理？不合理的地方和如何优化？

---


# 在mpvue使用vnode2canvas时，store修改后不能同步更新视图层，为什么？
    [官方参考文档](https://github.com/muwoo/vnode2canvas/blob/master/examples/mpvue/README.md)
    分析：
      1. 新建一个mpvue项目，同时使用vuex和store是否还出现类似问题
      答： 还是出现这个问题，渲染
---

# 每一个请求没有登录都会跳入登录页，如果请求很多就会跳入多次，如何阻止？
---

# 每个页面都要导航栏，mpvue在minxin中导入，不能渲染出来
---
