# 反射型XSS
**题目来源**: CTFHub
**题型**: Web
**难度**: 简单

## 解题思路
1. 漏洞探测：在页面 name 参数输入 `<script>alert(1)</script>`，成功弹窗，确认存在反射型XSS漏洞。
2. 构造Payload：flag保存在Bot的Cookie中，使用 Webhook.site 搭建接收端，构造脚本窃取Cookie并外带数据。
3. 触发Bot执行：将包含恶意Payload的完整URL提交给机器人访问。
4. 接收数据：Bot访问页面自动执行XSS脚本，将Cookie回传到Webhook接收地址。
5. 提取Flag：在请求参数中成功获取题目Flag。

## 关键操作
> 反射型XSS数据不存入服务器，仅即时渲染触发；利用webhook盲打获取bot cookie，特殊字符需要URL编码避免拦截。

## Flag
`ctfhub{3f118cf8d3c7a6f6cf51d2a3}`

## 总结
本题考察反射型XSS漏洞利用。区别于存储型XSS，漏洞仅单次触发、无持久化存储。通过构造外带脚本盲打Bot，窃取Cookie获取Flag，是Web XSS基础经典题型。
