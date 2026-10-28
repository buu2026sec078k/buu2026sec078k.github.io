# CTFHub - 前端验证 Writeup
**题目来源**：CTFHub
**题型**：Web
**难度**：简单

## 解题思路
1. 将一句话木马保存为shell.jpg，利用Burp抓包，绕过前端JS校验。
2. Burp Suite拦截数据包，修改文件后缀为shell.php，绕过服务端校验。
3. 准备蚁剑，填写木马URL和连接密码，成功连上Webshell。
4. 在服务器目录找到flag文件，打开读取flag。

Flag：ctfhub{3ec5450fb6d4a448bc61b80f}

## 总结
前端JS校验仅在浏览器本地生效，抓包拦截修改数据包可以完全绕过前端限制，服务端才是安全校验的关键点。
