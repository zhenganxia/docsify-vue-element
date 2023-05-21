## 导航栏
> 根路径添加_navbar.md 文件
```js
// index.html
window.$docsify = {
    loadNavbar: true, // 导航栏
}
```

<image src="/assets/img/nav.png">

## 侧边栏
> - 根路径 添加_sidebar.md文件- 默认/根加载侧边栏
> - 如果修改默认侧边栏页面 设置 loadSidebar:'自定义.md' 自定义.md 不以_开头
```js
window.$docsify = {
    // index.html
    loadSidebar: true, // 展示侧边栏
    subMaxLevel: 2, // 侧边栏默认展开层级
}
```

## 导航栏和侧边栏联动
```js
// index.html
window.$docsify = {
    loadSidebar: true, // 侧边栏
    subMaxLevel: 2, // 侧边栏默认展开层级
}
```
<image src="/assets/img/nav.png">
<image src="/assets/img/side.png">

## vue+element插件实现功能
```js
 // index.html
 <!-- vue -->
  <script src="//cdn.jsdelivr.net/npm/vue/dist/vue.min.js"></script>
  <!-- 引入样式 -->
  <link rel="stylesheet" href="//unpkg.com/element-ui/lib/theme-chalk/index.css">
  <!-- 引入组件库 -->
  <script src="//unpkg.com/element-ui/lib/index.js"></script>
```
```js
// 使用
<div id="select">
    <el-select v-model="value" class="m-2" placeholder="请选择" size="large">
    <el-option
      v-for="item in options"
      :key="item.id"
      :label="item.name"
      :value="item.id"
    />
  </el-select>
</div>
<script type="text/javascript">
    // 需要new实例
    new Vue({
        el:'#select',
        data(){
            return {
                value:'',
                options: [
                    {
                        id: 'Option1',
                        name: 'Option1',
                    },
                    {
                        id: 'Option2',
                        name: 'Option2',
                    }
                ] 
            }
        }
    })
</script>
```
## homepage修改展示主页
```js
// 默认为根节点下的README.md文件
window.$docsify = {
    homepage:'home.md',
    ...
}
```
## 全局搜索
```js
// index.html 
window.$docsify = {
    search: 'auto', // 默认值
    search: {
        maxAge: 86400000, // 过期时间，单位毫秒，默认一天
        paths: [], // or 'auto'
        // 支持本地化
        placeholder: {
        '/': '搜索'
        },
        // 支持本地化
        noData: {
        '/': '找不到结果'
        },
        // 搜索标题的最大层级, 1 - 6
        depth: 4,
        hideOtherSidebarContent: false, // 是否隐藏其他侧边栏内容
    }
}
  <script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/search.min.js"></script>
```

## 引入本地静态图片
```
<image src="/assets/img/nav.png">
```
## 右上角地址挂件
```js
// index.html 
window.$docsify = {
    repo:'https://docsify.js.org/#/configuration', // 右上角地址挂件
}
```

## 代码复制功能
```js
// index.html 
<script src="//cdn.jsdelivr.net/npm/docsify-copy-code/dist/docsify-copy-code.min.js"></script>
```
## 图片缩放功能
```js
<script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/zoom-image.min.js"></script>
```

## 字数统计 docsify-count
```js
https://unpkg.com/docsify-count/dist/countable.min.js
https://unpkg.com/docsify-count/dist/countable.js
https://unpkg.com/docsify-count/dist/
```
