# XSS漏洞基础

## 关键

寻找参数未过滤的输出函数

常见输出函数：

![常见输出函数](<../.gitbook/assets/image (6).png>)

## 分类

### 反射性XSS

攻击者事先准备好xss

### 存储型XSS

通过对网页注入可执行代码且成功地被浏览器执行，达到攻击的目的，一般是注入一段javascript脚本。

### DOM型XSS（不常见）

可以通过DOM动态的检查和修改页面内容，不依赖提交数据到服务器端

## 原理

### 反射型xss

比较容易扫描直接发现

## Xray使用

1.启动powershell

2.进入根目录 d:

3.cd到文件路径

4.命令格式 .\xray -h

5.扫描漏洞指令 .\xray webscan --basic-crawle url（http://testphp.vulnweb.com/）

```
[Vuln: xss]   //vuln表示是什么漏洞（xss漏洞）
Target "http://testphp.vulnweb.com/guestbook.php" //漏洞地址
VulnType "reflected/default" 
Payload "<script>alert(1)<script>" //漏洞指令
Position "body" 
ParamKey "text" 
ParamValue "vjjsddkkvvphlooblgvo"
```

## 目的

![](<../.gitbook/assets/image (8).png>)

## 常用xss攻击代码

![](<../.gitbook/assets/image (9).png>)
