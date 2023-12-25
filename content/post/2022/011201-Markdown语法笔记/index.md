---
title: 'Markdown语法'
date: 2022-01-12T6:00:00+08:00
keywords:
  - '文章'
---

原在2021年3月于有道云笔记发布，那边不想再打开了所以搬运一下

<!--more-->

## Markdown语法

<div id="目录"></div>

### 目录

- [代码高亮](#代码高亮)
- [制作待办事项](#制作待办事项)
- [高效绘制](#高效绘制)
    - [流程图](#流程图)
    - [序列图](#序列图)
- [列表](#列表)
- [区块引用](#区块引用)
- [粗体斜体](#粗体斜体)
- [删除线](#删除线)
- [链接和图片](#链接和图片)
- [分割线](#分割线)
- [表格](#表格)
- [跳转](#跳转)

---

<div id="代码高亮"></div>

### 代码高亮

```markdown
``csharp
private int age; //字段
``
``diff
- features = ["dynamic"]
+ features = ["jpeg", "dynamic"]
``
```


效果

```csharp
private int age; //字段
```
```diff
- features = ["dynamic"]
+ features = ["jpeg", "dynamic"]
```

---

<div id="制作待办事项"></div>

- 制作待办事项

```markdown
- [x] 已完成项目1
  - [x] 啊这1
  - [ ] 啊这2
- [ ] 未完成项目
```
效果

- [x] 已完成项目1
  - [x] 啊这1
  - [ ] 啊这2
- [ ] 未完成项目

> 二级分支要空两格 不要用Tab比较好 虽然一样

<div id="高效绘制"></div>

### 高效绘制

<div id="流程图"></div>

> 【注意!此部分样式未补全因此非最终效果】

- 流程图

```markdown
``
graph TD
    A[Christmas] -->B(Go shopping)
    B --> C{Let me think}
    C -->|One| D[Laptop]
    C -->|Two| E[iPhone]
    C -->|Three| F[Car]
``
```
效果

``
graph TD
    A[Christmas] -->B(Go shopping)
    B --> C{Let me think}
    C -->|One| D[Laptop]
    C -->|Two| E[iPhone]
    C -->|Three| F[Car]
``

<div id="序列图"></div>

- 序列图

```markdown
``
sequenceDiagram
    loop Everyday
        Alice->>John: Hello John, how are you?
        John-->>Alice: Great!
    end
``
```
效果

```
sequenceDiagram
    loop Everyday
        Alice->>John: Hello John, how are you?
        John-->>Alice: Great!
    end
```

---
# 待续

> **Tips:** 按住Alt+鼠标左键可以方框多选
---

<div id="列表"></div>

## 列表

**无序**

```markdown
- 列表1
    - 列表1.1
    - 列表1.2
- 列表2
```
效果

- 列表1
    - 列表1.1
    - 列表1.2
- 列表2

---

**有序**

```markdown
1. 列表1
    1. 列表1.1
    2. 列表1.2
2. 列表2
```

效果

1. 列表1
    1. 列表1.1
    2. 列表1.2
2. 列表2


<div id="区块引用"></div>

- 区块引用

```markdown
> 一级引用
>> 二级引用
>>> 三级引用
```
效果

> 一级引用
>> 二级引用
>>> 三级引用

---

<div id="粗体斜体"></div>

- 粗体斜体
```markdown
*斜体*
```
效果

*斜体*

---

```markdown
**粗体**
```

**粗体**

符号与文本之间无须空格

---

<div id="删除线"></div>

- 删除线

```markdown
~~删除~~
``````

~~删除~~

---

<div id="链接和图片"></div>

**链接和图片**

- 文字链接

```markdown
[百度官网](www.baidu.com)
```

[百度官网](www.baidu.com)

- 图片链接

```markdown
![图片名字](图片链接)

![favicon](https://blog.himesamanoyume.top/favicon.ico)
```

![favicon](https://blog.himesamanoyume.top/favicon.ico)

> 区别就是图片链接最前面多了个"!"

---

<div id="分割线"></div>

- 分割线

```markdown
---
```
> 连续多个- 一行
```markdown
***
```
> 连续三星号一行

---

<div id="表格"></div>

- 表格

```markdown
表头1|表头2
---|---
左上|右上
左下|右下

header1|header2
:------|------:
left|right|

|header1|header2|
|------|------|
|left|right|

header1 | header2
:--|---
left|right
```

表头1|表头2
---|---
左上|右上
左下|右下

header1|header2
:------|------:
left|right|

|header1|header2|
|------|------|
|left|right|

header1 | header2
:--|---
left|right

<div id="跳转"></div>

- 跳转
```markdown
> 带#是本地跳转的

[跳转到temp](#temp)

<div id="temp"></div>
将会跳转到改div块所在位置
```

[跳转到temp](#temp)



```markdown
> 不带#会打开网页跳转

[跳转到temp 不带#](temp)

[跳转到主页 不带#](https://blog.himesamanoyume.top)

```

[跳转到temp 不带#](temp)

[跳转到主页 不带#](https://blog.himesamanoyume.top)
