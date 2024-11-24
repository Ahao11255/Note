# MySQL的DML操作

## DML操作

DML是数据操作语言，主要对MySQL数据进行增删改

### 关键字

inster	update	delete	truncate







## 数据插入

关键字：inster

格式：

​	方式1：

​		inster into 表 (列名1,列名2,列名3,列名4......) values (值1,值2,值3,值4......);

​	方式2：

​		inster into 表 values (值1,值2,值3,值4......);







## 数据修改

关键字：update

格式：

​	方式1：

​		update 表 set 字段名=值,字段名=值......;

​	方式2：

​		update 表 set 字段名=值,字段名=值...... where ......;





## 数据删除

关键字：delete/truncate

格式：

​	方式1：

​		delete from 表名；			------#会将整个表数据删除！				

​	方式2：

​		delete from 表名 where ......;

​	方式3：

​		truncate 表名;						------#清空整个表，本质上是删除表并创建新表，与delete不同！