# 回转十三位
**题目来源**：CTFHub
**题型**：Crypto
**难度**：简单

## 解题思路
1. 第一步：下载题目附件，得到一串疑似 Base64 编码的密文字符串 `EzkuM0yGAzA2n3WbEaOJEHuOFmuOpN==`。
2. 第二步：根据题目名称“回转十三位”，推断出该密文使用了 ROT13（凯撒密码的变种，偏移量为13）加密。由于 ROT13 是自身逆运算，直接对密文进行 ROT13 解码。
3. 第三步：将 ROT13 解码后的字符串再进行 Base64 解码，得到明文 `FlagIS6cvkrhFpVEHAK8Ap`。分析出题人意图，`FlagIS` 为干扰提示语，提取核心字符串，加上 `flag{}` 格式提交。

## 关键操作
> 这里写用到的工具、payload、命令、截图说明

**使用工具**：CyberChef（网页在线工具，手机端亦可操作）

**操作流程**：
1. 在 CyberChef 的 Input 框输入密文：`EzkuM0yGAzA2n3WbEaOJEHuOFmuOpN==`
2. 在左侧 Operations 栏搜索并添加 `ROT13` 操作（注意：只勾选 `Rotate lower case chars` 和 `Rotate upper case chars`，**不要勾选** `Rotate numbers`，否则会导致后续解码失败）。
3. 搜索并添加 `From Base64` 操作，确保它在 `ROT13` 的右侧（即先 ROT13 后 Base64）。
4. 观察 Output 框，成功得出明文：`FlagIS6cvkrhFpVEHAK8Ap`。

**避坑指南**：
- **手机端文本渲染Bug**：使用手机自带或网盘自带的普通文本阅读器打开附件时，可能会出现字符混淆（例如把数字 `0` 显示成字母 `O`，字母 `l` 显示成 `I`），建议使用 HTML 查看器或专业的代码编辑器查看密文。
- **出题人套路**：明文中的 `FlagIS` 实际上是英文短语“Flag is”，真正的 Flag 内容从后面的数字 `6` 开始。
- **平台环境问题**：CTFHub 为动态环境，如果在解题页面停留时间过长，后台密文可能会刷新，导致提交旧答案一直报错，需销毁环境后重新提取。

## Flag
`flag{6cvkrhFpVEHAK8Ap}`

## 总结
本题考察的知识点：古典密码（ROT13）、Base64 多层编码的混合解密、CyberChef 工具的使用。

**收获**：
1. 掌握了“编码顺序与解码顺序相反”的原则（加密：明文 -> ROT13 -> Base64；解密：Base64 -> ROT13 -> 明文）。
2. 积累了 CTF 实战中的“避坑”经验，明白了在处理长字符串时，要警惕不同软件字库带来的视觉误差（0/O, l/I）。
3. 认识到在 CTF 比赛中，不能盲目相信全量输出结果，要结合题目提示（如 `flag{xxx}` 格式）对明文进行合理的逻辑提取和过滤。
