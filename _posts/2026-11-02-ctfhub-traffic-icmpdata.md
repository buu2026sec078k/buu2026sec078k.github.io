# CTFHub - ICMP-Data Writeup
**题目来源**：CTFHub
**题型**：流量分析
**难度**：简单

## 解题思路
1. 载入流量包：使用Wireshark打开附件icmp_data.pcap，里面混杂大量无关SSH流量。
2. 协议过滤：在显示过滤器输入icmp，筛选出全部ICMP数据包；再添加icmp.type == 8只保留Ping请求包。
3. 观察异常：直接搜索ctfhub无法命中，说明flag不是明文存放。点开数据包查看ICMP的Data字段，正常ping包填充数据是固定重复值，本题每个请求包固定偏移位置存在变化的十六进制字符。
4. 提取数据：逐个查看数据包Data部分，取出固定位置的十六进制，转成ASCII字符拼接。也可以用pyshark写脚本自动批量提取。
5. 获取Flag：ctfhub{c87eb99796406ac0b}

## 总结
本题考察Wireshark基础过滤和ICMP协议理解，flag拆成单个字符藏在每个ICMP请求包Data的固定偏移处，掌握“过滤→找异常偏移→提取拼接”的思路就能解决同类隐写流量题。
