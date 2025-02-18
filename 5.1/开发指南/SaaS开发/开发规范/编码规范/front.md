## 前端开发规范{#front}

### 说明

1. 蓝鲸开发规范主要包括应用开发的代码，用户设计体验，安全和性能等的规范和建议
2. 在以下章节中，将用 `【必须】` 标签来标记开发过程中必须遵守的规范，其他均为建议

### 必须掌握的知识点


| 知识点 | 基本要求 | 参考章节 |
| ------ | ------ | ------ |
|  JavaScript 编码规范  | 遵循 [JavaScript Standard Style](https://github.com/standard/standard/blob/master/docs/README-zhcn.md) 编码风格规范，以及学会使用 eslint 对代码进行静态检查 |  [第一章 1](./front1.md) |
|  代码提交规范  | 提交代码前必须对进行自检，不允许提交调试代码；以及在每次提交时必须提供有效的提交备注 |  [第一章](./front1.md) |
| 静态资源引用 | 不同平台、不同环境之间的静态资源不允许交叉引用；在引用静态资源时增加版本号 |  [第一章](./front1.md) |
| 表单数据校验 | 提交表单前，必须对表单数据进行校验，包括但不限于边界校验、注入校验、合法性校验 | [第二章](./front2.md) |
| 页面性能要求 | 页面必须在**2秒**之内打开 | [第三章](./front3.md) |
