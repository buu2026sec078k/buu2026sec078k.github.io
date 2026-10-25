# CTFHub - MIME绕过 Writeup
**题目来源**：CTFHub
**题型**：Web
**难度**：简单

## 解题思路
1. 写木马：编写一句话木马 `<?php eval($_POST['ctfhub']);?>`，连接密码为ctfhub。
2. 抓包改包（MIME绕过核心）：使用Burp Suite拦截上传请求，将请求头里的Content-Type从application/octet-stream修改为image/jpeg，骗过服务器MIME类型校验。
3. 蚁剑连接：拿到上传后的文件URL，填入蚁剑，密码ctfhub，成功连接webshell。
4. 查找flag：在服务器 `/var/www/html/` 目录找到flag文件，读取得到flag。

Flag：ctfhub{5a5d3011ded4646158f67f56}

## 总结
MIME类型校验只校验请求头Content-Type，仅前端+请求头校验，没有校验文件真实内容。抓包修改请求头即可绕过上传php一句话木马。
