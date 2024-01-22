# BC中国开发规范

虽然这些细节是小事，不会有体验或者性能上的优化，但是却体现了一个 coder 和团队的专业程度，我们强烈建议你在写代码之前能花上一些时间把相关的规范文档通读一遍。

## 必要说明

- 必须（Must） - 只能这样子做，请无条件遵循，没有别的选项。
> MUST This word, or the terms “REQUIRED” or “SHALL”, mean that the
definition is an absolute requirement of the specification.

- 绝不（Must Not）- 严令禁止，在任何情况下都不能这样做。
> MUST NOT This phrase, or the phrase “SHALL NOT”, mean that the
definition is an absolute prohibition of the specification.

- 应该（Should） - 强烈建议这样做，但是不强求。
> SHOULD This word, or the adjective “RECOMMENDED”, mean that there
may exist valid reasons in particular circumstances to ignore a
particular item, but the full implications must be understood and
carefully weighed before choosing a different course.

- 不应该（Should Not） - 强烈建议不这样做，但是不强求。
> SHOULD NOT This phrase, or the phrase “NOT RECOMMENDED” mean that
there may exist valid reasons in particular circumstances when the
particular behavior is acceptable or even useful, but the full
implications should be understood and the case carefully weighed
before implementing any behavior described with this label.

- 可以（May） - 选择性高一点。
> MAY   This word, or the adjective "OPTIONAL", mean that an item is
   truly optional.  One vendor may choose to include the item because a
   particular marketplace requires it or because the vendor feels that
   it enhances the product while another vendor may omit the same item.
   An implementation which does not include a particular option MUST be
   prepared to interoperate with another implementation which does
   include the option, though perhaps with reduced functionality. In the
   same vein an implementation which does include a particular option
   MUST be prepared to interoperate with another implementation which
   does not include the option (except, of course, for the feature the
   option provides.)

[Reference](https://www.ietf.org/rfc/rfc2119.txt)




# Environment Management And Contorl Policies 环境管理和管控政策

## 开发人员禁止访问生产数据

生产环境包含关键数据。如果访问生产环境，不仅会涉及数据泄露，还涉及到进行了未经授权的操作。

## 部署角色隔离

只允许DM可以批准生产环境的发布。

## 隐藏生产环境密钥

生产管理访问权限，只能严格授予给专用的用户组。Azure DevOps Release Pipeline工具可以隐藏所有的生产密钥。
