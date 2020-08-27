这是一我第一个 vue项目 感受代码的魅力吧 我们是一个有灵魂的程序员 我们的代码充满诗意
让我来看看我的 git 有没有发生改变
实行步骤
## 改造 tabbar 为 router-link
## 设置 tabbar 点击的时候样式发生改变 高亮
## 点击 tabbar 中的路由 展示对应的组件
## 制作首页轮播图 通过 mintui 来做 导入需要的组件 然后设置 swiper的高度
<!-- 轮播图数据的获取 -->
## 加载首页轮播图的数据
## vue-resource 获取数据
## 获取到的数据 存在组件 data 中的 list 里面
## v-for 循环遍历小数组 在组件中循环要绑定 key 循环渲染
## 设置 img 标签 将得到的 response.body.message 绑定在 img 的 src中
<!-- 加上 toast 组件 提示 有没有获取数据成功 -->

## news 页面的添加
## 点击首页的小图标会自动跳转, 在当前home 页面中的 a 标签改为 routerlink 然后 配置路由
1. 构造页面   -- 使用 mui 中的 media list 来绘制页面
2. 通过 vue -resource 将data 渲染出来

## 定义全局的过滤器 过滤时间
## 实现列表点击 跳转到详情 -- 将列表的每一项都改为 router-link 并在跳转的时候提供唯一的标识符
## 创建组件页面 newsInfo.vue  -> 配置路由

## 单独封装一个 comment 子组件 
1. 先创建一个单独的 comment 组件模板
2. 在需要使用comment组件的地方导入 (手动dao)

## 获取所有的评论数据 渲染

## 发表评论
1. 文本框作为双向绑定 绑定事件
2. 校验 评论不能为空 trim 消除两边的空格 空则提示 评论内容不能为


## 绘制图片列表 组件页面结构并美化样式
1. 顶部的滑动条 swiper
2. make bottom photo list

## 制作顶部滑动条的坑
1. 需要借助于 mui中的界面 tab-top-webview-main.html
2. 需要将 slider中的 fullscreen class 去掉
3. 滑动条无法正常的被滑动 需要导入 mui 中的 js 文件 -> 检查官方文档发现需要初始化
    -. 导入 mui.js
    -. 调用官方提供的方式去初始化
    mui('.mui-scroll-wrapper').scroll({
	deceleration: 0.0005 //flick 减速系数，系数越大，滚动速度越慢，滚动距离越小，默认值0.0006

 ## (妈的 找了好久的问题) 我们在初始化 滑动条的时候导入了 mui.js 但是后来报错  Uncaught TypeError: 'caller', 'callee', and 'arguments' properties may not be accessed on strict mode functions or the arguments objects for calls to them
  经过我们的推测 可能是导包的时候用到了 caller callee 或者 arguments 这三个变量  webpack打包好的 bundle.js 中默认启用的是严格模式 这三个变量名称不能出现在严格模式中 产生冲突
 ## 解决方案:  
    1.把 mui js 中的非严格模式代码改掉 (不现实)
    2. 将打包时候的严格模式禁用 -> npm 下载插件 然后再 babel 中配置
    3. 不能滑动需要在样式中 
    *{
    touch-action: pan-y;
}
## 刚进入滑动条的时候 无法正常滑动 我们将 mui touch bar 的加载放到了 mounted 中 等页面元素加载完毕之后我们在启用这个滑动条


## 滑动条可以了 但是 tabbar 不能工作了 我们要将每个 tabbar的样式改名字


## 获取所有分类并且渲染分类列表
## 图片列表需要使用懒加载技术  我们使用 mint-ui 中的 lazy load , 根据 lazy load 渲染图片列表

## 实现点击图片跳转到图片详情, 将 a 标签替换为 router-link 中要注意 要给 router-link 添加属性 tag 将 routerlink 渲染为哪种元素 否则之后返回样式会发生改变 

## 实现详情页面的布局 然后渲染页面

