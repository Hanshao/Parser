# Parser
> 小程序富文本插件，详见 [文档](https://jin-yufeng.github.io/Parser)  

![star](https://badgen.net/github/stars/jin-yufeng/Parser)
![forks](https://badgen.net/github/forks/jin-yufeng/Parser)
![last-commit](https://badgen.net/github/last-commit/jin-yufeng/Parser)
![license](https://badgen.net/github/license/jin-yufeng/Parser)  

## 功能简介 ##
- 支持匹配 `style` 中的样式  
- 支持 `svg`  
- 支持锚点跳转  
- 支持设置占位图  
- 支持长按复制内容  
- 支持给多媒体标签设置多个源  
- 支持自动给链接填充主域名  
- 支持几乎所有的 `html` 标签  
- 支持丰富的事件和效果  
- 轻量化、效率高、容错性强  
- 支持多平台（微信、QQ、百度、支付宝、头条、uni-app 等）  
...

更多功能可见：[功能介绍](https://jin-yufeng.github.io/Parser/#/)

## 使用方法 ##
### 插件包说明 ##

| 名称 | 大小 | 使用 |
|:---:|:---:|:---:|
| parser | 39.9KB | 微信小程序插件包 |
| parser.min | 25.2KB | 微信小程序插件包压缩版（功能相同） |
| parser.qq | 39.5KB | QQ 小程序插件包 |
| parser.bd | 37.9KB | 百度小程序插件包 |
| parser.my | 38.3KB | 支付宝小程序插件包 |
| parser.tt | 38.7KB | 头条小程序插件包 |
| parser.uni | 57.8KB | `uni-app` 插件包（可以编译到所有平台） |

### 在原生框架中使用 ###
1. 复制 `parser` 文件夹至 `components` 目录  
2. 在需要使用页面的 `json` 文件中添加  
   
   ```json
   {
     "usingComponents": {
       "parser":"/components/parser/parser"
     }
   }
   ```
3. 在需要使用页面的 `wxml` 文件中添加  
   
   ```html
   <parser html="{{html}}" />
   ```
4. 在需要使用页面的 `js` 文件中添加  
   
   ``` javascript
   data: {
     html:"<div>Hello World!</div>"
   }
   ```
- `demo/wx` 文件夹下的是微信小程序 `富文本插件` 示例程序的源码，可供参考  

### 在 uni-app 中使用 ###
1. 复制 `parser.uni` 包到 `components` 目录下（更名为 `jyf-parser`）  
2. 在需要使用页面的 `vue` 文件中添加  
   
   ```vue
   <template>
     <view>
       <jyf-parser :html="html"></jyf-parser>
     </view>
   </template>
   <script>
   import parser from "@/components/jyf-parser/jyf-parser"; // HBuilderX 2.5.5 及以上可以不需要引入
   export default {
     // HBuilderX 2.5.5 及以上可以不需要引入
     components: {
       "jyf-parser": parser
     },
     data() {
       return {
         html: '<div>Hello World!</div>'
       }
     }
   }
   </script>
   ```
- 可以直接通过 [插件市场](https://ext.dcloud.net.cn/plugin?id=805) 引入
- `demo/uni-app` 文件夹下是一个示例程序，可供参考  

其他框架中使用可见：[在其他框架中使用](https://jin-yufeng.github.io/Parser/#/instructions?id=在其他框架中使用)

### 组件属性 ###  

| 属性 | 类型 | 默认值 | 说明 |
|:----:|:----:|:----:|----|
| html | String |  | 要显示的 html 字符串 |
| autopause | Boolean | true | 是否允许播放视频时自动暂停其他视频 |
| autoscroll | Boolean | false | 是否自动给 table 加一个滚动层（使表格可以单独滚动） |
| autosetTitle | Boolean | true | 是否自动将 title 标签的内容设置到页面标题 |
| compress | Number | 0 | 压缩等级，可以选择是否移除 id 和 class |
| domain | String |  | 主域名，设置后将给链接自动拼接主域名或协议名 |
| lazy-load | Boolean | false | 是否开启图片懒加载 |
| loading-img | String |  | 图片加载完成前的占位图，详见 [占位图](https://jin-yufeng.github.io/Parser/#/#设置占位图) |
| selectable | Boolean | false | 是否允许长按复制内容 |
| show-with-animation | Boolean | false | 是否使用渐显动画 |
| tag-style | Object |  | 设置标签的默认样式 |
| use-anchor | Boolean | false | 是否使用页面内锚点 |
| use-cache | Boolean | false | 是否使用缓存，设置后多次打开不用重复解析 |
  
详细可见：[组件属性](https://jin-yufeng.github.io/Parser/#/instructions?id=组件属性)

### 事件 ###

| 名称 | 功能 | 说明 |
|:----:|----|----|
| bindparse | 解析完成时触发 | 返回解析结果，可以对该结果进行自定义修改，将在渲染时生效 |
| bindload | dom 加载完成时触发 | 所有节点被添加到节点树中时触发，无返回值，可以调用 api |
| bindready | 渲染完成时触发 | 返回 boundingClientRect 的查询结果（包含宽高、位置等信息），所有图片（除懒加载）加载完成时才会触发，图片较大时可能 **延时较长** |
| binderror | 出错时触发 | 返回一个 object，其中 source 是错误来源，errMsg 为错误信息，target 包含出错标签的具体信息 |
| bindimgtap | 图片被点击时触发 | 返回一个 object，其中 src 是图片链接，ignore 是一个函数，在回调函数中调用将不进行预览 |
| bindlinkpress | 链接被点击时触发 | 返回一个 object，其中 href 是链接地址，ignore 是一个函数，在回调中调用将不自动跳转/复制 |  

详细可见：[事件](https://jin-yufeng.github.io/Parser/#/instructions?id=事件)
  
### 使用外部样式 ###
如果需要使用一些固定的样式，可以通过 `wxss` / `css` 文件引入  
在 `parser/trees/trees.wxss(css)` 中通过 `@import` 引入自定义的样式文件即可  
```css
/*
* parser/trees/trees.wxss(css)
* 在这里引入您的自定义样式
*/
@import "external.wxss(css)";
```

更多信息可见：[使用方法](https://jin-yufeng.github.io/Parser/#/instructions)

## 扩展包 ##
`patches` 文件夹中准备了一些扩展包，可根据需要选用，可以实现更加丰富的功能  
具体信息见：[扩展包](https://jin-yufeng.github.io/Parser/#/instructions?id=扩展包)

## 案例体验 ##

| [富文本插件](https://github.com/jin-yufeng/Parser/tree/master/demo/wx) | [程序员技术之旅](https://github.com/fendoudebb/z-blog-wx) | [极客时代](https://github.com/GeekEra/GBlog-wx) | APP 比比 | 全品作业小助手 |
|:---:|:---:|:---:|:---:|:---:|
| <img src="https://6874-html-foe72-1259071903.tcb.qcloud.la/md/md5.jpg?sign=911a1fd62af2666f9c8dfa367b22479c&t=1574499374" width="200" alt="富文本插件"> | <img src="https://user-images.githubusercontent.com/16144460/74083526-0528bc80-4aa0-11ea-841f-a974c5f9131d.jpg" width="200" alt="程序员技术之旅"> | <img src="https://camo.githubusercontent.com/f15b6b8854ae6d7fc4ceea552b79e326d5036978/68747470733a2f2f63646e2e66757a75692e6e65742f626c6f672f7172636f64655f313539323230383033333536372e6a7067" width="200" alt="极客时代"> | <img src="https://user-images.githubusercontent.com/5304020/80313264-70229d80-881c-11ea-8d8f-aed45719aed5.jpg" width="200" alt="APP 比比"> | <img src="https://user-images.githubusercontent.com/21222276/80563130-b3e3f580-8a1c-11ea-9a07-7671ea5aa320.jpg" width="200" alt="全品作业小助手"> |

| 多么生活 | 恋爱宝典 xcx | 古典文学名著阅读 | 典典博客 | |
|:---:|:---:|:---:|:---:|:---:|
| <img src="https://user-images.githubusercontent.com/16403746/69929565-665d6e00-14fa-11ea-807a-8d9050caf342.jpg" width="200" alt="多么生活"> | <img src="https://user-images.githubusercontent.com/22900470/70421652-2de30480-1aa5-11ea-93b0-180352d4c397.jpg" width="200" alt="恋爱宝典 xcx"> | <img src="https://camo.githubusercontent.com/bb2aa4562a8b4912c82129f10ff15d1eb4ce0d08/68747470733a2f2f63646e2e6e6c61726b2e636f6d2f79757175652f302f323031392f6a7065672f3432383733322f313537353830303731333133312d36326639663836362d366233362d343766312d396234302d6132633964373839616633362e6a706567" width="200" alt="古典文学名著阅读"> | <img src="https://6874-html-foe72-1259071903.tcb.qcloud.la/%E5%85%B8%E5%85%B8%E5%8D%9A%E5%AE%A2.jpg?sign=5b2d371a4bd840c14c8d3740c35ee07f&t=1586360436" width="200" alt="典典博客"> | <img width="200"> |

以上排名不分先后，更多可见：[链接](https://github.com/jin-yufeng/Parser/issues/27)（欢迎添加）  

相关项目：  
[EastWorld/wechat-app-mall](https://github.com/EastWorld/wechat-app-mall)  
[zhangdaren/miniprogram-to-uniapp](https://github.com/zhangdaren/miniprogram-to-uniapp)  

## 许可与支持 ##
- 许可  
  您可以随意的使用和分享本插件 [MIT License](https://github.com/jin-yufeng/Parser/blob/master/LICENSE)  
  不可用于任何违法用途  
  在用于生产环境前务必经过充分测试，由插件 `bug` 带来的损失概不负责（可以自行修改源码）  

- 支持  
  ![支持](https://6874-html-foe72-1259071903.tcb.qcloud.la/md/md6.png?sign=24395ad7572c19464db67d8997e3b2d2&t=1574502139)   


## 更新日志 ##
- 2020.6.15  
  1. `U` 文档添加 [性能优化建议](https://jin-yufeng.github.io/Parser/#/question#性能优化建议) 和 [体验优化建议](https://jin-yufeng.github.io/Parser/#/question#性能优化建议)  
  2. `D` `html` 属性不再支持 `Array` 类型（传入 `Array` 的优化程度有限（解析时间基本 `<50ms`）；但相同的内容，解析为 `Array` 后会增加大小，进而导致网络传输时间增加；因此大部分情况下传入 `Array` 起到的优化效果不大，甚至可能负优化，还增加了处理复杂度）  

- 2020.6.11  
  1. `A` 增加支付宝小程序原生包 [详细](https://jin-yufeng.github.io/Parser/#/instructions#插件包说明)  
  2. `U` `uni-app` 包适配华为快应用  
  3. `U` `uni-app` 包编译到 `App` 时实现了 `lazy-load` 属性（图片懒加载）  
  4. `F` 修复了 `ios` 端图片长按可能导致页面失去响应的问题 [详细](https://github.com/jin-yufeng/Parser/issues/130)  
  5. `F` 修复了 `uni-app` 包多次设置 `html` 内容时可能出现一些不正确情况的问题  
  6. `D` 移除了 `trustAttrs` 的配置项，改为自动移除 `data-` 开头的属性  

- 2020.5.28  
  1. `U` `uni-app` 包适配 `360` 小程序（由于 `360` 小程序在浏览器中运行，和 `H5` 处理方式相同）  
  2. `F` 修复了属性名后有空格会无法识别的问题 [详细](https://github.com/jin-yufeng/Parser/issues/152)  
  3. `F` 修复了 `img` 没有设置 `src` 会报错的问题  
  4. `F` 修复了 `uni-app` 包部分情况下 `errorImg` 失效的问题  
  5. `F` 修复了 `uni-app` 包编译到 `NVUE` 时若 `html` 中含有换行符可能无法显示的问题  
  6. `F` 修复了 `uni-app` 包编译到 `App` 时前几秒点击视频无法播放的问题  

- 2020.5.24
  1. `A` 增加 `loading-img` 属性，可以设置图片加载完成前的占位图 [详细](https://jin-yufeng.github.io/Parser/#/#设置占位图)  
  2. `A` 增加 `errorImg` 的配置项，可以设置图片出错时的占位图 [详细](https://jin-yufeng.github.io/Parser/#/#设置占位图)   
  3. `F` 修复了 `uni-app` 包使用 [audio 扩展包](https://jin-yufeng.github.io/Parser/#/instructions?id=audio) 后编译到百度小程序出错的问题  
  4. `D` `error` 事件中不再返回 `context` 对象  

- 2020.5.21
  1. `U` 支持 `embed` 标签（`type` 中含 `video` 或后缀名为 `.mp4`、`.3gp`、`.m3u8` 的将被转为视频；`type` 中含 `audio` 或后缀名为 `.m4a`、`.wav`、`.mp3`、`.aac` 的将被转为音频；其余不支持）  
  2. `U` 音视频如果既没有设置 `autoplay` 也没有设置 `controls` 将自动设置 `controls`，避免无法播放  
  3. `F` 修复了锚点无法跳转到 `li` 和 `a` 标签的问题 [详细](https://github.com/jin-yufeng/Parser/issues/142)  
  4. `F` 修复了部分情况下 `svg` 标签 `style` 中的 `vertical-align` 无法生效的问题  
  5. `F` 修复了未闭合的标签如果是 `rich-text` 不支持的标签可能无法显示的问题 [详细](https://ask.dcloud.net.cn/question/96579)  
  6. `F` 修复了 `error` 事件中通过 [setSrc](https://jin-yufeng.github.io/Parser/#/instructions?id=%e5%85%b3%e4%ba%8e-error-%e4%ba%8b%e4%bb%b6) 重设图片地址后无法预览的问题  
  7. `F` 修复了微信包个别情况下可能出现 `null is not an object` 错误的问题 [详细](https://github.com/jin-yufeng/Parser/issues/146)  
  8. `F` 修复了百度包部分情况下预览时无法左右滑动查看所有图片的问题
  9. `F` 修复了 `uni-app` 包编译到百度小程序安卓真机可能无法显示的问题 [详细](https://github.com/jin-yufeng/Parser/issues/139)  
  10. `F` 修复了 `uni-app` 包编译到 `NVUE` 时通过 `v-if` 切换可能无法显示的问题 [详细](https://github.com/jin-yufeng/Parser/issues/147)  
  11. `F` 修复了 `uni-app` 包编译到 `app` 时 `iframe` 无法全屏的问题  

更多可见：[更新日志](https://jin-yufeng.github.io/Parser/#/changelog)
