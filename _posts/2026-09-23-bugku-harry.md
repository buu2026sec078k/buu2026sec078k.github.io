---
layout: post
title: Bugku CTF Crypto - harry
---

# Bugku CTF Crypto - harry

## 题目简介
题目给出一串由 `+ - . < > [ ]` 组成的字符，题型为 Brainfuck 代码解密。

## 解题思路
识别密文特征为 Brainfuck 语言代码，使用 Brainfuck 在线解释器运行代码，直接得到 Flag。

## 解题过程
1. 观察题目字符只有 `+ - . < > [ ]`，判断为 Brainfuck 编程语言。
2. 搜索 Brainfuck 在线解释器，复制题目里全部代码粘贴到输入框。
3. 运行解释器，输出得到 Flag。

## 最终Flag
flag{0d86208ac54fbf12}


## 学习总结
Brainfuck 是极简的8指令编程语言，CTF常用来作为密码题。只要密文只包含 `+ - . < > [ ] ,` 这几个符号，就优先考虑Brainfuck，直接使用在线解释器运行获取结果。
