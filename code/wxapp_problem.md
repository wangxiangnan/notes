##微信小程序遇到的问题


#### 小程序本身的问题
    1. 列表搜索时，当列表上滑加载出现改动条时，使用关键字等搜索时，由于滚动条位置不变，就会出现加载很多页的情况
        解决方法： 使用wx.pageScrollTo({scrollTop: 0, duration: 0});

    2. 预览图片会触发onShow周期函数
        解决方法：使用全局变量或属性，在预览是设置isPreview = ture, onshow(){ if (isPreview) return isPreview = false }

    3. wx.onAppShow(callback), 这是一个监听函数，绑定后就会自动触发

    4. App.onShow()的参数，有保存时间，预览图片和从后台切换到前台，参数不变

#### 小程序框架Mpvue的问题


#### 其他问题

    1. 是否需要一个全局的变量isUseStorage的变量，来指定是否使用缓存？
      (1) 需要： 


      (2) 不需要




