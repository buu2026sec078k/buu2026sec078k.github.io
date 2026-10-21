# Cookie注入
**题目来源**: CTFHub
**题型**: Web
**难度**: 简单

## 解题思路
1. 定位注入点：使用Burp Suite抓包，页面没有GET/POST输入框，发现HTTP请求Cookie字段内 `id=1` 参数可控，确定为Cookie型SQL注入。
2. 判断注入类型：使用 `and 1=1`、`and 1=2` 测试，页面响应存在差异，确认是数字型注入。
3. 判断列数：使用 `order by` 语句测试，`order by 2` 页面正常，`order by 3` 页面异常，得出查询一共2列。
4. 确定回显位：构造 `-1 union select 1,2`，将原查询置空，页面成功回显数字，确认存在回显位。
5. 查询表名：通过 `information_schema.tables` 元数据表，查询当前数据库下所有表名，得到随机表 `shwfjtdoum`。
6. 查询列名：通过 `information_schema.columns` 元数据表，查询该表对应的列名，得到随机列 `umzcajugmu`。
7. 获取Flag：联合查询读取该列数据，成功爆出flag：`ctfhub{17831d33a0943f365ed4c0a6}`
