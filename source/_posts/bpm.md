---
title: bpm
date: 2020-04-09 17:47:07
categories: bpm
summary: 记录bpm一些常用方法操作注意等
tags:
 - bpm
---

 1. 隐藏表单上面按钮 
 ```js
   window.frameElement.containerPanel.ownerCt.ownerCt.toolbar.remove(window.frameElement.containerPanel.ownerCt.ownerCt.toolbar.items.items[0])
 ```
 2. 表单事件
 ```js
     agent.on({
        beforePost: function (action, validationGroup, params) {   //开始节点生效   控件验证前事件
                debugger;
                return false;
            },
            Post: function (action, validationGroup, data) {   //开始节点生效   控件验证后事件
                debugger;
                return false;
            },
            beforeSubmit: function (action, validationGroup, params) {   //所有节点生效   控件验证前事件
                debugger;
                return false;
            },
            Submit: function (action, validationGroup, data, params) {   //所有节点生效   控件验证后事件
                debugger;
                return false;
            },
            afterPost: function () { //开始节点生效 提交成功后事件
                alert(12312);
            },
            afterSubmit: function () { //所有节点生效 提交成功后事件
                alert(12312);
            },
        });
 ```

 3. 表单加载完后执行

 ```js
  OnAfterLoad = function () {
 ```


 4.提交时选择下一步审批人

 ```js
  agent.on({
            beforeSubmit: function (a, b, c, e, f, g) {

                if (b == "提交") {
                    if (this.validator.submitValidate("")) {
                        if (agent.tryGetChechedEle(document.getElementById("XTextBox2")).getValue() == "") {
                            Ext.create('YZSoft.bpm.src.dialogs.SelUsersDlg', {
                                autoShow: true,
                                fn: function (users) {
                                    var accounts = "";
                                    for (var i = 0; i < users.length; i++) {
                                        accounts += users[i].Account + ",";
                                    }
                                    agent.tryGetChechedEle(document.getElementById("XTextBox2")).setValue(accounts);
                                    var g = window.frameElement.containerPanel;
                                    var btns = g.ownerCt.ownerCt.optButtons;

                                    var link = btns[15].link;
                                    g.ownerCt.ownerCt.post(link);
                                }
                            })
                            return false;
                        } else {
                            return true;
                        }
                    }
                }
              
            }
        });
 ```

 5.审批意见赋值
 ```js
        agent.on({
                Submit: function (action, validationGroup, data, params) {
                    params.Header.Comment = "aa"
                }
            });
 ```
 6.文本框取值赋值
 ```js
 agent.tryGetChechedEle(document.getElementById("id")).getValue();
 agent.tryGetChechedEle(document.getElementById("id")).setValue("test");
 ```
