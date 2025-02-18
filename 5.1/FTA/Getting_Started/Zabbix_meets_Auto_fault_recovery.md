### 2.3.1 当 Zabbix 遇见故障自愈

Zabbix 用户的福音来了，通过对接蓝鲸智云的故障自愈，实现故障的无人值守。
![](media/15060385121293.jpg)

对于 Zabbix 用户，故障自愈可以实现哪些功能呢?

## 1."告警风暴"到此为止

"告警风暴"是 Zabbix 用户心中的痛。

一旦遇到网络波动、机房停电等情况告警根本停不下来，打爆你的手机。

有人甚至将 Zabbix 告警插入 redis 自己编写代码设定规则，来实现告警收敛。

如今，有了故障自愈，你不需要这样。

故障自愈拥有强大、可自助配置的收敛模块，轻松解决 Zabbix 的告警收敛。

![](media/15039926943795/15040067360890.jpg)

### 1.1 网络出现异常时，收敛即是防护
当网络出现波动导致“假的 Ping 告警”产生时，可以在自愈里设定收敛规则，有效防护，而不是直接重启服务器。
![](media/15060131567224.jpg)

### 1.2 相同处理方案的告警，成功后跳过

当进程告警  和 端口告警同时来袭，选择成功后跳过的收敛方式可以防止重复执行处理方案。

当然，自愈的收敛规则还有很多，等待你去配置。

![](media/15060122272210.jpg)


## 2. 故障处理作业自由定制
故障自愈的处理套餐当前在社区版 V3.1 中有“分析 CPU 和内存使用率”、“磁盘清理”的快捷套餐，也有自己编写脚本的`作业平台`，以及最近一周即将推出的 HTTP 回调套餐（直接对接企业内部运维网关）

### 2.1 分析 CPU 和内存使用率
![CPU使用率——自愈](media/CPU%E4%BD%BF%E7%94%A8%E7%8E%87%E2%80%94%E2%80%94%E8%87%AA%E6%84%88.png)

### 2.2 磁盘清理套餐
![](media/15060398388668.jpg)


### 2.3 万能的作业平台
在作业平台里可以发挥你技高一筹的脚本编写能力，支持 Shell、bat、Perl、Python、Powershell.
![](media/15060120685247.jpg)

### 2.4  对接企业内部的运维网关
比如 PING 不可达后，你需要重启服务器
![](media/15060116985910.jpg)


## 3.与 CMDB 联动，精准处理告警
故障自愈在清洗告警时，会从蓝鲸的配置平台（CMDB）中拉取告警 IP 的配置信息，与自愈方案做匹配。

实现不同模块，不同集群的告警精细化处理。
![](media/15060141816012.jpg)

## 4. 故障自愈集成 Zabbix 的方法

### 4.1 运行初始化脚本
![](media/15060403024197.jpg)

就这么简单！

以下是原理，剖析给大家听听。

## 4.2 Zabbix 是如何发送消息给故障自愈的
执行了 4.1 中的初始化脚本后，自愈会自动创建如下操作。

自动创建名为 FTA_Act 的 Action
![](media/15060403626099.jpg)

FTA_Act 这个 Action 的 Operation 会通知 FTA_Mgr 用户，FTA_Mgr 的通知媒介就是调用/usr/lib/zabbix/alertscripts/zabbix_fta_alarm.py 
![](media/15060409949390.jpg)

告警产生后在 Action log 中可以看到发给 FTA_Act 的 Message
![](media/15060403778865.jpg)

### 4.3 自愈集成 Zabbix 告警注意事项
自愈处理告警是把 {HOST.IP}作为故障主机 IP，{ITEM.KEY}作为告警类型，请确保 {HOST.IP}在配置平台中注册，同时 ITEM.KEY 能被你接入的告警类型所匹配。

上图的 ITEM.KEY 为 system.swap.size[,pfree]被下图的 Swap 使用量(system.swap.*)的规则所匹配。
![](media/15060407047244.jpg)

![](media/15060408193567.jpg)

在/tmp/zabbix_fta_alarm.log 中可以查看到日志信息
![](media/15060409189531.jpg)

## 5.故障自愈，不只是集成 Zabbix
![](media/15060122755230.jpg)


作为运维的你，还在等什么？释放双手的时候到了！

