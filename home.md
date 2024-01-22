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

# Software Requirements 软件要求

如下软件和工具建议每个开发工程师自行安装，方面快速进入开发状态

## 基础

- [Google Chrome (64-bit)](https://www.google.com/chrome/) 
- [VS Code](https://code.visualstudio.com/) 

## 前端

- [VS Code](https://code.visualstudio.com/) 

## 后端

- [Visual Studio 2019 （通过MSDN订阅的账号获取使用）](https://my.visualstudio.com/) 
- [Visual Studio 2022（通过MSDN订阅的账号获取使用）](https://my.visualstudio.com/) 
- [SQL Server  （通过MSDN订阅的账号获取使用）](https://my.visualstudio.com/) 

## Git工具

- [Git Fork](https://git-fork.com/)
- [Git Kraken](https://www.gitkraken.com/)
- [SourceTree](https://www.sourcetreeapp.com/)
- [GitHub Desktop](https://desktop.github.com/)
- [Sublime Merge](https://www.sublimemerge.com/)
- [Git Extensions](https://gitextensions.github.io/)

## 可选工具

- [Postman](https://www.getpostman.com/)
- [Jetbrains Toolbox](https://www.jetbrains.com/toolbox/)
- [LINQPad](https://www.linqpad.net/)
- [Sublime Text](https://www.sublimetext.com/)
- [Fillder](https://www.telerik.com/fiddler)

# Front End Coding Policies 前端编码规范

## HTML规范

### 标签
- 自闭合（self-closing）标签，无需闭合，例如： 
```
    <img>
    <input>
    <br>
    <hr>
```
- 可选的闭合标签（closing tag），需闭合，例如：
```
    </li>
    </body> 
```
- 尽量减少标签数量

### Class 与 ID
- class 应以功能或内容命名，不以表现形式命名。
- class 与 id 单词字母小写，多个单词组成时，采用中划线-分隔。
- 使用唯一的 id 作为 Javascript hook, 同时避免创建无样式信息的 class。

### 属性顺序
HTML 属性应该按照特定的顺序出现以保证易读性。

- id
- class
- name
- data-xxx
- src, for, type, href
- title, alt
- aria-xxx, role

### 嵌套

### HEAD 模板
```
<!DOCTYPE html>
<html lang="zh-cmn-Hans">
<head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
    <title>Style Guide</title>
    <meta name="description" content="不超过150个字符">
    <meta name="keywords" content="">
    <meta name="author" content="name, email@gmail.com">

    <!-- 为移动设备添加 viewport -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <!-- iOS 图标 -->
    <link rel="apple-touch-icon-precomposed" href="/apple-touch-icon-57x57-precomposed.png">

    <link rel="alternate" type="application/rss+xml" title="RSS" href="/rss.xml" />
    <link rel="shortcut icon" href="path/to/favicon.ico">
</head>
```

## CSS规范

### 在没有必要的情况下避免元素选择器叠加 Class、ID 使用

### Class 和 ID

- 使用语义化、通用的命名方式。
- 使用连字符 - 作为 ID、Class 名称界定符，不要驼峰命名法和下划线。
- 避免选择器嵌套层级过多，尽量少于 3 级。
- 避免选择器和 Class、ID 叠加使用。

## VUE规范 

### 慎用 this.$refs、this.$parent、this.$root、provide/inject
```
【数据流向】(#数据流向)
【慎用全局注册】(#慎用全局注册)
【组件名称】(#组件名称)
【组件中的 CSS】(#组件中的-css)
【统一标签顺序】(#统一标签顺序)
【其它注意事项】(#其它注意事项)
【 !!!其它则严格遵守 vue 官方风格指南】(#a-target_blank-hrefhttpscnvuejsorgv2style-guide其它则严格遵守-vue-官方风格指南a)
```
### 数据流向
```
props、data/$store/$route、computed (由前面派生)
  ↓
template/render
  ↓
用户交互事件、初始化的异步回调
  ↓
data/$store/$route
```

### 目录结构
```
|-- .env.development ------------ dev 环境变量
|-- .env.development.local ------ dev 本地环境变量 (被 git 忽略，需手动新建，用来重写部分环境变量)
|-- .env.production-stage ------- stage 环境变量
|-- .env.production ------------- prod 环境变量
|-- .env.test
|-- .vscode --------------------- 统一 VSCode 插件及配置
|-- static-server.js ------------ 静态资源服务 (node 运行)，通常用于预览/检查打包结果，或者临时给其他人员启用前端服务
|-- docs ------------------------ 开发文档
|   |-- README.html ------------- 由 ../README.md 手动生成 (使用 VSCode 插件 Markdown Preview Enhanced)
|   |-- xxx.md
|   |-- xxx.html
|-- public
|   |-- favicon.ico
|   |-- index.html
|   |-- libs -------------------- 不支持模块化加载的第三方 ES5 类库/模块 (只能通过全局变量引用)
|-- src
    |-- main.js
    |-- App.vue
    |-- libs -------------------- 支持模块化加载但是无法通过 npm 安装的第三方 ES5 类库/模块
    |-- assets
    |-- styles
    |   |-- global.less
    |   |-- reset.less
    |   |-- vars.less ----------- less 全局变量/函数 (webpack 自动注入)
    |   |-- xxx.less
    |-- scripts
    |   |-- utils --------------- 通用方法
    |   |-- constants ----------- 常量 (多使用 Object.freeze)
    |   |-- xxx.js
    |   |-- http ---------------- axios 实例
    |       |-- index.js
    |       |-- http.js
    |       |-- createAxios.js
    |       |-- xxx.js
    |-- injects ----------------- vue 全局注册 (慎用)
    |   |-- index.js
    |   |-- $xxx.js
    |   |-- v-xxx.js
    |   |-- mixin_xxx.js
    |   |-- xxx.js
    |-- element-ui
    |   |-- index.js
    |   |-- rewrite ------------- 主题样式复写
    |       |-- index.less
    |       |-- xxx.less
    |-- vant
    |   |-- index.js
    |   |-- vars.less ----------- 内置变量复写
    |   |-- rewrite ------------- 主题样式复写
    |       |-- index.less
    |       |-- xxx.less
    |-- router
    |   |-- index.js
    |   |-- routes.js
    |   |-- registerInterceptor.js
    |-- store
    |   |-- index.js
    |   |-- root.js
    |   |-- xxx.js
    |-- api
    |   |-- xxx.js
    |   |-- mock ---------------- 模拟数据
    |       |-- index.js
    |       |-- createMock.js
    |       |-- xxx.js
    |-- components
    |   |-- BaseXxx.vue --------- 非业务通用组件
    |   |-- TheXxx.vue ---------- 单例组件
    |   |-- ExXxx.vue ----------- 扩展/包装第三方开源组件或内部公共库组件
    |   |-- XxxXxx.vue
    |   |-- ComponentExamples --- 非单例公共组件需要在这里写示例
    |   |   |-- index.vue
    |   |   |-- XxxXxx.vue
    |   |-- SvgIcon ------------- svg-sprite 图标组件
    |   |   |-- index.vue
    |   |   |-- icons
    |   |-- directives ---------- 可复用的自定义指令（局部注册）
    |   |   |-- xxx.js
    |   |-- mixins -------------- 可复用的混入（局部注册）
    |       |-- xxx.js
    |-- views
        |-- Xxx.vue
        |-- Xxx ----------------- 除了 api 和 vuex，其它的专属模块要内聚在同一目录下
            |-- index.vue
            |-- Xxx.vue --------- 相关页面/子页面/子路由
            |-- xxx.js
            |-- xxx.module.less
            |-- components ------ 存放私有组件
```
# Back End Coding Policies 后端编码规范

## Code Style 代码规范

项目工程搭建初始，对于项目主要工程应安装代码格式分析工具，强制团队代码风格以及必要的注释、文档。

### 预期目标， 如没有按照约定，编译即报错，不允许提交代码

- 代码强制遵守广泛认可的编码风格
- 约束命名规则
- Using 按照字母顺序排序，System 优先
- 不允许有多余空格
- 对于WebApi必须有规范的注释和文档说明
- 启动代码深度和复杂度分析，约束编码逻辑和质量

### 使用方式

- 代码分析工具  StyleCop、Roslynator、XUnit Analyzers 和 Sonar Analyzer ， 建议使用StyleCop.Analyzers
- 项目文件加入 <TreatWarningsAsErrors>true</TreatWarningsAsErrors> 节点，将警告识别为错误
- 解决方案加入约定的 .editorconfig 文件
- 对于WebApi启用文档生成功能 <GenerateDocumentationFile>True</GenerateDocumentationFile>

.editorconfig 文件内容
```
# You can modify the rules from these initially generated values to suit your own policies
# You can learn more about editorconfig here: https://docs.microsoft.com/en-us/visualstudio/ide/editorconfig-code-style-settings-reference
[*.{cs,vb}]
#### Core EditorConfig Options ####
 
 
#### .NET Coding Conventions ####
 
# Organize usings
dotnet_sort_system_directives_first = true
 
# SA0001: XML comment analysis disabled
dotnet_diagnostic.SA0001.severity = none
 
# SA1101: Prefix local calls with this
dotnet_diagnostic.SA1101.severity = none
 
# SA1122: Use string.Empty for empty strings
dotnet_diagnostic.SA1122.severity = none
 
# SA1200: Using directives should be placed correctly
dotnet_diagnostic.SA1200.severity = none
 
# SA1309: Field names should not begin with underscore
dotnet_diagnostic.SA1309.severity = none
 
# SA1402: File may only contain a single type
dotnet_diagnostic.SA1402.severity = none
 
# SA1413: Use trailing comma in multi-line initializers
dotnet_diagnostic.SA1413.severity = none
 
# SA1516: Elements should be separated by blank line
dotnet_diagnostic.SA1516.severity = none
 
# SA1600: Elements should be documented
dotnet_diagnostic.SA1600.severity = none
 
# SA1601: Partial elements should be documented
dotnet_diagnostic.SA1601.severity = none
 
# SA1602: Enumeration items should be documented
dotnet_diagnostic.SA1602.severity = none
 
# SA1629: Documentation text should end with a period
dotnet_diagnostic.SA1629.severity = none
 
# SA1633: File should have header
dotnet_diagnostic.SA1633.severity = none
 
# CA1707: 标识符不应包含下划线
dotnet_diagnostic.CA1707.severity = none
```

## 编辑器警告

- 对于所有项目开发过程中，编辑器Warning警告不能出现
- 对于所有项目开发过程中，编辑器Information警告应被及时修复

## 后端编码规范

本页代码规范用于约束编码过程中的代码规范，所有开发者应阅读该内容并按照规范完成日常开发工作。

### 项目风格

#### 项目结构
- 项目中应有明确的项目结构（待补充）
- 每个解决方案（solution）中有readme.md 文件，并写明项目描述、 项目描述、所用技术栈及对应链接、补充内容等

#### Framework
- 对于常用 Framework 应及时生成Nuget包，并分析给各团队
- 每个Framework类库应有功能描述、使用及参数说明、Change log


## C# 代码风格

### 术语定义

**            Pascal 大小写**

```
        将标识符的首字母和后面连接的每个单词的首字母都大写。可以对三字符或更多字符的标识符使用Pascal 大小写。例：`BackColor`
```

**            Camel 大小写**

```
        标识符的首字母小写，而每个后面连接的单词的首字母都大写。例：`backColor`
```

**            匈牙利命名法**

```
        匈牙利命名法是一名匈牙利程序员发明的，而且他在微软工作了多年。此命名法就是通过微软的各种产品和文档传出来的。多数有经验的程序员，不管他们用的是哪门儿语言，都或多或少在使用它。

        这种命名法的基本原则是：  变量名＝属性＋类型＋对象描述

        即一个变量名是由三部分信息组成，这样，程序员很容易理解变量的类型、用途，而且便于记忆。
```

### 列宽

```
      代码列宽控制在120字符左右。
```

### 换行

```
       当表达式超出或即将超出规定的列宽，遵循以下规则进行换行
```

* * 在逗号后换行。
  * 在操作符前换行。
  * 规则1优先于规则2。

    ```
      当以上规则会导致代码混乱的时候自己采取更灵活的换行规则。
    ```

### 空行

```
      空行是为了将逻辑上相关联的代码分块，以便提高代码的可阅读性。
```

**          在以下情况下使用两个空行**

* * 接口和类的定义之间。
  * 枚举和类的定义之间。
  * 类与类的定义之间。

**          在以下情况下使用一个空行**

* * 方法与方法、属性与属性之间。
  * 方法中变量声明与语句之间。
  * 方法与方法之间。
  * 方法中不同的逻辑块之间。
  * 方法中的返回语句与其他的语句之间。
  * 属性与方法、属性与字段、方法与字段之间。
  * 注释与它注释的语句间不空行，但与其他的语句间空一行。

### 括号 - ()

* * 左括号“(”不要紧靠关键字，中间用一个空格隔开。
  * 左括号“(”与方法名之间不要添加任何空格。
  * 没有必要的话不要在返回语句中使用()。

### 花括号 - {}

* * 左花括号 “{” 放于关键字或方法名的下一行并与之对齐。如：

### 注释概述

* 修改代码时，总是使代码周围的注释保持最新。
* 在每个例程的开始，提供标准的注释样本以指示例程的用途、假设和限制很有帮助。注释样本应该是解释它为什么存在和可以做什么的简短介绍.
* 避免在代码行的末尾添加注释；行尾注释使代码更难阅读。不过在批注变量声明时，行尾注释是合适的；在这种情况下，将所有行尾注释在公共制表位处对齐。
* 避免杂乱的注释，如一整行星号。而是应该使用空白将注释同代码分开。
* 避免在块注释的周围加上印刷框。这样看起来可能很漂亮，但是难于维护。
* 在部署发布之前，移除所有临时或无关的注释，以避免在日后的维护工作中产生混乱。
* 如果需要用注释来解释复杂的代码节，请检查此代码以确定是否应该重写它。尽一切可能不注释难以理解的代码，而应该重写它。尽管一般不应该为了使代码更简单以便于人们使用而牺牲性能，但必须保持性能和可维护性之间的平衡。
* 在编写代码时就注释，因为以后很可能没有时间这样做。另外，如果有机会复查已编写的代码，在今天看来很明显的东西六周以后或许就不明显了。
* 避免多余的或不适当的注释，不应包含个人情绪内容，如幽默的不主要的备注。
* 在编写注释时使用完整的句子。注释应该阐明代码，而不应该增加多义性。
* 使用注释来解释代码的意图。它们不应作为代码的联机翻译。
* 注释代码中不十分明显的内容。
* 为了防止问题反复出现，对错误修复和解决方法代码总是使用注释。
* 对由循环和逻辑分支组成的代码使用注释。这些是帮助源代码读者的主要方面。
* 在整个应用程序中，使用具有一致的标点和结构的统一样式来构造注释。
* 用空白将注释同注释分隔符分开。在没有颜色提示的情况下查看注释时，这样做会使注释很明显且容易被找到。
* 代码修改变更记录不应使用注释标明修改日期和修改人，注释应只针对代码不记录版本，代码版本应该使用代码版本系统进行管理
* 为了使层次清晰，在闭合的右花括号后注释该闭合所对应的起点。

### 文档型注释

```
      该类注释采用.Net已定义好的Xml标签来标记，在声明接口、类、方法、属性、字段都应该使用该类注释，以便代码完成后直接生成代码文档，让别人更好的了解代码的实现和接口。如

      注释标签的使用请参考:[http://msdn.microsoft.com/zh-cn/library/5ast78ax.aspx](http://msdn.microsoft.com/zh-cn/library/5ast78ax.aspx)
```

### 单行注释

```
    该类注释用于
```

* * 方法内的代码注释。如变量的声明、代码或代码段的解释。例：//// 注释语句// privateint number; 或 // 注释语句privateint number;
* * 方法内变量的声明或花括号后的注释, 例：if(1 == 1)// always true { statement; } // always true

### 初始化

```
      建议在变量声明时就对其做初始化。
```

### 类和接口的声明

* 在方法名与其后的左括号间没有任何空格。
* 左花括号 “{” 出现在声明的下行并与之对齐，单独成行。
* 方法间用一个空行隔开。

### 字段的声明

不要使用是 public 或 protected 的实例字段。如果避免将字段直接公开给开发人员，可以更轻松地对类进行版本控制，原因是在维护二进制兼容性时字段不能被更改为属性。考虑为字段提供 get 和set 属性访问器，而不是使它们成为公共的。 get 和 set 属性访问器中可执行代码的存在使得可以进行后续改进，如在使用属性或者得到属性更改通知时根据需要创建对象。下面的代码示例阐释带有 get 和 set 属性访问器的私有实例字段的正确使用。例：

public class Control: Component { private int handle; public int Handle { get { return handle; } } }

## ***1*** **|*****5*****命名规范**

### 命名概述

> 名称应该说明“什么”而不是“如何”。通过避免使用公开基础实现（它们会发生改变）的名称，可以保留简化复杂性的抽象层。例如，可以使用 `GetNextStudent()`，而不是 `GetNextArrayElement`()。

**命名原则是：**

> 选择正确名称时的困难可能表明需要进一步分析或定义项的目的。使名称足够长以便有一定的意义，并且足够短以避免冗长。唯一名称在编程上仅用于将各项区分开。表现力强的名称是为了帮助人们阅读；因此，提供人们可以理解的名称是有意义的。不过，请确保选择的名称符合适用语言的规则和标准。

**以下几点是推荐的命名方法：**

* 避免容易被主观解释的难懂的名称，如方面名 `AnalyzeThis()`，或者属性名 `xxK8`。这样的名称会导致多义性。
* 在类属性的名称中包含类名是多余的，如 `Book.BookTitle`。而是应该使用 `Book.Title`。
* 只要合适，在变量名的末尾或开头加计算限定符 `（Avg、Sum、Min、Max、Index）`。
* 在变量名中使用互补对，如 `min/max、begin/end` 和 `open/close`。
* 布尔变量名应该包含 `Is`，这意味着 `Yes/No` 或 `True/False` 值，如 `fileIsFound`。
* 在命名状态变量时，避免使用诸如 `Flag` 的术语。状态变量不同于布尔变量的地方是它可以具有两个以上的可能值。不是使用 `documentFlag`，而是使用更具描述性的名称，如 `documentFormatType`。
* 即使对于可能仅出现在几个代码行中的生存期很短的变量，仍然使用有意义的名称。仅对于短循环索引使用单字母变量名，如 i 或 j。 可能的情况下，尽量不要使用原义数字（幻数）或原义字符串，如
  `for (int i = 1; i < 7; i++)`。而是使用命名常数，如 `for (int i = 1; i < NUM_DAYS_IN_WEEK; i++)` 以便于维护和理解。

### 大小写规则

**     大写**

* * 组织名缩写使用大写
  * 两个或者更少字母组成的标识符使用大写。例：

| 标识符                    | 大小写 | 示例                                                   |
| ------------------------- | ------ | ------------------------------------------------------ |
| ------------------------- |        |                                                        |
| 类                        | Pascal | AppDomain                                              |
| -                         | -      | -                                                      |
| 枚举类型                  | Pascal | ErrorLevel                                             |
| 枚举值                    | Pascal | FatalError                                             |
| 事件                      | Pascal | ValueChange                                            |
| 异常类                    | Pascal | WebException``注意: 总是以 Exception 后缀结尾。 |
| 只读的静态字段            | Pascal | RedValue                                               |
| 接口                      | Pascal | IDisposable``注意: 总是以 I 前缀开始。          |
| 方法                      | Pascal | ToString                                               |
| 命名空间                  | Pascal | System.Drawing                                         |
| 属性                      | Pascal | BackColor                                              |
| 公共实例字段              | Pascal | RedValue``注意: 应优先使用属性。                |
| 受保护的实例字段          | Camel  | redValue``注意: 应优先使用属性。                |
| 私有的实例字段            | Camel  | redValue                                               |
| 参数                      | Camel  | typeName                                               |
| 方法内的变量              | Camel  | backColor                                              |

### 缩写

```
      为了避免混淆和保证跨语言交互操作，请遵循有关区缩写的使用的下列规则：
```

* * 不要将缩写或缩略形式用作标识符名称的组成部分。例如，使用 `GetWindow`，而不要使用 `GetWin`。
  * 不要使用计算机领域中未被普遍接受的缩写。
  * 在适当的时候，使用众所周知的缩写替换冗长的词组名称。例如，用 `UI` 作为 `User Interface` 缩
    写，用 `OLAP` 作为 `On-line Analytical Processing` 的缩写。
  * 在使用缩写时，对于超过两个字符长度的缩写请使用 Pascal 大小写或 Camel 大小写。例如使用 `HtmlButton` 或 `HTMLButton`；但是，应当大写仅有两个字符的缩写，如：`System.IO`，而不是 `System.Io`。
  * 不要在标识符或参数名称中使用缩写。如果必须使用缩写，对于由多于两个字符所组成的缩写请使用Camel 大小写。

### 命名空间

* * 命名命名空间时的一般性规则是使用公司名称，后跟技术名称和可选的功能与设计，如：CompanyName.TechnologyName[.Feature][.Design]

### 类

* * 使用 Pascal 大小写。
  * 用名词或名词短语命名类。
  * 使用全称避免缩写，除非缩写已是一种公认的约定，如 `URL`、`HTML`
  * 不要使用类型前缀，如在类名称上对类使用 C 前缀。例如，使用类名称 `FileStream`，而不是
    `CFileStream`。
  * 不要使用下划线字符 (_)。
  * 有时候需要提供以字母 I 开始的类名称，虽然该类不是接口。只要 I 是作为类名称组成部分的整个单词的第一个字母，这便是适当的。例如，类名称 `IdentityStore` 是适当的。在适当的地方，使用复合单词命名派生的类。派生类名称的第二个部分应当是基类的名称。例如，`ApplicationException` 对于从名为 `Exception` 的类派生的类是适当的名称，原因 `ApplicationException` 是一种 `Exception`。请在应用该规则时进行合理的判断。例如，`Button` 对于从 `Control` 派生的类是适当的名称。尽管按钮是一种控件，但是将 `Control` 作为类名称的一部分将使名称不必要地加长。

### 接口

* * 用名词或名词短语，或者描述行为的形容词命名接口。例：
    * 接口名称 `IComponent` 使用描述性名词
    * 接口名称 `ICustomAttributeProvider` 使用名词短语
    * 接口名称 `IPersistable` 使用形容词。
  * 使用 Pascal 大小写。
  * 少用缩写。
  * 给接口名称加上字母 I 前缀，以指示该类型为接口。在定义类/接口对（其中类是接口的标准实现）时使用相似的名称。两个名称的区别应该只是接口名称上有字母 I 前缀。
  * 不要使用下划线字符 (_)。

### 属性类 (Attribute)

```
           应该总是将后缀 Attribute 添加到自定义属性类。例：public class ObsoleteAttribute { }
```

### 枚举 (Enum)

```
       枚举 (Enum) 值类型从 Enum 类继承。
```

* * 对于 Enum 类型和值名称使用 Pascal 大小写。
  * 少用缩写。
  * 不要在 Enum 类型名称上使用 Enum 后缀。
  * 对大多数 Enum 类型使用单数名称，但是对作为位域的 Enum 类型使用复数名称。
  * 总是将 `FlagsAttribute` 添加到位域 Enum 类型。

### 参数

* * 使用描述性参数名称。参数名称应当具有足够的描述性，以便参数的名称及其类型可用于在大多数情况下确定它的含义。
  * 对参数名称使用 Camel 大小写。
  * 使用描述参数的含义的名称，而不要使用描述参数的类型的名称。开发工具将提供有关参数的类型的有意义的信息。因此，通过描述意义，可以更好地使用参数的名称。
  * 不要给参数名称加匈牙利语类型表示法的前缀，仅在适合使用它们的地方使用它们。
  * 不要使用保留的参数。保留的参数是专用参数，如果需要，可以在未来的版本中公开它们。相反，如果在类库的未来版本中需要更多的数据，请为方法添加新的重载。

### 方法

* * 使用动词或动词短语命名方法。
  * 使用 Pascal 大小写。

### 属性 (property)

* * 使用名词或名词短语命名属性。
  * 使用 Pascal 大小写。
  * 考虑用与属性的基础类型相同的名称创建属性。例如，如果声明名为 `Color` 的属性，则属
    性的类型同样应该是 Color。

### 事件

* * 对事件处理程序名称使用 `EventHandler` 后缀。
  * 指定两个名为 `sender` 和 `e` 的参数。`sender` 参数表示引发事件的对象。`sender` 参数始
    终是 `object` 类型的，即使在可以使用更为特定的类型时也如此。与事件相关联的状态封装
    在名为 `e` 的事件类的实例中。对 `e` 参数类型使用适当而特定的事件类。
  * 用 `EventArgs` 后缀命名事件参数类。
  * 考虑用动词命名事件。
  * 使用动名词（动词的“ing”形式）创建表示事件前的概念的事件名称，用过去式表示事
    件后。例如，可以取消的 `Close` 事件应当具有 `Closing` 事件和 `Closed` 事件。不要使用
    `BeforeXxx/AfterXxx` 命名模式。
  * 不要在类型的事件声明上使用前缀或者后缀。例如，使用 `Close`，而不要使用 `OnClose`。
  * 通常情况下，对于可以在派生类中重写的事件，应在类型上提供一个受保护的方法（称为
    `OnXxx`）。此方法只应具有事件参数 `e`，因为发送方总是类型的实例。
  * 字段
* private、protected 使用 Camel 大小写。
* public 使用 Pascal 大小写。
* 拼写出字段名称中使用的所有单词。仅在开发人员一般都能理解时使用缩写。

### 静态字段

* * 使用名词、名词短语或者名词的缩写命名静态字段。
  * 使用 Pascal 大小写。
  * 建议尽可能使用静态属性而不是公共静态字段。

### 集合

```
     集合是一组组合在一起的类似的类型化对象，如哈希表、查询、堆栈、字典和列表，集合的命名建议用复数。
```

### 措词

```
       避免使用与常用的 .NET 框架命名空间重复的类名称。例如，不要将以下任何名称用作类名称：System、Collections、Forms 或 UI。有关 .NET 框架命名空间的列表，请参阅类库。

       另外，避免使用与C#语言关键字冲突的标识符。
```

### 表达式

* * 避免在表达式中用赋值语句
  * 避免对浮点类型做等于或不等于判断

### 类型转换

* * 尽量避免强制类型转换。
  * 如果不得不做类型转换，尽量用显式方式。
# Database Policies 数据库规范

## 命名规范规定

- 表名必须使用单数名

- 禁止使用无谓的表格后缀

- 所有表示时间的字段，应该统一以 Date 来作为结尾

- 所有表示数目的字段，应该以Count作为结尾

- 所有代表链接的字段，应该使用Url结尾

- 所有名称的字符范围为：A-Z, a-z, 0-9 和_(下划线)。禁止使用其他字符作为名称。

- 必须采用英文单词或英文短语（包括缩写）作为名称，不能使用无意义的字符或汉语拼音。

- 名称必须清晰明了，能够准确表达事物的含义，最好可读，遵循“见名知意”的原则。

## 表设计命名规范

- 注意字段名不应该使用保留关键字：如action,avg等

- 不应该使用tab或tbl作为表前缀（本来就是一个表，为什么还要说明）

- 表名应该以代表表内的内容的一个和多个名词组成，每个名词的第一个字母大写，例如：User、UserLogin，UserGroupRelation等

- 应该使用表的内容分类作为表名的前缀：如，与用户信息相关的表使用前缀User，与内容相关的信息使用前缀Content。

- 表的前缀以后，是表的具体内容的描述。如：用户登录信息的表名为：UserLogin，用户在论坛中的信息的表名为：UserBBSInfo

- 一些作为多对多连接的表，应该使用两个表的前缀作为表名：

         如：用户登录表UserLogin，用户分组表GroupInfo，这两个表建立多对多关系的表名为：UserGroupRelation

## 存储过程命名

不应该使用存储过程

## 视图命名

不应该使用视图

## 主键命名

- 一个数据库中的主键名不能重复

- 主键名=PK_(前缀)+[表名]

## 外键命名

- 一个数据库中的外键名不能重复

- 外键名=FK_(前缀)+[主表名]+[从表名]+[字段名]

## 字段命名规范

- 字段不应该使用任何前缀（表名代表了一个名称空间，字段前面再加前缀显得罗嗦）

- 布尔型的字段，应该以一些助动词开头，更加直接生动：如，用户是否有留言HasMessage，用户是否通过检查IsChecked等。

- 字段名应该为英文短语、形容词+名词或助动词+动词时态的形式表示，大小写混合，遵循“见名知意”的原则。

## 表创建规范

1. 创建新的表结构，必须有创建日期时间和修改日期时间（CreatedOn` datetime NOT NULL DEFAULT CURRENT_TIMESTAMP COMMENT '创建时间',LastModifiedOn` datetime NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP COMMENT '修改时间'），创建日期和修改日期赋值均通过数据库自动触发，禁止任何程序代码进行赋值。

2. 业务表宽度可以限制在30个字段以内。

3. 业务分类或状态标识字段值域应该为10的整数倍，以便后续进行扩展。

4. 业务主表中如果出现单个字段的数据存储值超过300，可以扩充子业务表进行存储。

6. 业务数据不应该进行物理删除，需对数据处理进行逻辑删除。

7. 如果频繁地访问涉及的是对两个相关的表进行连接操作，应该将其合并

8. 如果频繁地访问只是在表中的某一部分字段上进行，则应该分解表，将该部分单独作为一个表

9. 当系统中有一些少量的，重复出现的值时，应该使用字典表来节约存储空间和优化查询。如地区、系统中用户类型的代号等。这类值不会在程序的运行期变化，但是需要存储在数据库中。

## 索引

1. 如果查询是瓶颈，可以在关系上建立适当的索引；通常，作为查询条件的属性上建立索引可以提高查询效率。

2. 如果更新是瓶颈，因为每次更新都会重建表上的索引，引起效率降低，则可以考虑删除某些索引。

3. 选择适当索引，如果经常使用范围查询，则B树索引比散列索引更高效

4. 应该将有利于大多数查询和更新的索引设为聚集性索引。

## SQL性能优化规范

1. 多表关联查询表个数原则上不超过三个，如果超过三个业务表的复杂的sql，需要拆分成多个SQL进行执行。具体视情况而定。

2. list查询SQL尽量要有起止时间和结束时间，默认起止时间和结束时间区间为2~6个月。

3. 联合索引创建的字段建议不要超过三个，防止大量无效的索引占用空间，造成索引效率低下。

4. 严格禁止循环对数据库进行查询，建议批量查询操作提升性能。

5. 返回结果集存在按时间先后顺序返回数据的，优先通过主键ID进行排序（正常情况下，ID是作为主键默认是有索引的，），尽量不要用时间进行排序（时间排序会带来file sort性能损耗，如果为此排序单独给时间字段创建索引，会进行索引空间的开销）。

6. 只检索需要的列

7. 只使用需要的检索项检索数据，其余查询不需要的检索可以在代码中使用if过滤掉

# Naming 命名

命名原则适用于项目Projects、解决方案Solutions、命名空间Namespaces、代码仓储Git Repositories

- 以BCChina开始。
- 以BCChina开始。，全部大写字母命名只用于机构缩写（例如：NEEA等）、系统缩写（例如：VCS、MIS2、IOL等）、产品类型（例如：IELTS、UKVI等）。
- 使用大驼峰命名法命名其他名字。

| Good | Bad |
| --- | --- |
| BCChina.IOL.IELTS.Domain | BCChina.Vcs.Ielts.Domain or bcchina.vcs.ielts.domian |
| BCChina.MIS2 | BCChina.mis2 or Bc.Mis2 |
| BCChina.NEEA.Sync | BcChina.neea.sync or BcChina.Neea.Sync |
| BCChina.VOPortal.WebApi | BCChina.Voportal.Webapi or BcChina.voportal.webApi |

Git 分支和源码管理
分支管理
分支命名
master：主分支，永远是可用的、稳定的、可直接发布的版本，由 develop 以及 hotfix 分支合并，不能直接在该分支上开发。
develop：开发主分支，代码永远是最新，所有 feature 分支以这个分支来创建自己的开发分支，该分支只做只合并操作，不能直接在该分支上开发。
feature/xxx：功能开发分支，在 develop 上创建分支，以自己开发功能模块命名，功能测试正常后合并到 develop 分支。
release：预发布分支，在合并好 feature 分支的 develop 分支上创建，主要是用来提测的分支，修改好 bug 并确定稳定之后合并到 develop 和 master 分支，然后发布 master 分支。
hotfix/xxx：紧急 bug 修改分支，项目上线之后可以会遇到一些环境问题需要紧急修复，在对应版本的 release 分支上创建，流程跟 release 分支相似，修复完成后合并 release 分支，根据情况判断需不需要再合并到 develop 和 master 分支。
注意事项
一个分支尽量开发一个功能模块，不要多个功能模块在一个分支上开发。
开发过程中，如果组员 A 开发的功能依赖组员 B 正在开发的功能，可以待组员 B 开发好相关功能之后，组员 A 直接 pull 组员 B 的分支下来开发，不需要先将组员 B 的分支 merge 到 develop 分支。
feature 分支在申请合并之前，一定要是先 pull 一下 develop 主分支下来，看一下有没有冲突，如果有就先解决冲突后再申请合并。
分支实践
feature/add-subject

(如果需要可以添加一个链接到 issue 地址或者其它文档)

Git Commit Message(GCM)
好的 GCM 能帮到我们什么
加快审查进程,
帮助项目未来的维护者,说五年后的未来,找出为什么特定的更改的代码或增加了特定的功能——他们为什么(之一)的主要手段,
开发团队的成员之间的沟通
帮助我们编写良好的版本发布日志
GCM 的模板格式
每个提交消息必须由一个头和一个可选的主体组成。
头部有一个特殊的格式，包括一个类型、一个 PB(US)标记和一个主题。
注意字母大小写和标点符号——PB(US)标记应该在圆括号内，后面跟着冒号。
// 整个提交消息中最重要的部分是主题。
<type>(<PB_tag>): <subject>
<blank_line>
[optional body]
提交类型

feat: 新功能
fix: bug 修复
docs: 文档跟新
refactor:代码重构
chore: 对构建过程或辅助工具和库的更改
test：测试代码相关
style: 仅仅修改了空格、格式缩进等等，不改变代码逻辑
merge: 解决冲突
revert：回滚到上一个版本
sync：同步主线或分支的 Bug
perf：优化相关，比如提升性能、体验
GCM 实践
feat(#1016): add ValidateAddress method to ExamDateValidator
fix(#734): add missing `track by`
(如果需要可以添加一个链接到issue地址或者其它文档)
//携带描述
feat(#9912): add cache for user permissions
<blank_line>
Without permissions cache every call to api caused request to
security system to obtain user permissions. Currently permissions are cached
for multiple request for 10 minutes.

# Pull Requests

## 为什么我们要用 PRs

- 代码质量更有保证，参与进来的的同事更多，看问题更全面，对代码本身甚至设计理念都会有一个保证，并允许团队成员在项目中保持一致和纪律。

- 更多人受益，除了代码提交者本身，参与进来的同事甚至“路过”的同事都可以从 comments 中看到整个讨论的过程，提供了良好实践的来源。

- 学习效果好，对于提交者来讲有点心理压力，印象更深刻。

- 正能量，当提交很棒的功能或者漂亮的代码时会被各种赞美，于是脑子一热又多做一个需求。

## PR 标题格式

## 我们应该怎么做

### 开发者

1. 在发出 PRs 之前，您必须验证所有单元和集成测试都能通过。
2. 负责你自己的 PRs，直到它被合并。
3. 创建 PR 之前和之后都要事先自己 review 提交的代码。
4. 保持的你的 PRs 和你的目标分支的同步。
5. 经常回复评论者的评论，并对你的决定进行论证。
6. 等待被审批过的合并，即使您已经回复了他们。这将给审阅人员一个机会来查看评论并可能进行回复。
7. 不要轻率地听从评论的变化——我们是鼓励讨论的。
8. 在可能会让审阅人员感到困惑的地方留下注释。
9. 保持 PR 尽可能小(尽量避免在一个大 PR 中堆积多个任务——把它分成多个小任务)。
10. 如果有依赖于其他项目的 PRs，需要著名依赖 PRs 的链接(如须同时合并)。
11. 创建 PR 的描述性标题，而不是默认标题(分支名称)。

### 评审者

1. 定期检查 PRs——每天安排一两次定期检查。
2. 不管别人是否已经 approved，都要对 PR 进行评审——其他评审人员可能漏掉了一些东西。
3. 即使您没有明确地列在 PR 评审人员列表中，也要对 PR 进行评审(例如，其他团队所做的一些更改可能会影响您的应用程序部分)。
4. 如果问题不是很明显，总是试着提出你的建议。
5. 永远不要推迟 PR 评审(特别是当有人直接要求的时候!)-代码评审是你工作的一个重要部分。
6. 代码评审不仅仅是发现代码变坏的征兆或者其他不好的东西——如果你发现了你喜欢的东西，用积极的评论来感谢作者。

### 团队领导者

1. 鼓励你的团队进行更高层次的评审活动
2. 标记还不能合并的 PRs(例如在 PR 标题中放置[暂停])，并在准备合并时取消标记
3. 不要为分支之间的同步创建 PRs (release/X -> development, develop -> feature/long-lived)，在本地合并分支并将更改直接推送到目标分支。确保所有的单元测试和集成测试都运行良好。

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



# Environment Management And Contorl Policies 环境管理和管控政策

## 开发人员禁止访问生产数据

生产环境包含关键数据。如果访问生产环境，不仅会涉及数据泄露，还涉及到进行了未经授权的操作。

## 部署角色隔离

只允许DM可以批准生产环境的发布。

## 隐藏生产环境密钥

生产管理访问权限，只能严格授予给专用的用户组。Azure DevOps Release Pipeline工具可以隐藏所有的生产密钥。
