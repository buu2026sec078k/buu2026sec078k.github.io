# 整数型注入
**题目来源**: CTFHub
**题型**: Web
**难度**: 简单

## 解题思路
1. 判断注入点：传入参数 `id=1 and 1=1` 页面正常回显数据，传入 `id=1 and 1=2` 页面无数据，证明存在整数型SQL注入漏洞。
2. 探测查询列数：使用 `order by` 排序猜列数，`id=2 order by 2` 页面正常，`id=2 order by 3` 页面报错，判断当前查询语句共 2 列。
3. 确定回显位置：构造报错查询 `id=-1 union select 1,2--+`，页面成功输出可控数字，确认两列均可回显。
4. 查询当前库名：在回显位填入 `database()` 函数，成功获取当前网站数据库名称。
5. 查询数据表名：利用 `information_schema.tables` 数据表，使用 `group_concat(table_name)` 查询所有表，爆出 `flag`、`news` 两张数据表。
6. 查询最终Flag：针对性查询 flag 数据表内容，成功读取数据，拿到题目 Flag。

## 关键操作
> 通过布尔判断确认整数型注入，order by 测列数、union select 找回显位，逐级爆库、爆表、爆字段，最终读取Flag。

## Flag
`ctfhub{fcff778d619078eff11b4696}`

## 总结
本题考察最基础的整数型SQL注入，属于Web注入入门题型。通过布尔真假判断确认注入点，结合order by、union联合查询逐级枚举库、表、数据，是SQL注入最核心、最通用的解题流程。
