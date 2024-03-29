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