# CTFHub - 伪协议读取文件 Writeup
**题目来源**：CTFHub
**题型**：Web
**难度**：简单

## 解题思路
1. 找到漏洞点：页面url参数可控，存在文件包含漏洞，没有做过滤，可以使用file://伪协议读取本地文件。
2. 构造Payload：`?url=file:///var/www/html/flag.php`，拼接到题目url后缀访问。
3. 获取Flag：访问后页面没有直接显示flag，右键查看网页源代码，即可读出flag。

Flag：ctfhub{638bfbd5e9e96e35b132d92d}

## 总结
本题是基础本地文件包含，利用file://伪协议读取服务器上的php文件；php文件会被服务端解析，所以必须查看网页源代码才能拿到里面隐藏的flag。
