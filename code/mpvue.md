### mpVue小程序优化

    1. 视图层：
      (1) 优化结构标签,避免使用没必要的标签
      (2) 长列表页避免使用绝对定位
      (3) 使用tinypng对图片做无损压缩



    2. 逻辑层
      (1) 精简data数据(1. 视图层不使用的数据可以绑定到Vue上。 2. 对于接口返回的数据，页面大量没有用到可以进行精简)
      (2) 开发时打开Vue.config._mpTrace = true;
      (3) Vuex保持数据精简，必要时可先存放在storage