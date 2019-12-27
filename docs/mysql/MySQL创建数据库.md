数据库可以看作是一个专门存储数据对象的容器，这里的数据对象包括表、视图、触发器、存储过程等，其中表是最基本的数据对象。在 

MySQL

 数据库中创建数据对象之前，先要创建好数据库。

在 MySQL 中，可以使用 **CREATE DATABASE**语句创建数据库，语法格式如下：

CREATE DATABASE [IF NOT EXISTS] <数据库名>
[[DEFAULT] CHARACTER SET <字符集名>] [[DEFAULT] COLLATE <校对规则名>];

```
[ ]
```

中的内容是可选的。语法说明如下：

- <数据库名>：创建数据库的名称。MySQL 的数据存储区将以目录方式表示 MySQL 数据库，因此数据库名称必须符合操作系统的文件夹命名规则，注意在 MySQL 中不区分大小写。
- IF NOT EXISTS：在创建数据库之前进行判断，只有该数据库目前尚不存在时才能执行操作。此选项可以用来避免数据库已经存在而重复创建的错误。
- [DEFAULT] CHARACTER SET：指定数据库的默认字符集。
- [DEFAULT] COLLATE：指定字符集的默认校对规则。

MySQL 的字符集（CHARACTER）和校对规则（COLLATION）两个不同的概念：字符集是用来定义 MySQL 存储字符串的方式，校对规则定义了比较字符串的方式，解决排序和字符分组的问题。

字符集和校对规则是一对多的关系，每个字符集至少对应一个校对规则，MySQL 支持 39 种字符集的将近 200 种校对规则。

#### 实例1：最简单的创建 MySQL 数据库的语句

在 MySQL 中创建一个名为 test_db 的数据库。在 MySQL 命令行客户端输入 SQL 语句

```
CREATE DATABASE test_db;
```

即可创建一个数据库，输入的 SQL 语句与执行结果如下。

mysql> CREATE DATABASE test_db;
Query OK, 1 row affected (0.12 sec)

若再次输入上述语句，则系统会给出错误提示信息，如下所示：

mysql> CREATE DATABASE test_db;
ERROR 1007 (HY000): Can't create database 'test_db'; database exists

MySQL 不允许在同一系统创建两个相同名称的数据库。

如果加上

```
IF NOT EXISTS
```

从句，则可以避免类似错误，如下所示：

mysql> CREATE DATABASE IF NOT EXISTS test_db;
Query OK, 1 row affected (0.12 sec)

#### 实例2：创建 MySQL 数据库时指定字符集和校对规则

使用 MySQL 命令行工具创建一个测试数据库，命名为 test_db_char，指定其默认字符集为 utf8，默认校对规则为 utf8_chinese_ci（简体中文，不区分大小写），输入的 SQL 语句与执行结果如下所示：

mysql> CREATE DATABASE IF NOT EXISTS test_db_char
​    -> DEFAULT CHARACTER SET utf8
​    -> DEFAULT COLLATE utf8_chinese_ci;
Query OK, 1 row affected (0.03 sec)

这时，可以使用

```
SHOW CREATE DATABASE
```

查看 test_db_char 数据库的定义声明，发现该数据库的指定字符集为 utf8，运行结果如下所示：

```
mysql> SHOW CREATE DATABASE test_db_char;
+--------------+-----------------------------------------------------+
| Database     | Create Database                                     |
+--------------+-----------------------------------------------------+
| test_db_char | CREATE DATABASE `test_db_char` /*!40100 DEFAULT CHARACTER SET utf8 */ |
+--------------+-----------------------------------------------------+
1 row in set (0.05 sec)
```

为防止字符混乱的情况发生，MySQL 有时需要在创建数据库时明确指定字符集；在中国大陆地区，常用的字符集有 utf8 和 gbk。

- utf8 能够存储全球的所有字符，在任何国家都可以使用，默认的校对规则为 utf8_general_ci，对于中文可以使用 utf8_general_ci。
- gbk 只能存储汉语涉及到的字符，不具有全球通用性，默认的校对规则为 gbk_chinese_ci。