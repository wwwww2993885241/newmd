# Securtiy 安全

## Secure Code Review 代码安全审查

在代码审查（Code Review）方面，应该依据 [OWASP Secure Code Review](https://owasp.org/www-pdf-archive/OWASP_Code_Review_Guide_v2.pdf) 的指导。

依据 OWASP Secure Code Review，简化了内容。

### Code Review Checklist 代码审查列表

检查列表中，应该包含最关键的安全防控和漏洞领域，主要包括：

- Data Validation 数据校验
    - 在输入过程之前应该有安全检查。应该对输入数据进行验证，包括进行类型、长度、格式和范围的限制和验证。
    - 如果有请求中的参数来标识业务逻辑方法，检查是否包含用户权限相关的验证。
    - 检查绑定到用户输入的表单对象中是否存在未公开的实例变量。如果存在，请检查它们是否具有默认值。
    - 如果数据检验使用公用方法，那么一些特殊场景需要做特殊处理，例如，英文名字中应该包含“’”。
    - 数据校验要发生在服务端。
- Authentication 身份认证 & Authorization 授权
    - 检查身份验证和授权放置位置是否正确。
    - 身份验证和授权验证失败时，应该停止和终止执行请求。
    - 不使用身份验证和授权的后门，如果必须使用则应该在发布生产之前清除。
    - 身份认证应该应用于Web根目录下的所有目录及文件。
    - 对于密码的设置应该符合BC要求的密码设置原则。
    - 密码不能泄露给用户，包括泄露在日志文件、控制台程序等位置。
    - 密码应该设置有效期。
    - 认证使用的Cookies需要加密，并且不能长时间保存。
    - 认证使用凭证不能使用HTTP GET方式获取。
    - 禁止通过Cookie干预的方式绕过授权。
- Session Management Session管理
    - 如果多个组件共享Session，那么每个组件都需要对Session需要进行校验。
    - URL内容中不能包含Session参数。
    - Session需要有超时时间。
- Cryptography 加密 
    - 密码应该加密格式保存，并使用BC要求的加密算法。
    - 加密算法应该使用符合BC要求的算法。
    - 密钥不应该以硬代码方式放置。
- Error Handling 错误处理
    - 错误信息中不能包含个人信息、密码、敏感信息等内容。
    - 错误信息中不能包含详细问题信息。
- Logging 日志
    - 日志中不能包含个人信息、密码、敏感信息等内容。
    - 日志中应该能够包含成功和失败的请求。
- Security Confguration 安全类配置
    - 及时删除业务逻辑相关的未使用的配置。
- Network Architecture 网络架构
    - 数据传输过程必须使用HTTPS进行传输。
- Data 数据保存
    - 禁止将生产数据备份或还原到非生产环境或系统中。