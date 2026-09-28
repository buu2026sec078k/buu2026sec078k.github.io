# Cookie
**题目来源**: CTFHub
**题型**: Web
**难度**: 简单

## 解题思路
1. 访问题目页面，根据题目提示得知需要查看、修改或读取Cookie信息。
2. 使用浏览器抓包工具查看请求包与响应包中的Cookie字段。
3. 在Cookie信息中找到隐藏的flag，提取并提交。

## 关键操作
> 通过抓包查看HTTP数据包中的 Cookie 内容，从 Cookie 字段中读取隐藏 flag。

## Flag
`ctfhub{29a24bdfe9eafa291ab1becb}`

## 总结
本题考察 Web 基础 Cookie 知识点，掌握 HTTP 数据包中 Cookie 的查看与信息搜集，是 Web 入门常见基础题型。
