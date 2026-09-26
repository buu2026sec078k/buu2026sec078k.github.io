---
layout: post
title: Bugku CTF - linux
---

# Bugku CTF - linux

## 题目简介
Bugku Linux基础题型，考察Linux基础命令操作，在服务器环境下查找指定文件，读取文件内容获取key。

## 解题思路
连接Linux服务器，使用基础文件查找命令定位目标文件，cat读取文件内容得到key。

## 解题过程
1. 远程连接Linux服务器。
2. 使用ls、find等基础Linux命令浏览目录，查找存放key的目标文件。
3. 使用cat命令读取目标文件，拿到key。

## Key
```
key{feb81d3834e2423c9903f4755464060b}
```

## 总结
入门Linux实操题，熟悉基础目录浏览、文件查找与文件读取命令即可完成，适合练习Linux基础操作。
