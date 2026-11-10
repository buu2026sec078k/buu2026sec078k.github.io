# CTFHub - SQL注入 - 报错注入 WriteUp

## 一、题目信息
- 平台：CTFHub
- 技能树：Web - SQL注入
- 题目名称：报错注入
- 分类：Web
- 考点：报错注入、floor(rand())+group by、updatexml截断、正则提取数据

## 二、原理与解题思路
页面直接输出SQL报错信息，可以把查询内容嵌入报错信息带出。
updatexml存在32字符截断限制，本题使用`floor(rand(0)*2)`搭配group by，制造主键冲突报错，带出查询结果，不受32字符限制。使用正则提取报错里的flag。

## 三、解题过程
1. 注入测试，页面返回数据库报错，确定报错注入
2. 使用floor报错payload，构造查询语句
3. Python请求页面，正则匹配提取报错中的flag
4. 注意修改payload闭合符号，适配题目

## 四、Flag
`ctfhub{af2b6964c68f7c040b03832e}`

## 五、总结
报错注入最简单直接，数据直接在报错中返回；updatexml有长度限制，长flag优先floor报错。需要留意单引号/双引号/数字型的闭合。
