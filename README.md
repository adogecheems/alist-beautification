# ALIST-BEAUTIFICATION

这是一个alist/openlist美化代码存储库，但特别的是，它提供了一种与传统美化代码不同的、全新的实现原理。

它并非是按照以往的做法，对alist/openlist的前端元素进行枚举修改，而是加载了一个动态的监视器，自动地对带有背景色的元素进行替换颜色，从而在alist/openlist前端功能更新时有更好的适应性。

可以在[我的博客](https://blog.mmoe.work/alist-js-beautification/)查看相关介绍。

## 组件

- `head.html`: 自定义头部，不过事实上与这个项目的主体没有什么关系，是自定义字体一类的传统的美化代码。
- `body.html`: 自定义内容，这个项目的核心，包含了动态美化监视器。
- `src/beautifier.js`: 动态美化监视器的js代码， 是`body.html`的一部分。

## 使用方法

直接将`head.html`和`body.html`的内容复制到alist的自定义头部和自定义内容中即可（位于`/设置/全局`中）

### 通过cdn引入

 如果你只需要美化alist背景色，而不需要自定义头部提供的功能，可以直接从cdn引入`beautifier.js`：

```html
<!-- 修正部分区域的透明 -->
<style>
    .hope-ui-light,
    .hope-ui-dark {
        --hope-colors-background: transparent;
    }
</style>

<script type="module" src="https://fastly.jsdelivr.net/gh/adogecheems/alist-beautification@latest/src/beautifier.js"></script>
```

### 控制台

美化器实例暴露了三个方法：

- `observe()`: 开始监听页面变化并美化背景色
- `disconnect()`: 停止监听页面变化
- `undo()`: 恢复页面背景色到默认状态

你可以通过window对象访问美化器实例，比如在控制台中输入以下命令可以完全消除美化效果：

```javascript
window.beautifier.undo();
```

### 对默认背景色不满意？

在`body.html`的第58行附近（在`beautifier.js`中是47行）找到以下代码，你可以修改这些变量来调整默认背景色：

```javascript
static lightBgColor = 'rgba(255, 255, 255, 0.8)';
static darkBgColor = 'rgb(32, 36, 37)';
//                                         ^
// 这里可以修改为你想要的默认背景色
//比如为黑夜模式也加入半透明：
static lightBgColor = 'rgba(255, 255, 255, 0.8)';
static darkBgColor = 'rgba(32, 36, 37, 0.8)';
```

## 对登录界面的美化

如果你想要对alist的登录界面进行美化，可以使用`body_with_login.html`替换`body.html`的内容。

## 关于

对你有用的话，就请给我点个star支持一下吧！  
作者：adogecheems  
许可：AGPL-3.0
