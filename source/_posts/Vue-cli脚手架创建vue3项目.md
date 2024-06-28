---
title: Vue-cli脚手架创建vue3项目
tags:
  - Vue
categories:
  - 教程
comments: false
abbrlink: 38573
date: 2023-02-07 12:31:49
updated: 
keywords:
description:
top_img:
cover:
---

<font size=5 color=#f33b45>**Vue-cli脚手架创建vue3项目**</font>

<font size=4 color=#3399ea>**原创：丶无殇&emsp;&emsp;2023-02-07**</font>

---

如果需要使用vite可以跳转[文章末尾](#vite_255)

---
# Vue-cli脚手架创建vue3项目

安装vue-cli脚手架
--

执行：`npm install -g @vue/cli`

脚手架安装具体内容不在此赘述

---
创建项目（默认配置）
--

执行`vue create {filename}`

`{filename}`整个替换为你的项目名称，一定要`全部小写`，否则会报错：

> Warning: name can no longer contain capital letters

### 创建

输入：

```powershell
vue create test01
```

输出：

```powershell
Vue CLI v5.0.8

? Please pick a preset:
> Default ([Vue 3] babel, eslint) 
  Default ([Vue 2] babel, eslint) 
  Manually select features
```

使用<kbd>↑</kbd><kbd>↓</kbd>按键操作，`>`指向的为选中的

然后输入：回车

输出：

```powershell
Vue CLI v5.0.8
✨  Creating project in ██████████████████████████████\test01.
⚙️  Installing CLI plugins. This might take a while...

[██████............] / idealTree:serve-index: sill fetch manifest unpipe@~1.0.0
```

然后安装好之后会显示：

```powershell
added 102 packages in 20s
⚓  Running completion hooks...

📄  Generating README.md...

🎉  Successfully created project vue3test.
👉  Get started with the following commands:

 $ cd test01
 $ npm run serve
```

至此项目创建完成，这是默认配置的创建，如果需要手动配置，可进行以下操作

---

创建项目（手动配置）
--

执行`vue create {filename}`

`{filename}`整个替换为你的项目名称，一定要`全部小写`，否则会报错：

> Warning: name can no longer contain capital letters

### 创建

输入：

```powershell
vue create test02
```

输出：

```powershell
Vue CLI v5.0.8

? Please pick a preset:
  Default ([Vue 3] babel, eslint) 
  Default ([Vue 2] babel, eslint) 
> Manually select features
```

使用<kbd>↑</kbd><kbd>↓</kbd>按键操作，`>`指向的为选中的

然后输入：回车

### 配置功能

回车后会显示功能列表，可以根据项目的需求选择对应的功能：

```powershell
? Check the features needed for your project: (Press <space> to select, <a> to toggle all, <i> to invert selection, and <enter> to proceed)
>(*) Babel
 ( ) TypeScript
 ( ) Progressive Web App (PWA) Support
 ( ) Router
 ( ) Vuex
 ( ) CSS Pre-processors
 (*) Linter / Formatter
 ( ) Unit Testing
 ( ) E2E Testing
```

此时，可以通过<kbd>空格(Space)</kbd>进行选择和取消选择，<kbd>a</kbd>全选，<kbd>i</kbd>反选，<kbd>回车(Enter)</kbd>继续

`Router`和`Vuex`一般会用上，如果是单页应用可以不选择

选择完成后回车

### 版本选择

然后根据项目需求选择`Vue.js`的版本

```powershell
? Choose a version of Vue.js that you want to start the project with (Use arrow keys)
> 3.x
  2.x
```

现在大多是`Vue3`，所以选择默认的`3.x`后回车即可

### History模式

此处需要选择`是否使用路由的历史记录模式`，一般选择是，也可根据项目需求来

```powershell
? Use history mode for router? (Requires proper server setup for index fallback in production) (Y/n) 
```

输入`Y`后回车

### 格式检测

接下来的是一个代码格式检测的，一般公司会要求这个必须选择

```powershell
? Pick a linter / formatter config: (Use arrow keys)
> ESLint with error prevention only
  ESLint + Airbnb config
  ESLint + Standard config
  ESLint + Prettier
```

此处选择默认第一个即可，然后选择Lint的其他功能：

1. 保存时候Lint
2. Git提交时候

这里建议保存时候检测代码

```powershell
? Pick additional lint features: (Press <space> to select, <a> to toggle all, <i> to invert selection, and <enter> to proceed)
>(*) Lint on save
 ( ) Lint and fix on commit (requires Git)
```

回车后继续

### 配置方式

选择Babel，ESLint等功能的配置方式：

1. 在专属配置文件里面
2. 在`package.json`

```powershell
? Where do you prefer placing config for Babel, ESLint, etc.? (Use arrow keys)
  In dedicated config files
> In package.json
```

这里博主使用的是`package.json`，可以选择在专属配置文件里面

### 另存预设

以上的配置是否保存为一个预设，以后可以直接使用此配置

```powershell
? Save this as a preset for future projects? (y/N)
```

选择`Y`的话，需要设置一个名称，比如叫`setting01`

```powershell
? Save preset as: setting01

🎉  Preset tempset saved in C:\Users\User\.vuerc
```

然后就开始自动安装了

### 配置总览

```powershell
Vue CLI v5.0.8
? Please pick a preset: Manually select features
? Check the features needed for your project: Babel, Router, Linter
? Choose a version of Vue.js that you want to start the project with 3.x
? Use history mode for router? (Requires proper server setup for index fallback in production) Yes
? Pick a linter / formatter config: Basic
? Pick additional lint features: Lint on save
? Where do you prefer placing config for Babel, ESLint, etc.? In package.json
? Save this as a preset for future projects? Yes
? Save preset as: setting01

🎉  Preset tempset saved in C:\Users\User\.vuerc
```

### 安装完成

安装完成后提示

```powershell
🎉  Successfully created project vue3test1.
👉  Get started with the following commands:

 $ cd test02
 $ npm run serve
```

进入文件夹`cd test02`后就可以`npm run serve`然后查看创建的默认项目了


---

如果需要使用Vite创建，可以使用下面的方法

Vite脚手架创建vue3项目
==


## 安装vite
```sh
npm install vite@latest
```


## 创建项目
```sh
npm init vite@latest
//或者
npm create vite@latest
```

流程如下：
```sh
> npm init vite@latest
√ Project name: ... testvue
√ Package name: ... testvue
? Select a framework: » - Use arrow-keys. Return to submit.
    Vanilla
>   Vue
    React
    Preact
    Lit
    Svelte
    Solid
    Qwik
    Others
? Select a framework: » - Use arrow-keys. Return to submit.
    Vanilla
>   Vue
    React
√ Select a framework: » Vue
√ Select a variant: » JavaScript
```

