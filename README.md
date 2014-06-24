# saber-firework [![Build Status](https://travis-ci.org/ecomfe/saber-firework.png)](https://travis-ci.org/ecomfe/saber-firework)

移动端`MVP`开发框架，使用[etpl](https://github.com/ecomfe/etpl)作为模版引擎，结合[页面转场](https://github.com/ecomfe/saber-viewport)与[路由管理](https://github.com/ecomfe/saber-router)，提供完整的`SPA`解决方案。

## Usage

```javascript
var firework = require('saber-firework');

// 加载index配置
firework.load({
    path: '/index',
    action: require('./index')
});

// 启动App
firework.start();
```

参考[使用指南](doc/guide.md)

## API

### .load(route)

加载路由配置信息

* `route` `{Object|Array.<Object>}` 路由配置信息，具体参考[doc/route](doc/route.md)

### .start(ele, options)

启动App

* `ele ` `{HTMLElement}` 容器元素
* `options` `{Object}` 全局配置信息，具体参考[doc/config](doc/config.md)

### .addFilter(url, fn)

添加在加载页面前执行的filter

* `url ` `{string|RegExp=}` filter匹配的url或者url正则表达式，如果不设置则filter对所有url都生效
* `fn` `Function(route, next, stop, jump)` filter，支持异步操作，有四个参数：
    * `route` `{Object}` 路由信息，包括页面URL`path`与查询条件`query`等
    * `next` `{Function}` 执行下一个filter
    * `stop` `{Function}` 终止页面的加载
    * `jump` `{Function(num)}` 跳过后续的filter

### .on(name, fn)

绑定事件

* `name ` `{string}` 事件名称，具体请参考[事件说明](#events)
* `fn` `{Function}` 事件处理函数

## Events

### beforeload

加载页面前事件，有两个参数，`after`待转加载页面信息 与 `before`当前页面信息

* `{Object}` after 待转加载页面信息
* `{Action}` after.action 待转加载的[action对象](doc/action.md)
* `{Page}` after.page 待转加载的[page对象](https://github.com/ecomfe/saber-viewport#page)
* `{Object}` before 当前页面信息
* `{Action}` before.action 当前的[action对象](doc/action.md)
* `{Page}` before.page 当前的[page对象](https://github.com/ecomfe/saber-viewport#page)

### beforetransition

转场动画开始前事件，参数同[beforeload](#beforeload)

### afterload

页面加载完成事件，参数同[beforeload](#beforeload)

### error

页面加载失败事件，参数同[beforeload](#beforeload)

===

[![Saber](https://f.cloud.github.com/assets/157338/1485433/aeb5c72a-4714-11e3-87ae-7ef8ae66e605.png)](http://ecomfe.github.io/saber/)
