# 标准运维FAQ

## 标准运维原子能否支持用户接入企业内IT系统

支持，接入方式请参考“[附录3：原子开发](http://docs.bk.tencent.com/product_white_paper/gcloud/term3.html)”。

## 标准运维点击开始执行任务后报错

`taskflow[id=1] get status error: node(nodee37e20…c7fb131) does not exist, may have not by executed`，并且在任务列表中查看任务状态是“未知”，可能是什么原因？

标准运维执行引擎依赖于蓝鲸的RabbitMQ服务和App启动的celery进程，请登录服务器确认服务已启动并正常运行，可以查看App的celery.log日志文件帮助定位问题原因。

## 标准运维能执行任务，但是原子节点报错

`Trackback…TypeError:int() argument must be a string or a number,not ‘NoneType’`，可能是什么原因？

标准运维任务流程的执行状态和原子输入、输出等信息缓存依赖Redis服务，所以首次部署请务必按照“标准运维部署文档”，配置Redis环境变量后重新部署。