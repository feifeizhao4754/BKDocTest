### 业务配置 {#deploy}

业务配置是当前业务下的公共配置，主要是业务执行者设置，业务执行者只能被设置为使用过标准运维的业务运维，可以为空。当设置了执行者时，业务非运维人员和职能化人员执行任务时会以业务执行者身份执行任务，调用 ESB；运维人员执行任务时，依然以本人身份执行任务。当业务执行者为空时，业务非运维人员和职能化人员执行任务时会以任一使用过标准运维的业务运维身份执行任务。

![](../assets/业务配置.png)
