---
title: bpmwebapp
date: 2020-03-25 11:14:56
categories: bpm
summary: bpm webapp部署及说明文档
comments: true
 # password: a665a45920422f9d417e4867efdc4fb8a04a1f3fff1fa07e998e86f7f7a27ae3
tags:
- html
- vue
- .net
---
<img src="bpmadpp/image/4.PNG" width = "400" height = "400"  alt ="样例效果" align=center >

<video width="100%" height="320" controls>
<source src="image/1.MP4">
</video>

`预览地址`


[bpmwebapp](http://emip.lxyzy.top:8081/emip/app/dist/#/login)


# APP界面结构说明

<img src="bpmadpp/image/12.png" width = "100%" height = "800"  alt ="app结构说明" align=center >

# 部署文件
 - <a href="http://www.linxueyang.cn/2020/03/26/bpmwebappversion/" target="_blank">BPMWEBAPP版本</a>


# 环境配置
## BPM

```
安装BPM，安装包自行获取
```
## EMIP
```
部署EMIP到BPM中
```
`以下说明 默认EMIP在BPM中的应用程序，并不在根目录，如在根目录自行修改`
## APP部署
### 文件拷贝
```
  1. 将 文件目录中=> 部署文件 => EMIP         拷贝到部署的emip中进行文件替换 
  2. 将 文件目录中=> 部署文件 => appsql.sql   执行到数据库中(目前只支持sqlserver数据库) 
```
`表结构说明`

|  表名   | 说明  |
|  ----  | ----  |
| BPMAPPADMIN_HOME_MENUS  | 菜单表，存储菜单 |
| BPMAPPADMIN_HOME_MENUS_PERM  | 菜单权限表 |
| BPMAPPADMIN_HOME_NOTICE  | 通知公告配置表 |
| BPMAPPADMIN_HOME_SWIPE  | 新闻轮播配置表 |
| BPMAPPADMIN_MENU_APPCONFIG  | 菜单中应用配置表 |
| BPMAPPADMIN_PERSONAL_CONFIG  | 个人配置表目前只有存储中英文 |
| BPMAPPADMIN_TBAR_D  | 底部tbar明细表 |
| BPMAPPADMIN_TBAR_M  | 底部tbar主表，选择颜色 |

### 访问
 #### 本地访问
 ```
  1. 后台管理：http://本地地址/emip/admin/dist/          (只有超级管理员即administartor组可以登录配置)
  2. webapp:  http://本地地址/emip/app/dist/#/login     (默认登录账号为sa,如需修改请修改 emip/appadmin/login/login.ashx 见下图)  
```
`如果访问出现http错误，检查EMIP\Web\APP\dist\index.html 中 yzapiurl配置是否当前程序地址，默认是emip`

<img src="bpmadpp/image/20.png" width = "100%" height = "400"  alt ="修改yzapiurl" align=center >

<img src="bpmadpp/image/1.png" width = "100%" height = "400"  alt ="替换登录账号" align=center >
 
 #### 微信访问
  ```
  1. 修改 EMIP\Web\APP\dist\index.html 中 agentId corpid appSecret (具体获取方法请查询微信企业号官网)
  2. 配置企业号后台，
     工作台应用主页：http://域名/emip/app/dist/#/wechat
     网页授权及JS-SDK: 域名（必须配置，不然没法登录和使用附件上传）
```
`如果访问出现http错误，检查EMIP\Web\APP\dist\index.html 中 yzapiurl配置是否当前程序地址，默认是emip`
<img src="bpmadpp/image/3.png" width = "100%" height = "400"  alt ="修改index" align=center >
<img src="bpmadpp/image/2.png" width = "100%" height = "400"  alt ="企业号配置" align=center >

## 应用配置
### 后台登录

```
 http://本地地址/emip/admin/dist/    (只有超级管理员即administartor组可以登录配置)
```
`如需修改登录administartor组限制，可修改文件EMIP\Web\appadmin\api\login.ashx中的配置`

<img src="bpmadpp/image/5.png"  width = "100%" height = "800"  alt ="后台配置页面" align=center >

### Tbar配置

```
 点击右侧编辑
```

<img src="bpmadpp/image/6.png"  width = "100%" height = "800"   alt ="Tbar" align=center >

`参数说明`

|  字段   | 必填  |   说明  |
|  ----  | ----  |   ----  |
| 选中标签的颜色      | 是 | tbar点击选择时显示的颜色 |
| 未选中标签的颜色     | 是  | tbar未点击选择时显示的颜色 |


#### 新增Tbar

<img src="bpmadpp/image/7.png"  width = "100%" height = "800"  alt ="Tbar配置" align=center >

`参数说明`

|  字段   | 必填  |   说明  |
|  ----  | ----  |   ----  |
| CODE      | 否 | 用于后台判断，index时可以配置主页，其他值可以随便填写 |
| 中文名     | 是  | 底部tabr中文名称 |
| 英文名     | 否  |切换英文时显示，如果为空，切换英文时显示中文 |
| 选中图片   | 是 | 点击tbar显示的图片，图片颜色最好和tbar选中标签的颜色一致,图片必须为PNG且小于1M  |
| 未选中图片 | 是 | 未点击显示的图片,图片必须为PNG且小于1M |
| 地址  | 是 | 可配两种地址<br/>1.vue ：路由地址 <br/>2.html : /html?url=http://baidu.com&name=百度<br/>默认两个地址1./index(主页) 2./my(我的)|
| 排序  | 是 |tbar显示的顺序 |

`如果上传图片提示权限不足，需把文件夹EMIP\Web\appadmin\upload赋相应的权限`

### 新闻轮播配置

<img src="bpmadpp/image/8.png"  width = "100%" height = "800"   alt ="新闻轮播" align=center >

`参数说明`

|  字段   |    说明  |
|  ----  |   ----  |
| 是否开启新闻轮播  | 关闭后webapp将不显示 |
| 自动轮播间隔     |  切换图片的间隔时长 |
| 动画时长     |切换图片的时长 |
| 是否开启循环播放   | 开启后轮播到最后将从第一张开始 |
| 是否显示指示器 | 轮播下面显示指示器 |
| 是否为纵向滚动  | 默认为横向滚动，开始后将纵向滚动|
| 数据源类型  | |
| 静态数据源  | 可以上传图片 |
| 动态数据源  | 添加接口地址，动态数据源返回示例:{ success:true,//必须 list:{ url:''//必须 } } |

`动态数据源 list数组中的url为图片地址`

### 公告滚动配置

<img src="bpmadpp/image/9.png"  width = "100%" height = "800"  alt ="公告滚动" align=center >

`参数说明`

|  字段   |    说明  |
|  ----  |   ----  |
| 是否开启公告滚动  | 关闭后webapp将不显示 |
| 文本颜色     |  公告的文字颜色 |
| 滚动条背景     |公告背景颜色 |
| 动画延迟时间 (s)   |  |
| 滚动速率 (px/s) |  |
| 数据源类型  | |
| 静态数据源  | 写文字 |
| 动态数据源  | 添加接口地址，动态数据源返回示例:{ success:true,//必须 text:""//必须 } |

### 菜单配置

<img src="bpmadpp/image/10.png" width = "100%" height = "800"  alt ="菜单配置" align=center >

#### 分类

<img src="bpmadpp/image/11.png" width = "100%" height = "800"  alt ="分类" align=center >

`参数说明`

|  字段   | 必填  |  说明  |
|  ----  |  ---- |  ----  |
| 分类所属  | 否 | 菜单属于哪个目录下 |
| 分类名称(中文)  | 是  |  分类的中文名称 |
| 分类名称(英文)   |否 |  分类的英文名称，如不填切换英文时则显示中文名称 |
| 宫格列数   | 是 | 大类分类下菜单每一行显示菜单个数 |
| 间距(PX) | 是 | 菜单之间的间隔 |
| 是否显示边框  | 否 | 不选择则不显示边框 |
| 可见安全组  | 否 | 此类别哪些安全组可见，如不选择则都不可见，安全组来源于BPM安全组，新增和编辑请到BPM修改|
| 排序  | 是| 分类显示的顺序|


#### 菜单

<img src="bpmadpp/image/13.png" width = "100%" height = "800"  alt ="菜单" align=center >

`参数说明`

|  字段   | 必填  |  说明  |
|  ----  |  ---- |  ----  |
| 菜单所属  | 否 | 菜单属于哪个目录下 |
| 菜单名称(中文)  | 是  |  菜单的中文名称 |
| 菜单名称(英文)   |否 |  菜单的英文名称，如不填切换英文时则显示中文名称 |
| 菜单图片   | 是 | 菜单显示的图片，图片必须为PNG且小于1M |
| 类型 | 是 | 1.VUE:vue应用，需开发vue应用地址填写vue路由<br/>2.HTML:html页面，地址填写html地址<br/>3.APP:详细见APP应用配置<br/>4.MENU:二级菜单，可再配置下级菜单 |
| 地址  | 否 | 根据类型不同填写 |
| 角标  | 否 | 菜单右上角可显示数量，@Account参数为当前登录人 |
| 可见安全组  | 否 | 此类别哪些安全组可见，如不选择则都不可见，安全组来源于BPM安全组，新增和编辑请到BPM修改|
| 排序  | 是| 分类显示的顺序|


#### APP应用

<img src="bpmadpp/image/14.png" width = "100%" height = "800"  alt ="APP应用" align=center >

`使用说明`
1.选择表单服务
2.选择字段：显示表单服务中所用到的所有表，但目前只可以选择一张表作为应用列表
<img src="bpmadpp/image/15.png" width = "100%" height = "400"  alt ="选择字段" align=center >

3.字段配置：对选择的字段进行配置，中文名，英文名，是否显示，格式化（可写css样式）
<img src="bpmadpp/image/16.png" width = "100%" height = "400"  alt ="字段配置" align=center >
4.选择事件：查看、新增、编辑、删除、搜索、排序的配置
<img src="bpmadpp/image/17.png" width = "100%" height = "400"  alt ="选择事件" align=center >



## 后台管理源码说明


1.框架:vue+element
<img src="bpmadpp/image/18.png" width = "100%" height = "400"  align=center >

2.目录结构：后续详细介绍


## WEBAPP源码说明

1.框架:vue+vant

<img src="bpmadpp/image/19.png" width = "100%" height = "400"  align=center >

2.目录结构：后续详细介绍