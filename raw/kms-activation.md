title: KMS激活
category: 教程
time: 1484793898048

---

###KMS服务软件
[vlmcsd - Github.com](https://github.com/Wind4/vlmcsd)

###测试地址
[mcs.lotlab.org](http://mcs.lotlab.org)  
请勿滥用

###Windows 激活命令

```
CD "%SystemRoot%\SYSTEM32"
CSCRIPT /NOLOGO SLMGR.VBS /SKMS mcs.lotlab.org
CSCRIPT /NOLOGO SLMGR.VBS /ATO
CSCRIPT /NOLOGO SLMGR.VBS /XPR
```

###Office/Project/Visio 2013(2010换下安装路径) 激活命令

```
32位：CD "%ProgramFiles(x86)%\MICROSOFT OFFICE\OFFICE15"
64位：CD "%ProgramFiles%\MICROSOFT OFFICE\OFFICE15"
CSCRIPT OSPP.VBS /SETHST:mcs.lotlab.org
CSCRIPT OSPP.VBS /ACT
CSCRIPT OSPP.VBS /DSTATUS
```

