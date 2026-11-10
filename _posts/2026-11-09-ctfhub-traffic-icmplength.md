# CTFHub - ICMP-Length Writeup
**来源**：CTFHub
**题型**：流量分析
**难度**：简单

## 解题思路
1. Wireshark打开icmp_len.pcap，流量为ICMP ping包，包长度异常。
2. 使用过滤语句 `icmp && icmp.type == 8`，只保留请求包。
3. Length减去42得到ASCII字符，拼接即为flag。

## 解题步骤
1. 在过滤器输入 `icmp && icmp.type == 8` 筛选ping请求包。
2. 每个数据包的Length减42，转成字符，拼接得到flag。

## Flag
`ctfhub{acb659f023}`

## 总结
考察ICMP载荷长度隐写，利用Wireshark过滤数据包，计算长度还原flag。
