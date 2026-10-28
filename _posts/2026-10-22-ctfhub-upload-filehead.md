# CTFHub - 文件头检查 Writeup
**题目来源**：CTFHub
**题型**：Web
**难度**：简单

## 解题思路
1. 构造木马：文件开头添加GIF89a图片文件头，绕过服务器文件头检测，后面接上一句话木马。
2. Burp抓包修改：拦截上传数据包，修改Content-Type为image/gif，补充空行保证文件内容正常上传。
3. 蚁剑连接：访问上传后的shell.php，用蚁剑连接服务器，进入 `/var/www/html/` 目录。
4. 找到目标flag文件，读取拿到flag。

Flag：ctfhub{96fe161c1dbaaff376dae528}

## 总结
服务端读取文件头部字节校验图片类型，在木马文件最前面加上GIF文件头标识GIF89a，即可绕过文件头检测完成webshell上传。
