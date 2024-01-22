# Environment Management And Contorl Policies 环境管理和管控政策

## 开发人员禁止访问生产数据

生产环境包含关键数据。如果访问生产环境，不仅会涉及数据泄露，还涉及到进行了未经授权的操作。

## 部署角色隔离

只允许DM可以批准生产环境的发布。

## 隐藏生产环境密钥

生产管理访问权限，只能严格授予给专用的用户组。Azure DevOps Release Pipeline工具可以隐藏所有的生产密钥。
