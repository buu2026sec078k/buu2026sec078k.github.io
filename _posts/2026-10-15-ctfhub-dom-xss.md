# DOM反射XSS
**题目来源**: CTFHub
**题型**: Web
**难度**: 简单

## 解题思路
1. 代码审计：查看页面源码，发现页面通过 innerHTML 直接渲染用户可控参数，无任何过滤，存在 DOM 型XSS漏洞。
2. 绕过前端过滤：题目前端过滤了 script 标签，无法直接使用脚本标签，改用 img 标签 onerror 事件执行JS代码。
3. 构造闭合Payload：通过引号与标签闭合，跳出原有代码结构，插入恶意img加载错误执行代码，向外携带Cookie。
4. 盲打Bot触发漏洞：填入Payload生成新URL，将完整链接提交给机器人访问，管理员身份访问页面触发XSS。
5. 获取Flag：Webhook接收Bot回传的Cookie数据，解析参数成功拿到Flag。

## 关键操作
> DOM XSS无需服务器解析、完全前端执行；script被过滤可使用img onerror替代；通过标签与引号闭合实现代码逃逸，利用webhook外带Cookie盲打获取数据。

## Flag
`ctfhub{d389bb40463820bd4051071e}`

## 总结
本题考察DOM型反射XSS，漏洞产生于前端JS代码对用户变量的不安全渲染。掌握了前端关键字过滤绕过、标签闭合逃逸、事件触发执行JS以及XSS盲打外带Cookie的完整利用流程。
