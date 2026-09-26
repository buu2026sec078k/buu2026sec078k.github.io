---
layout: post
title: Bugku CTF - source
---

# Bugku CTF - source

## 题目简介
Bugku Web入门题，考点为.git源码泄露，通过获取泄露的.git目录，恢复git提交历史，从中提取flag。

## 解题思路
页面源码无有效信息，存在.git目录泄露。下载.git目录，利用git reflog查看提交历史，回退到对应版本拿到flag。

## 解题过程
1. 查看网页源代码，没有有用信息，页面中的/flag.txt为干扰项。
2. 使用Kali Linux的dirsearch工具扫描目录，发现存在/.git/和/flag.txt路径。
3. 访问/flag.txt无法得到flag，转向/.git/目录，查阅资料得知logs/HEAD存在提交记录线索。
4. 使用wget下载整个.git目录到本地。
5. 执行`git reflog`查看git提交历史，在版本40c6d51中找到flag。

## Flag
```
flag{git_is_good_distributed_version_control_system}
```

## 总结
本题考察.git源码泄露漏洞。当网站存在.git目录未禁止访问时，可以下载仓库信息，通过git命令恢复历史提交，获取曾经存在的源码与敏感信息。
