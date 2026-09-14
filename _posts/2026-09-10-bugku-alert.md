---
layout: "Bugku-alert write up"
date: 2026-09-10
---

## 题目描述
打开页面会不断弹出alert弹窗，无法正常浏览页面。

## 解题思路
在浏览器控制台重写alert函数，屏蔽弹窗，页面显示flag。
## 操作步骤
1. 访问题目链接，页面无限弹出alert窗口。
2. F12打开开发者工具，切换到Console控制台。
3. 输入 `alert=function(){};` 回车执行，弹窗被关闭。
4.  页面展示flag。


##flag
flag{14de4a05073584db45a8cd98582933b6}
