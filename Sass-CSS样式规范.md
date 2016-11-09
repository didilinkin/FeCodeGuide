# Sass and CSS style rules——Sass与CSS 样式规范

## 1. 命名规范

ID和class(类)名总是使用可以反应元素目的和用途的名称，或其他通用名称。

代替表象和晦涩难懂的名称。

应该首选具体和反映元素目的的名称，因为这些是最可以理解的，而且发生变化的可能性最小。

通用名称只是多个元素的备用名，他们兄弟元素之间是一样的，没有特别意义。

#### **不推荐**
```SASS
.fw-800
    font-weight: 800
.red
    color: red
```

#### **推荐**
```SASS
.heavy
    font-weight: 800
.important
    color: red
```

## 稳定项目(长期维护)使用BEM命名法
### BEM简述
```CSS
.block{ ... } /* 模块 */
.block__element{ ... } /* 模块的子元素 */
.block--modifier{ ... } /* 模块的修饰样式 */
```

#### **BEM命名法需要注意的问题**

1. 避免过长嵌套(不宜超过3层嵌套,超过4层 通过Sass方法跳出嵌套`@at-root`)

2. BEM命名需要语义化，能立刻明白class/ID 所描述的内容

3. BEM的命名单词尽可能简练,当需要多个单词拼接时使用`驼峰`命名方法
```CSS
.module__returnBtn
    {...}
```
