---
title: BPM版本库
date: 2020-04-03 14:31:56
summary: bpm 版本及更新说明
categories: bpm
tags:
- BPM
---

### 6.70b
-  [SetupDisk_R6.70b](http://qn.lxyzy.top/SetupDisk__R6.70b.rar)
<details>
<summary>更新说明</summary>

 1. "数据库若设置TaskID为主键，表单提交提示TaskID不能为空（紧急）
由Oracle自增列判断优化引起"
 2. "彻底修正Asp.net FormsAuthentication Cookie为Lax的问题
虽然以前将SameSite强制设置为None起到一定作用，但现在发现None也是有问题的
    1.chrome 64位版本80.0.3987.149 http请求不接受SameSite=None 的cookie（只能在https中使用），当http场合发送这样的cookie时，浏览器认为cookie错误，结果：在某些电脑上，BPM网站登录时输入正确账密后，登录页面不跳转
    2.Response.Redirect时FormsAuthentication cookie为None或Lax有时不会传递到目标页面（Lax总是不传，None看浏览器版本），表现为：移动端打开PC表单某些情况下不会直接打开表单，而是跳转到登录页面的问题
    目前采用解决办法：SameSite既不是Lax也不是None而是空
    老版本可拷贝WEB\App_Code\YZSoft\Helper\YZAuthHelper.cs的2个方法：
    public static void SetAuthCookie(string account)
    public static void SetAuthCookie(string account, string token)"



</details>


### 6.70a
-  [SetupDisk_R6.70a](http://qn.lxyzy.top/SetupDisk__R6.70a.rar)
<details>
<summary>更新说明</summary>

 1. "服务器端.net环境需4.5以上（原来是4.0），客户端还是4.0
 2. 服务器和WEB Newtonsoft.Json都升级为12.0.01
 2. 升级原因：系统使用的部分库需要.net4.5"
 2. ESB2.0推出，除数据源外还支持输出，原ESB建的内容仍可用，也可修改，但取消新增功能
 2. 推出队列，支持异步输出
 2. 运维\任务移交模块，切换用户后，任务列表不会自动更新
 2. 报表设计器设计的报表没有导出Grid的按钮


</details>



### 6.00f
-  [SetupDisk_R6.00f](http://qn.lxyzy.top/SetupDisk_R6.00f.rar)
<details>
<summary>更新说明</summary>

 1. 流程运维 ，任务移交时选择 在途申请的任务移交会出错
 2. 应用客制模块，记录授权，点击报错
 2.  集成管理，添加BPM服务器，示例数据端口为1590,建议1580
 2. 报表，明细表没有记录勾选的字段。下次设置需重新勾选
 2. 下拉列表通过别的字段过滤 ，然后赋值给金额。移动端输入数据没有过滤出结果时，金额字段为上一次过滤的结果，应该为空过滤增加!=选项（涉及表单数据源和开窗查询）
 2. "支持数据库连接信息存储到外部系统，在Server.config,database节，增加ConnectionStringProvider配置项，如下：
 <ConnectionStringProvider>MyConnectionProvider.Provider,MyConnectionProvider</ConnectionStringProvider>
 新建库：MyConnectionProvider.dll，添加类：MyConnectionProvider.Provider
 实现接口：
 BPM.Server.Interface.IConnectionStringProvider，通过GetConnectionString方法返回连接字符串"

 2. 6.00f主数据库支持Oracle
 2. 在阅示节点，处理人再次启用阅示，选择人员，提交后报错
 2. ExtServer对应的.svr文件中连接信息，用户名、密码加密（对于已存在的ExtServer，重新保存后会自动加密）
 2. 访问控制模块，增加资源权限管理，可授权资源管理员和授权管理员，资源管理员可在后台模块编辑资源，授权管理员可在运维模块修改资源权限
 2. 一人多岗，增加设置缺省职位，管理员在组织管理中修改，个人在岗位地图中修改，在起流程时，缺省职位显示在最前面

</details>


### 4.0~5.0

