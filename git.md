# Git 分支和源码管理

## 分支管理

### 分支命名

1. master：主分支，永远是可用的、稳定的、可直接发布的版本，由 develop 以及 hotfix 分支合并，不能直接在该分支上开发。
2. develop：开发主分支，代码永远是最新，所有 feature 分支以这个分支来创建自己的开发分支，该分支只做只合并操作，不能直接在该分支上开发。
3. feature/xxx：功能开发分支，在 develop 上创建分支，以自己开发功能模块命名，功能测试正常后合并到 develop 分支。
4. release：预发布分支，在合并好 feature 分支的 develop 分支上创建，主要是用来提测的分支，修改好 bug 并确定稳定之后合并到 develop 和 master 分支，然后发布 master 分支。
5. hotfix/xxx：紧急 bug 修改分支，项目上线之后可以会遇到一些环境问题需要紧急修复，在对应版本的 release 分支上创建，流程跟 release 分支相似，修复完成后合并 release 分支，根据情况判断需不需要再合并到 develop 和 master 分支。

### 注意事项

- 一个分支尽量开发一个功能模块，不要多个功能模块在一个分支上开发。
- 开发过程中，如果组员 A 开发的功能依赖组员 B 正在开发的功能，可以待组员 B 开发好相关功能之后，组员 A 直接 pull 组员 B 的分支下来开发，不需要先将组员 B 的分支 merge 到 develop 分支。
- feature 分支在申请合并之前，一定要是先 pull 一下 develop 主分支下来，看一下有没有冲突，如果有就先解决冲突后再申请合并。

### 分支实践

feature/add-subject

(如果需要可以添加一个链接到 issue 地址或者其它文档)

## Git Commit Message(GCM)

### 好的 GCM 能帮到我们什么

1. 加快审查进程,
2. 帮助项目未来的维护者,说五年后的未来,找出为什么特定的更改的代码或增加了特定的功能——他们为什么(之一)的主要手段,
3. 开发团队的成员之间的沟通
4. 帮助我们编写良好的版本发布日志

### GCM 的模板格式

1. 每个提交消息必须由一个头和一个可选的主体组成。
2. 头部有一个特殊的格式，包括一个类型、一个 PB(US)标记和一个主题。
3. 注意字母大小写和标点符号——PB(US)标记应该在圆括号内，后面跟着冒号。

```csharp
// 整个提交消息中最重要的部分是主题。
<type>(<PB_tag>): <subject>
<blank_line>
[optional body]
```

提交类型

1. feat: 新功能
2. fix: bug 修复
3. docs: 文档跟新
4. refactor:代码重构
5. chore: 对构建过程或辅助工具和库的更改
6. test：测试代码相关
7. style: 仅仅修改了空格、格式缩进等等，不改变代码逻辑
8. merge: 解决冲突
9. revert：回滚到上一个版本
10. sync：同步主线或分支的 Bug
11. perf：优化相关，比如提升性能、体验

### GCM 实践

```csharp
feat(#1016): add ValidateAddress method to ExamDateValidator
fix(#734): add missing `track by`
(如果需要可以添加一个链接到issue地址或者其它文档)
```

```csharp
//携带描述
feat(#9912): add cache for user permissions
<blank_line>
Without permissions cache every call to api caused request to
security system to obtain user permissions. Currently permissions are cached
for multiple request for 10 minutes.
```
