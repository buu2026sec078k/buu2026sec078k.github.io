# 存储型XSS
**题目来源**: CTFHub
**题型**: Web
**难度**: 简单

## 解题思路
1. 判断漏洞类型：页面存在修改昵称输入框与Send URL to Bot机器人访问功能，输入普通文本后内容会持久展示在页面，确认存在存储型XSS漏洞。
2. 构造攻击Payload：flag存放在管理员Bot的Cookie中，使用Webhook.site获取临时接收URL，构造fetch脚本Payload用来窃取Cookie并发送到接收地址。
3. 植入恶意代码：将XSS Payload填入Change name昵称输入框，回车提交，恶意代码保存到后端数据库。
4. 触发Bot访问：将靶场首页URL填入Send URL to Bot输入框提交，让机器人访问页面执行植入的XSS脚本。
5. 获取Flag：在Webhook接收页面查看Bot发来的请求，从query参数里面拿到包含flag的Cookie。

## 关键操作
> 存储型XSS恶意代码永久保存在服务器；使用webhook接收盲打返回的数据；提交payload和bot链接时需要按回车提交。如果script标签被过滤，可以替换为img标签的onerror版本payload。

## Flag
`ctfhub{332a3c76efae984aaae7d74a}`

## 总结
本题考察存储型XSS盲打，存储型XSS与反射型XSS不同，输入内容持久保存在服务端。解题核心就是利用bot访问页面执行恶意脚本，窃取bot的Cookie拿到flag，是XSS方向经典基础题型。
