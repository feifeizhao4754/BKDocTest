## 用户
蓝鲸体系内的用户信息统一由**蓝鲸用户管理**服务提供，蓝鲸权限中心的用户数据也是从**蓝鲸用户管理**拉取，蓝鲸权限中心只管理用户的权限数据。
用户的权限来源可以有多种方式：

1. **被管理员直接授予的权限**：管理员通过权限模板直接给用户授权。
![](../../assets/画板复制4.jpg)

2. **继承组织的权限**：用户属于某个组织，管理员给该组织添加权限后，组织内的所有用户自动继承该组织的权限。

![](../../assets/画板复制5.jpg)

3. **直接继承用户组的权限**：将用户直接添加到用户组，管理员给该用户组添加权限后，用户组内的所有用户自动继承该用户组的权限。

![](../../assets/画板复制6.jpg)

4. **继承组织所在用户组的权限**：用户属于某个组织，将该组织添加到用户组，管理员给该用户组添加权限后，组织内的所有用户自动继承该用户组的权限（组织本身不会继承用户组的权限）。

![](../../assets/画板复制7.jpg)

```

注：当同一条权限同时来自多个来源方式时，权限中心会同时保留多份数据源，权限有效期使用多份来源中最长时间的那个，
当这份权限数据移除后，自动使用次长的权限数据，依次类推直到所有权限来源数据被移除，该用户将彻底失去这条权限。
```

####同步新增用户/组织
管理员在用户管理新增加用户/组织，需要在组织架构手动同步一次，否则需要等**24小时**后新用户/组织才能在权限中心里使用。
1. 在**权限管理**菜单下，单击**组织架构**；
2. 在右侧展示的**组织架构**页面，点击搜索框右侧的按钮，点击**同步组织**，提示同步组织成功后，重新刷新页面即可在权限中心使用新用户/组织。

####直接给用户授权
在**权限管理**菜单下，单击**权限模板**，找到需要授权给用户的权限模板，单击**授权**，或者同时勾选多个权限模板，然后单击**批量授权**，然后**关联资源实例**、通过**授权对象**选择需要授权的用户，选择**授权期限**，填写授权**备注**信息，单击**提交**后权限将直接授予用户。
####删除用户权限
在**权限管理**菜单下，单击**组织架构**，单击具体需要管理的用户，可以针对用户进行权限移除和用户组退出。
    - 移除权限：单击**权限**，勾选需要批量移除的权限，单击**批量移除**，可将权限移除，这里移除会同时移除权限所有来源数据。
    - 退出用户组：单击**加入的组**，找到**直接加入的用户组**，在列表中找到需要退出的组名，单击**退出该组**，退出后，该用户直接继承的组权限将失效（用户组继承**组织**和**继承组织所在用户组**的权限无法通过退出用户组的方式直接取消继承）。
