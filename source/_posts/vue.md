---
title: vue
date: 2020-04-09 15:23:05
categories: vue
summary: 记录vue一些常用方法操作注意等
tags:
 - vue
---

 1. 当页引用vue时注意，IE的不兼容性es6，如果data(){}需写成 data:function()
 2. 加载闪屏

    ```js
    v-cloak
    [v-cloak] {
        display: none;
    }
    ```
 3. 取消事件冒泡 @click.stop，阻止默认事件  @click.prevent