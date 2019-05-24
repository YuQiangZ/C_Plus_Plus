# MySQL学习笔记

## 1. 数据库分类

- 网络数据库
- 层级数据库
- 关系数据库 
  1. 关系数据结构
  2. 关系操作集合
  3. 关系完整性约束

## 2. SQL（Structured Query Language） 指令介绍

``` mysql
net start mysql;//开启服务
net stop mysql;//关闭服务

mysql -h IP地址/域名 -P 端口(3306) -u 用户名 -p 密码;//登录MySQL

exit/\q/quit;//均可退出MySQL

create database 数据库名字 库选项;//创建数据库 [charset 字符集名称]
show databases;//显示全部数据库
show databases like '匹配模式';//_:匹配当前位置单个字符 %：匹配当前位置多个字符
show create database 数据库名字;//可以显示创建数据库的基本信息（字符集等）

use 数据库名字；//可以进到这个数据库，进行想关才做
alter database 数据库名字 charset = 字符集;//修改数据库 注：一般不要做这种操作
drop database 数据库名字;//删除数据库

create table 表名(字段名 字段类型[字段属性]，字段名 字段类型[字段属性]，...);//创建表
    alter table 表名 add [column] 新字段名 列类型 [列属性] [位置first/after 字段名];//加字段
    alter table 表名 change 旧字段名 新字段名 字段类型 [列属性] [新位置];//修改字段名
    alter table 表名 modify 字段名 新类型 [新属性] [新位置];//修改字段类型
    alter table 表名 drop 字段名;//删除字段
create table 新表名 like 数据库名.表名;//复制已有表结构
show tables;//显示所有表名
show tables like '匹配模式'；//参照上文
describe / desc/ show columns from 表名;//显示表名：显示表中所包含的字段信息（名字，类型，属性等）
show create table 表名;//显示表创建语句
alter table 表名 表选项 [=] 值;//表属性指的就是表选项：engine，charset和collate
rename table 旧表名 to 新表名;//修改表名
drop table 表名[,表名2…];//删除表结构

insert into 表名[(字段列表)] values(对应字段列表);//向表中指定字段插入数据

select * from 表名;//查询表中全部数据
select 字段列表 from 表名;//查询表中部分字段
select 字段列表 / * from 表名 where 字段名 = 值;//简单条件查询数据

delete from 表名 [where 条件];//如果没有where条件：意味着系统会自动删除该表所有数据（慎用）

update 表名 set 字段名 = 新值 [where 条件];//将数据进行修改（通常是修改部分字段数据）
  
```



