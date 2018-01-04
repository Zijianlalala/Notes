# MySQL触发器trigger
#编程/MySQL
## 需求背景

### 数据库表
最近正在做图书管理系统，数据库中建立三个表

* 用户表 users

Field     | Type         | 解释
--------- | -----------  | ----
id        | int(11)		  |	用户id
username  | varchar(25)  |用户名
password  | varchar(45)  |密码
priority  | int(1)       |权限
available | int(11)      |可借阅图书数

* 图书表 books

Field     | Type         | 解释
--------- | -----------  | ----
id        | int(11)		  |	书号
name  | varchar(25) 	 |书名
author  | varchar(45)	  |作者
price  | float     		 |价格
others | varchar(40)     |备注
num    | int(11)      	 | 拥有数量
	
* 用户-图书表 user_book

Field     | Type         | 解释
--------- | -----------  | ----
id        | int(11)		  |	id
user_id  | int(25)  	|用户id
book_id  | int(45) 		 |书号
borrow_time  | DATE	   |借阅时间

### 实现逻辑

在向**user_book**表中插入一条数据后，触发users表中**available**减1以及books表中**num**减1操作

* beforeInsertTrigger

```
CREATE DEFINER=`root`@`localhost` TRIGGER `library`.`user-book_BEFORE_INSERT` BEFORE INSERT ON `user_book` FOR EACH ROW
BEGIN
    if (select available from users where id=NEW.user_id) > 0 and 
    (select num from books where id=NEW.book_id) >0 then
    SET NEW.borrow_time = NOW();
    update users set available=available-1 where id=NEW.user_id;
    update books set num=num-1 where id=NEW.book_id;
   
	else signal sqlstate 'HY000' set message_text = '借阅失败';
    end if;
END
```

* afterDeleteTrigger

```
CREATE DEFINER=`root`@`localhost` TRIGGER `library`.`user_book_AFTER_DELETE` AFTER DELETE ON `user_book` FOR EACH ROW
BEGIN
	update users set available = available+1 where id= OLD.user_id;
    update books set num=num+1 where id=OLD.book_id;
END

```