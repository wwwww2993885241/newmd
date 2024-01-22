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
