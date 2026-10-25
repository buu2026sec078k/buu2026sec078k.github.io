# CTFHub - 文件包含 Writeup
**题目来源**：CTFHub
**题型**：Web
**难度**：简单

## 解题思路
1. 源码审计：页面给出PHP源码，通过GET方式接收file参数并文件包含，代码过滤了flag关键字，直接读取flag会被拦截，页面提示存在shell.txt一句话木马。
2. 利用思路：规避flag关键词过滤，通过包含本地shell.txt木马文件，利用木马的命令执行功能读取flag。
3. 构造Payload：`?file=shell.txt&ctfhub=system('cat /flag');`
4. 访问链接执行系统命令，成功获取flag。

Flag：ctfhub{2f346c69093b44270e9531a7}

## 总结
本题为基础的本地文件包含+命令执行题型。题目直接过滤flag关键字，无法直接读取flag文件，通过加载题目自带的木马文件，间接执行系统命令，成功绕过过滤获取flag。
