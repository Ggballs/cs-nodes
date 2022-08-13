# Database

# 考试可以带一页A4纸笔记

# 1.General Concept

* DBMS database Management System

* View of Data

  * Levels of Data Abstraction

    (from bottom up)

    * Physical level: describe how to store the record;
    * logical level:  describe data sorted in database and **relationships **among data and upper level;
    * view level: 

  * Schemas :

    * structure of DB on different levels
    * Physical schema: DB structure design at  PL
    * Logical schema: DB structure design at LL;
    * subschema:       schema at view level;

  * Instance: like the value of a variable

  * relationship between Instance and Schema:

    **type** <->**schema**  **variable**<->**instance**; 

    <img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220306204733873.png" alt="image-20220306204733873" style="zoom:33%;" />

  * Physical Independence & Logical independence

    * Physical data Independence :

       **modify** the **physical schema** without changing the **logical schema**

      applications depend on the logical schema

    * Logical data Independence:

      **protect application** programs from **changes in logica**l structure of data.

      **is hard to achieve as application programs are heavily dependent on the logical structure of data.**




* Database Language

  DD(definition)L :defining;			CREATE、DROP、ALTER等语句。

  DM(manipulation)L:accesing and manipulating the data		INSERT（插入）、UPDATE（修改）、DELETE（删除）语句。

  DC(control)L:		give user's access priviledge to database	GRANT、REVOKE等语句。

  * DDL

    Specifies a database scheme as a set of definitions of relational schema.

    specifies **storage structure, access methods consistency constrains**

    <img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220306214845943.png" alt="image-20220306214845943" style="zoom: 50%;" />

    DDL statements are compiled and stored as a file called **data dictionary**

    * data dictionary

      Database schema

      Integrity constrains:  Primary key  Referential integrity

      Authorization

  * DML

    Retrieve

    insert/delete/update

    also called as **query Language**

    ​						(**SQL** is the most widely used one)

    ​	2 classes:

    * Procedural DML: specifies **what** data is required and how to get it
    * Nonprocedural DML:  specifies what data is required without specifying how to get those data.

  * SQL

    SQL = DDL+DML+DCL

    ![image-20220306220042381](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220306220042381.png)

    

    

* Database Design

  A high-level description of data, constrains using **Entity-Relationship** model 

  * E-R Model
    * Entities :(objects) e.g: customers account (described by a set of atrributes)
    * Relationships between entities:![image-20220307004315182](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220307004315182.png)
  * ![image-20220307004340791](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220307004340791.png)
  * ![image-20220307004428963](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220307004428963.png)

* Database administrator(DBA):

  special user having the central control---including:

  * Schema definition
  * Storage structure and method definition
  * Granting of authorization for data modification 

  ​	

* DB Architecture

  <img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220307005932518.png" alt="image-20220307005932518" style="zoom: 67%;" />

  <img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220307010006742.png" alt="image-20220307010006742" style="zoom:67%;" />

  * Storage Manager

     a program module that provides the interface between the low-level data stored in the database and the application programs and queries submitted to the system. 

    * responsible for :①interaction with file manager

    ​							②Efficient storing ,retrieving and updating of data

    * include:
    * ![image-20220307005531618](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220307005531618.png)

  * Query Processor

    includes DDL interpreter,DML compiler, query processing

    <img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220307005733704.png" alt="image-20220307005733704" style="zoom:67%;" />

    * Query Processing Optimization 

    

  

  

  

# 2.Relation：

- **table**  contains  more than 1 attributes

  ​			a row represents a relationship among a set of value

  ​			a column represent a set of attribute

   a lot different tables to comprise the whole **relations** among all the attributes

- **tuple** 

  ​	simply a sequence (or list )of values;

  ​	(refers to a rows of the table)

- **attribute**

  ​	refers to a column of the table

  

  

## 2.1 fundamental relation-algebra operator

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220302111605514.png" alt="image-20220302111605514" style="zoom: 50%;" />



* ## Structure of Relational Databases

  KEY:(a set of attribute)

  * primary key: nonnull   and  unique(no 2 tuples have the same primary-key attributes)
  * foreign key: the connection attributes between two tuples 
  * super key: 能区分在一个学生的表中，假设有“学号”、“姓名”、“相关信息”、“生日”等字段， 其中学号是唯一的，那么（学号）是一个超键，也可称为[主键](https://baike.baidu.com/item/主键/1232239)，同时（学号，姓名，生日）的组合也是唯一的，所以也可以为一个超键。但（学号，姓名，生日）当插入不唯一的集合，例如插入学号、姓名、生日相同的情况，就会出错不允许插入，反正记住一点，就是这些属性可以区别每一个学生的就是超键，也就是根据这些属性可以唯一确定一名学生的，就是超键。
  * candidate key : (included by the super key) and (any one could be chosen as primary key)

* ## Fundamental relation-Algebra Operations

  selection:![image-20220302213031722](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220302213031722.png)	

  ![image-20220329195851294](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220329195851294.png)

  ![image-20220329200118962](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220329200118962.png)

  projection:![image-20220302213041503](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220302213041503.png)

  

  Union:![image-20220302213103182](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220302213103182.png)

  //(that has to be two tuples have the same schemas)

  

  <img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220302213400603.png" alt="image-20220302213400603" style="zoom:80%;" />

  除法：

  ![image-20220528192817769](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220528192817769.png)

  借过全部在McGraw-Hill 出版的books的人

  ![image-20220529175319859](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220529175319859.png)

  

  

  在取自然交集时可以使用on，在relational algebra 中表示为括号内的字符

  （字符内表达的tuples是符号左右的2个tuple）

  ![image-20220529163752409](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220529163752409.png)

* ## Additional Relation-Algebra Operations

  Set-intersection: 交集 

  Set-difference 并集   //2 者 均为等元运算 +Uinion

  Natural Join: ![image-20220302213526346](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220302213526346.png)

  <img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220302213602078.png" alt="image-20220302213602078" style="zoom: 50%;" />

  只找2 tuples 间 相同attributes 中 items也相同的行找全排列；

  如图2*2+1=5；

  Theta Join =![image-20220302213745402](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220302213745402.png) 

  Division: 

  ![image-20220302213809207](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220302213809207.png)

  operations only between two attributes (but could from different tuples)

  assignments:  ->

  <img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220302214042838.png" alt="image-20220302214042838" style="zoom:50%;" />

  as the 赋值 in C++

  E。G![image-20220302214417144](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220302214417144.png)

  

* ## Extended Relation-Algebra Operations

  ![image-20220302214848789](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220302214848789.png)

  

  semijoin：

  ![image-20220618012959973](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220618012959973.png)

  作为选择条件

  ![image-20220618013223851](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220618013223851.png)

  exists 比 in 快 也比 count（*） 快 在大数据时

  小数据时 count 比 exist 快

  

* ## Modification of the Database

  <img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220302120001483.png" alt="image-20220302114132820" style="zoom: 67%;" />

  ​	unknown or inexistence 

  ​	记忆：  priority：

  ​	or   true > unknown> false      

  ​	and false > unknown > true;

* ## Aggregation

  ①：可以直接求一个单独的值

  ![image-20220529161615500](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220529161615500.png)

  ②：也可以求group by 之后的列表

  ![image-20220529161606883](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220529161606883.png)

  G1 G2 表示按照多少种因素分组 比如name, dept  有这2个因素分组， 每个组都需要name dept都相同才行

# 3.SQL

## DDL

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220309103222170.png" alt="image-20220309103222170" style="zoom:67%;" />

```sql
char(n): A fixed -length n string; if the length of stored string <n; will be filled with spaces
varchar(30);//变长字符串 with longest length at 30;
int 
float(n):with precision of at least n digits;
numeric(8,2);// integer value has 8 bit , frac in 2 bit （总共8位）(6位小数点前，2位后)in 10-进制

//注意里面的not null  
//check为新建函数  check()只有是false才不插入  所以NULL也可以插入成功

eg:
create table department
	(	dept_name varchar(20),
    	building varchar(15),
    	budget	numeric(12,2),
    	primary key 	(dept_name) );##or could be more in the quotion
    	
 create table course
 	(	dept_name varchar(20),
     ...
     	primary key(1,2,3....),
     	foreign key(dept_name)reference department,
    	foreign key ()..reference...);
        ## foreign key has the reference to the existing table;
        on delete cascade / delete set null；
        ##意味着 存在依赖关系， 如果依赖z
```

### insert:

ALERT:  insert tuples that hash the **null value** or a value that **the same** as the existing ones for primary-key

will return FALSE 

```sql
insert into department
		value('Biology','West_2','50000.00');
		
insert into account
	select branch-name,loan-number,200
	from loan
	where where branch-name = "perryridge";
	#在account 里插入新的账户 whose branch name is ... (having loan number in,,,)
#还剩depositor 没有插入 此时为空 so now 
insert into depositor
	select customer-name,loan-number
	from borrower,loan
	where borrower.loan-number=loan.loan-number and branch-name = "...";
	
```



### delete

```sql
delete from students; ##delete all tuples from student relation
```

a more drastic version :  (drop off the relaiton as well , "delete" only delete the data but contains the relation student)

drop :

```sql
drop table student;
```



* delete from  删除一些tuples

  ```sql
  delete from account 
  where branch-name = "perryridge";
  
  delete from account
  where balance<(select avg(balance)
                from account);
  ```

  

## Alter

to add or drop attributes to an existing relaition.

all tuples  are assigned **null** in the new attributes after altering;



```sql
ALTER TABLE r ADD AD;## A is the name of attribute D is the type of the added attribute;
					# e.g alter table student add gpa numeric(3,2);
ALTER TABLE r ADD(A1D1,...AnDn)//alter table loan add loan_data date;
alter table r drop a;

............branch MODIFY(branch_name char(30),assets not null);

```

## update

```sql
update account
set balance =balance *1.05;
where...
```



* Create Index

  ![image-20220309104658916](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220309104658916.png)

  ![image-20220309104643512](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220309104643512.png)

## DML

### Select 

**1. from 2. where 3. select**

**1.** Generate a Cartesian product of the relations listed in the **from** clause

**2.** Apply the predicates specifified in the **where** clause on the result of Step 1.

**3.** For each tuple in the result of Step 2, output the attributes (or results of

expressions) specified in the **select** clause.

![image-20220330094751239](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220330094751239.png)

```sql
#Select 
#attributes("*"means all)
#from table
#where (constrain);

##################################################33
#distinct
SELECT distinct dept_name 
from instructor;#distinct means 去重

#all
select all dept_name# all means 不去重 保留即本来的样子 不加关键字默认为all
from instructor;


#operator 
select ID, name, dept name, salary * 1.1
from instructor;#+ - * / are all available to use

#where
select name 
from instructor
where dept_name ='Comp.Sci.' and salary >70000;# adding some constrain to the selection

#new name 
select A_name as B_name from.....;
select ... from T_name0 as T_name1; #注意这里也得考虑处理的先后顺序 不能再没有as T时就已经用了T
```

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220329203342287.png" alt="image-20220329203342287" style="zoom:50%;" />





**query on multiple relations  **

retrieve the names of all instructors , along with their department names and building names

```sql
select  name ,instructor.dept_name ,building #name and building only appears once so no need for the prefix
from instructor, department
where instructor.dept_name = department.dept_name;#simplification on the Caresian product

#######################################################
#which is natural join
#or:
select name, course id
from instructor, teaches
where instructor.ID= teaches.ID;
#This query can be written more concisely using the natural-join operation in SQL as:
select name, course id
from instructor natural join teaches;
#Both of the above queries generate the same result.

select name, title
from instructor natural join teaches, course
where teaches.course id= course.course id;
#first natural join then ",course"to generate the Cartesian product
#does not contain the same result as belows:
select name, title
from instructor natural join teaches natural join course;
#因为teach,instructor 外键只有ID 是唯一的所以二者的natural join 没有冗余
#而此时natural join 之后与course 的外键有course_id and dept_name so 将会只有 course_id 和dept_name 同时相同的results  而忽略了比如 教授不在自己部门下开设的课程(instructor 的 dept_name 与course 中的dept_name 含义不同)
#inorder to avoid this but still use natural join there is another key word called"join"

select name, title
from (instructor natural join teaches) join course using (course_id);
```

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220302213602078.png" alt="image-20220302213602078" style="zoom: 50%;" />

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220309105420160.png" alt="image-20220309105420160" style="zoom:67%;" />

**string operation**

```sql
’Intro%’ matches any string beginning with “Intro”. • ’%Comp%’ matches any string containing '%Comp%' as a substring, for example, ’Intro. to Computer Science’, and ’Computational Biology’.
’ ___’ matches any string of exactly three characters.
’ ___%’ matches any string of at least three characters
#转义字符 用在如果香查找带有“%”符号的东西时  前面加上"\" -> ;\%
```



**Ordering the display of Tuples**

```sql
select name
from instructor
where dept name = ’Physics’
order by name;#此时默认asc 可以用desc在后面 改为递减模式

```



* Set Operation

  union intersect except

  

  Union Intersect except will automatically **use distinct**;  or could use **tag "ALL"**to be un-distinct

  ```SQL
  (select name from deposit)
  union
  (select name form borrowers);
  #achieve "intersect"without using tag intersect;
  #如果一个人在银行拥有多个账户  可以使用(intersect)all来保证数据的完整性
  #比如找在银行同时拥有账户和贷款账户 intersect
  #有账户单无贷款的客户 except
  #账户 贷款or both 的客户 union
  ```

  

* Aggregate Function:

  **avg,min,max,sum,count**

  （avg sum 输入必须时数字）

  ```sql
  select avg(balance)
  from account;
  #出现的是一行数据 只有一行数字 mean average of all datas;
  select avg(balance)
  from account
  where branch-name ="Perryride";
  #输出只有一行 对应平均余额
  select branch-name avg(balance)
  from account 
  group by brach-name;
  #显示每个branch对应的balance average
  #having 语句 means  select 只对满足having 条件的物质处理
  
  ```

  ![image-20220329231556183](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220329231556183.png)

  

  ```sql
  SELECT A.branch_name, avg(balance) 
  FROM account A, branch B 
  WHERE A.branch_name = B.branch_name and 
  branch_city =‘Brooklyn’ 
  GROUP BY A.branch_name
  HAVING avg(balance) > 1200
  ```

  不能直接把条件写在where里 因为还没有进行分组 所以必须引入**having**关键字

  ![image-20220309111748502](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220309111748502.png)

  

  <img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220309115117286.png" alt="image-20220309115117286" style="zoom:67%;" />

  

* NULL value

  **null = null  return unknow**

  so select ......where amount **is** null  correct

### Nested queries嵌套式

in 是检验 是否在这个表里  not in 则是不在

```sql
#example  using tag"in"
SELECT distinct customer_name 
FROM borrower 
WHERE customer_name in (SELECT customer_name 
						FROM depositor);
#intersect
 SELECT distinct B.customer_name
FROM borrower B, depositor D 
WHERE B.customer_name = D.customer_name;#more efficient

#using tag "not in"
SELECT distinct customer_name 
FROM borrower 
WHERE customer_name not in (SELECT customer_name 
FROM depositor);

#using ""( branch...) in "to process partial nested queries;
                       
```

![image-20220329232744766](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220329232744766.png)

![image-20220330094615786](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220330094615786.png)

常量选择

**customer-name in （"Smith","Jones"）;**可以用常量来确定  customer-name ==Smith or Jones

* Set Comparation

**some** :<some <-some >=some  =some <>some （**仅仅是不等于一些 不等于not in**） **some means与其中一些相比**

**all**: means **与全部相比较**

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220309115602247.png" alt="image-20220309115602247" style="zoom: 50%;" />

```sql
select T.branch-name
from branch as T,branch as S
where T.assets>S.assets and S.branch-city="broklyn";
#or
select branch-name
from branch
where assets> some(select assets
                  	from branch
                  	where branch=city="brooklyn");
```



* 测试是否为空

  exists

![image-20220329234516726](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220329234516726.png)



判断语句 返回为1 则执行前面的select 语句  返回为0 则无动作。

先执行 select  --> exsists 后的判断从语句.

```sql
SELECT  *  
FROM user
WHERE
user.id IN (
	SELECT order.user_id FROM order
)
#########in 和exists 相同执行效果的语句
# in语句中 先查询子查询的表， 与外表做一个笛卡尔积 根据条件进行筛选
SELECT  user.* 
FROM user
WHERE
EXISTS (
	SELECT order.user_id FROM order
	WHERE
	user.id = order.user_id
)

```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190211111842381.png)user表

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190211111854581.png)order 表

第一个执行的是 SELECT order.user_id FROM order

得到 三个订单的user_id 值  

后与院user表做一个笛卡尔积 

根据 user_id = id 进行筛选， 能筛选过的就select



* 测试是否唯一 unique

![image-20220329235128493](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220329235128493.png)



### 派生关系

```sql
(select...)as resultname (relationname1 , RN2...);
```

```sql
select branch-name,avg-balance
from(select branch-name,avg(balance)
     from account
     group by branch-name
	)as result(branch-name,avg-balance);
where avg-balance>1200;
#找到平均账户结算>1200的
select branch-name,avg(balance)
from account
group by branch-name
having avg(balance)>1200
##########################最大平均值
select building
from university.department 
group by university.department.building
having avg(budget)>= (select max( )
		from
	(SELECT avg(budget) 
		FROM university.department 
		group by university.department.building));
```

```sql
with max_balance(value) as
	select max(balance)
	from account;#创建新的local 表
select ..
from max_balance,
```

### 组内连接



* 视图

  ```sql
  create view <view-name> as sq
  	(select.....)
  ```

## JOIN

inner join 不会新增null

outer join会

对于inner join，链接条件不是必须的  如果不加则是产生笛卡尔积  

对outer join 则是必须的



连接条件 on  loan.loan-number = borrower.loan-number  

​	或    者using (loan-number);

* inner join

  ```sql
  loan inner join borrower on loan.loan-number =borrower.loan-nnumber
  ```

  条件是在on里有相同的attribute 然后链接2个表 直接相当于贴在一起相加

  ![image-20220330003632947](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220330003632947.png)

  ![image-20220330003637212](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220330003637212.png)

* natural inner join

  ![image-20220330004950910](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220330004950910.png)

* left outer join

  先inner join 不匹配的在右边加上null

  ```sql
  loan left outer join borrower on loan.loan-number=borrower.loan-number;
  ```

  ![image-20220330004052902](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220330004052902.png)



```
SELECT a , b FROM test1
innner join 
SELECT a , b FROM test2

# 2.intersect

SELECT a , b FROM test1
intersect
SELECT a , b FROM test2
```



## Quel

### range of

每个元组变量在一个range of 子句中声明

```sql
range of t is r;
#t 是取自 Relation r的一个元组变量
```



### retrieve

retrieve 功能类似select 子句

![image-20220418192421609](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220418192421609.png)

### where

## 

## 

# 4.E-R Module

## 4.1Basic Concept

* 实体(entities)

  企业中每个人是一个实体  实体都有一组性质，有一部分为super key 

  ​														（e.g: social security for each person

* 实体集(Entity set)

  具有相同性质和类型的实体集合

  e.g: 某个银行的所有客户 customer

  ​		发放贷款的集合		loan

  ​		外延：实体集的组成个体  如customer 种的银行客户

  性质：彼此可以相交 employee 和 customer 可以相交

* 实体集 属性：

  将实体集映射到域种的函数，

  一个实体  可以由多个（属性：数据值）构成的集合来表示

  e.g" customer : 

  (name = tom ),(social-security = 677-89-9011),(cusromer-street = Main)...

* 简单属性 和 复杂属性

  简单属性不可拆分

  复杂属性可以拆分为简单属性 ：name -> first-name , last-name , middle-name

  ![image-20220409194224283](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220409194224283.png)

## 4.2 Realtional set

* 联系：

  多个实体间的关联 

  可以将客户hayes 和贷款 L-15 联系为：此人为改项目用户

* 联系集 

  同类联系的集合



![image-20220409195332776](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220409195332776.png)

如上图为borrower的实例 

customer 和 account 之间的联系集  is called depositor 可以将access - date 与该联系 关联起来 表示客户最新访问日期

## 4.3设计问题

用实体集还是属性

属性：

employee 由 telenumber , location 为属性

实体集

![image-20220409200611259](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220409200611259.png)

实体集更通用 因为可以表示一个employee 有 多个telenumber 或多人共用一个



实体集or联系集

联系集：

loan 可以不为一个实体 儿为 customer and branch-bank 的一个联系（relation)

这一联系具有描述性属性： loan-number 和 amount

如果每个贷款正好一个客户所有  且正好同一个分支结构联系 则联系即可以可以满足 。但不满足多人或多行share

所以不得不在relation  基础上添加decriptive 属性来约束



## 4.4 映射约束

### 4.4.1映射基数

映射基数：通过一个联系集能同另一个实体相联系 的  实体数目

e.g:

对于A与B实体集之间的二元联系集R来说 映射的计数

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220409201951142.png" alt="image-20220409201951142" style="zoom: 67%;" />



联系的基数中

一对一或者一对多的联系集的属性 **可以放到实体集**中 而不是联系集

![image-20220409202153026](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220409202153026.png)

多对多时 更适合联系集

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220409202426260.png" alt="image-20220409202426260" style="zoom:80%;" />

### 4.4.2存在依赖

如果实体x的存在 依赖于 y的存在 ：y删除 x也删除 

-> x **从属实体**  y **支配实体**

如loan 和 payment  中间有联系集 loan-payment （一对多）

每个payment必须和一个loan联系  如果loan被删除 所有与之联系的payment 也被删除

如果**实体集E**中每个实体都参与了**联系集R**中at least 1个联系 则说明E**全部参与**联系集R   其他还有 部分参与

如此时的payment 与loan-payment 为全部参与



## 4.5码 key

### 4.5.1 for entity set

**超码** super key 帮我们在实体集中 唯一标识一个实体

social-number could be

(social-number and customer-name )组成的entity set （S1）也 could be

此时叫做 **超集**



**候选码** candidate key

为最小超集  

如S1 就不能为candidate key cuz 他的子集social-number 已经为超码



**主码** primary key 设计者选中的 候选码

## 4.5.2  for relational set

假设R是一个涉及 E1 E2..En的联系集 而primary-key(Ei)标识构成实体集 Ei 主码的属性集合

①没有descriptive attribute for Relation

![image-20220409205523293](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220409205523293.png)

②如果有 a1, a2,...,an 

![image-20220409205556569](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220409205556569.png)

而in both cases 第一个primary-key （Ei）的并集  都可以为 Relation的 **超码**

## 4.6E-R 图

![image-20220529210603289](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220529210603289.png)

![image-20220529210610710](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220529210610710.png)

* 矩形 Entity
* 椭圆 attribute
* 菱形 relation
* 双椭圆 多值attribute
* 虚椭圆 派生attribute
* 双线 标识一个实体 全部参与 联系集中

![image-20220409205950224](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220409205950224.png)

![image-20220529205258645](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220529205258645.png)

![image-20220409210624708](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220409210624708.png)

## 4.7 弱实体集合 weak entity set

有primary key 强实体集

无------------------弱实体集

区分弱实体集的 ---  **分辨符**

如payment ---payment-number(不同付款可以由相同付款号)

弱实体集的主码 由 由wes 所依赖的ses的 **primary-key**+  分辨符组成

the primary key of payment: {loan-number,payment-number}



E-R 图中

wes 用双边框矩形标识

对应联系用双边框菱形  联系集是没有任何描述性属性的

![image-20220409211557289](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220409211557289.png)

## 4.8extended E-R feature

### 4.8.1 特殊化

* 特殊化和概括

account 可以衍生为 

saving-account 

checking - account

each has some attribute that  doesn't share with other entity sets

e.g: savings-account 可以由interest -rate 进一步买哦书

​		checking-account 可以由overdraft-amount 进一步描述

​	此过程称为 **特殊化**



通过ISA 三角形构件标识 每个子实体集 有子集独有的attribute链接

![image-20220409212140283](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220409212140283.png)

![image-20220529205655895](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220529205655895.png)

**概括**则是特殊化的反过程 为 给不同实体集 找相同点 最后 形成父类的过程

（自下而上）



* 属性继承 

  完全继承： 所有的高级attribute 都有一个对应 低级的

  部分继承   some 有对应 some 没有

  

* 约束涉及

  约束哪些实体能称为低层实体集 的 成员

### 4.8.5 聚集

将联系集和实体集 看成一个整体 高层实体 

![image-20220409213052838](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220409213052838.png)

## 4.9 设计E-R模式

![image-20220409213347171](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220409213347171.png)

![image-20220409213434961](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220409213434961.png)

## 4.10 将E-R模式转化为表

* 强实体集

  用table来表示

  ![image-20220409213532294](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220409213532294.png)

* 弱实体集

  用依赖的实体集主码 +子集的属性来标识

  ![image-20220409213715898](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220409213715898.png)

* 联系集

  由①primary-key(Ei)②decriptive-attribute 并集组成

  ![image-20220409213830927](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220409213830927.png)

* 表的冗余

  在联系强弱实体集的 联系集 没有描述性属性

  而wes的主码 又包含 ses的主码 如loan-payment table有2列

  ​														loan-number and payment-number

  与payment表冗余了  因此在用表标识ER图时不必给出

* 表的合并

  如果A对B存在多对一的联系集 且 A对B存在依赖  可以将A和AB合并乘一个表

  ![image-20220409214617393](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220409214617393.png)

![image-20220409214621841](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220409214621841.png)



* 多值属性

  multi-value attribute

  必须创建新表

### 4.10.1 用table概括

①为高层建一个表 每个低层实体建一个表

![image-20220409214920938](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220409214920938.png)

②如果概括时不相交且全部的

即2个低层实体集直接隶属于同一个高层实体集，（高层的每个实体必然是低层实体的成员）

不必建立高层实体

![image-20220409214940382](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220409214940382.png)

### 4.10.2 用table表示聚集

![image-20220409215323846](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220409215323846.png)

![image-20220409213052838](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220409213052838.png)

### 4.10.3 reduction

多值attribute 新建表 （如email 为多值 则新建表 studentemail(address,student-name);

each 关键词 记得用完全参与

弱实体集合 的Realationship 不必画  ||关系可以合并简化: wes 的table里包含自己和依赖的primary key

复合表：比如name(first-name,last-name) 可以直接合并入customer里

关系建表：包含的是每个参与关系的外键

多对一的关系中：可以把“一”的primary-key放进“多”的table里 省去对关系的建表

如果只是部分多对一：

![image-20220413105910457](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220413105910457.png)

可能会导致有NULL value 的存在

![image-20220413091813611](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220413091813611.png)

# 5.完整性约束 constrains

## 5.1 create中

```sql
create domain account-number char(10)
 		constraint account- number-null- test check (value not null);
 		
```

## 5.2 触发器trigger

一条语句

当数据库倍修改，则被系统自动执行，须满足2个需求

1）触发条件

2）出发的动作

e.g: 当银行的account 小于0，此时不是将其变成负数的余额，而是将其归零，并新建一个loan账户

```sql
define trigger overdraft on update of account T
(
	if new T.balance < 0
    then (
    		insert into loan values	( T.branch-name, T.account-number, - new T.balance)
        	insert into borrower (
            						select customer - name, account-number
                					from depositor
                					where T.account-number = depositor. account-number
            					)
        	update account S
        	set S.balance  = 0
        	where S.account-number = T.account-number
    	)
)
```

# 6.存储结构

主要存储在磁盘存储器上

为了能访问到数据 必须从磁盘移动到主存储器上

被修改过的数据 必须协会磁盘

## 6.1磁盘

1.**性能度量标准**  

容量 存取时间 数据传输率 可靠性

- 存取时间 
  - 平均寻道时间  基于一系列的随机请求衡量得到的
  - 旋转等待时间  等待磁盘转到读取头下

2.**存取的优化**

文件的I/O请求 由文件系统  和 虚拟内存管理器产生

请求指定要存取的磁盘地址  （以块号的形式提供  -- from 512bytes to several Kbs);

- 调度

  按照某些顺序法储存取块  节约时间

- 文件组织  

  减少存取块的时间   

- 非容易失去性的 写缓冲区

**3.RAID**

- 通过冗余提高可靠性

  使得需要使用的磁盘空间增加 导致有效信息的磁盘损坏率减小

- 通过并行提高性能

  在多个磁盘上对数据进行拆分来提高传输速率

- RAID级别

  - 0级 - 5 级

## 6.2**存储访问 ** 重要

每个文件被氛围定长的存储单元  称为块，存储分配和数据传输的基本单位

减少磁盘和储存器之间的块数目 

减少磁盘访问次数的方法之一  在主储存器中保留尽可能多的块

在主储存器中用于储存磁盘块的拷贝部分  -----缓冲区

* 缓冲区管理器

  根据数据库的需求 来安排空间来保存需要的块 并将主储存器中的地址 传送给请求者

* 缓冲区的替换策略

  减少对磁盘的访问  

  通常利用过去的块访问来语言未来的块访问 

  因此 如果替换一个块 通常替换最少访问的块 ----**LRU块替换策略**

  在立即丢弃策略中使用该策略  会有如下弊端

  ​	弊端：下一个接着要被访问的块 为最少访问的块  （意味着可能会被去除）

  因此替换为  **MRU 最近最长常用策略** 

  系统必须把正在处理的customer块钉住  在最后一个customer 元组处理完毕后 这个块就不被钉住

## 6.3文件组织

- 定长记录

  在文件的开始处 分配一定数量的字节作为文件头  包含有关文件的各种信息

  - 存储被删除的信息地址1
  - addr1 用来存储 可用的地址addr2
  - so on 形成一条链表

  所以在插入时  先找到文件头指向的可用记录 并改变文件头的指针 指向下一个可用的记录 如果没有则将记录加在文件末尾

  为了避免有被指向的 记录  被删除  （虚悬指针）我们将其钉住

- 变长记录

  将account-info 定义乘一个有任意多元素的数组

  ①字节流表示

  在每个记录的末尾加上特殊的记录终止符号（上）

  不足	

  - 重新使用被删除的空间困难 
  - 通常如果一个记录变长了   那么就必须移动  如果该记录时stick 则代价更大

  **②分槽的页结构**

  有一个块头  记录着

  - 块中记录的条目个数
  - 块中空闲空间的末尾地址
  - 一个 array containing 包含 记录的位置和大小 的记录条目

  块中的空闲空间是连续的

  插入 将在空闲空间的尾部给这条记录分配空间 并且将这条记录的大小和位置加到块头

  删除 空间被释放 条目置为删除状态（size = -1)  并移动该记录之前的记录  使得空闲空间连续

  ③定长的表示方式

  * 保留空间 设置一个永远不会被超过的最大记录长度

    ![image-20220520004441579](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220520004441579.png)

    造成冗余

  * 指针 变长记录用一系列通过指针连接在一起的定长记录表示

    分为 锚块 链表中第一个记录的块

    ​		溢出块	其他

    ![image-20220520004452373](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220520004452373.png)

# 7.index and hash

## 7.1basic concepts

数据量大的时候用才有效

![image-20220520085543031](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220520085543031.png)![image-20220520090000037](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220520090000037.png)

Search Key 是用来查找数据库记录的属性集合。

index是由一个个index entry组成的，每个entry由两部分组成：search key和pointer <K(i),P(i)>. 。pointer就是指向对应search key数据块地址的指针。

根据是否按照search key的顺序存储，可以将索引分为有序索引（ordered indices)和哈希索引（hash indices)。

基本的索引有

- 顺序索引
- hash索引

考虑要使用哪种索引方法要考虑如下因素

- 访问类型
- 访问时间 访问一个或多个数据 需要的时间
- 插入时间
- 删除时间
- 空间开销  索引结构需要额外的储存空间   如果较小 那么用空间换时间是值得的

## 7.2Ordered indices

如同图书馆目录一样

每个索引结构有一个特定的搜索码与之关联 

索引按顺序存储搜索码的值 并将搜索码与包含该搜索码的记录关联起来

一个文件可以有多个索引 对应不同的搜索码

如果包含记录的文件按照某个搜索码指定的顺序排序 那么该搜索码对应的索引称为主索引（也称聚集索引）

- 主索引

  在某个搜索码上有主索引的文件为索引顺序文件

  如 此时按照brach-name为搜索码

  

  ①稠密索引 search key对应的每一个值 都有一个索引记录（index entry）

  ②系数索引 并不是全部的search key 都有

  ![image-20220520091040470](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220520091040470.png)

  如图就只有3个search key 有 index entry

  ③多级索引

- 索引的更新

  - 删除 如果要删除记录的search key 在文件中是唯一的 那么该search key 要从index 中删除

    在sparse indix 中 可以将（按搜索码顺序）下一个搜索码值替代该搜索码

    如果下一个search key 已经有index entry 那么该search key 就直接被删除

  - 插入 首先搜索待插入记录的搜索码是否在index中

    如果不在 那么就插入index 

    如果索引是为每一个块 保存一个 index 的sparse index  之哟啊没有新快产生 则无需改动  如果有 则把块的第一个search key 插入index中

- 辅助索引

  ![image-20220520092120860](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220520092120860.png)

  必须为dense index

## 7.3B+ Tree Index Files

每个叶节点为一个block 都是4k bytes

num of entries on each node  == N

leaf node [(n-1) / 2] ---- n -1 points

inner node [n/2] n points

拥有子树从[n/2] --> n棵

在非叶子node 中 p1指向的子树所有search key 小于 K1

在其他的Pi 指向的subtree上都>=Ki-1 小于Ki

所以height = [log [N/2] (num of record)] 向上取整;

![image-20220603163940281](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220603163940281.png)

![image-20220520093208440](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220520093208440.png)

定义： 

节点结构： 包含n-1个search key 和n 个pointers

每个叶节点最多可拥有n-1个search key 允许最少为(n-1)/2 且 均互不相交

leaf node contain at lest (n-1)/2 value 不向下取整  n == 4 至少右2 个values

B+树非叶节点至少包含 n/2个指针  最多包含n个 （除了根节点）

除非只有一个节点 那么根节点必须index 数量 >= 2  且 可以 < n/2;

查询

搜索key = k的所有记录

首先root上找到大于k的最小搜索码值 走到下一层的对应节点上

![image-20220520101443270](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220520101443270.png)

到叶节点后 小于等于的只能往左子树走 然后找到没有相等的  后  不能直接判断没有  需要往右边走一条 

①更新

插入树时：

①insert in sorted order 在插入前先排序 再插入

新建树时

②bottom up B+

 ![image-20220618021011667](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220618021011667.png)

cost 

block num  Tt

1 Ts

合并时

old one bk + estimated new one bk Tt

2 Ts

- 插入

  先使用和查找一样的技术 先找到被插入的搜索码应在的叶节点，

  if已经存在 

  ​	插入record to file  如果必要在文件中对应的bucket 

  else 

  ​	add record to mainfile (create a bucket  if necessary)

  ​	在叶节点中加入

  ​	if there is room  直接 insert pair<key-value, pointer>

  ​	else split the node to the next slide then insert

  ![image-20220520104501522](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220520104501522.png)

  - split

    把中间的pointer 拆分 后新建一个block 再向上找是否满 未满就直接加入一个 pointer和searchkey 指向 这个block 

  - 对于非叶节点的split

    不需要先分再网上更新  直接将最后的值网上移动  再新创建一个block 

    因为新建的block 会有最左边的pointer  所以无需再把其中一个value移动到新的block里 直接网上移动就行 再建立心得pointer 指向该non-leaf node;

  

- 删除

  无法合并就只有 redistribute

  ![image-20220520114118219](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220520114118219.png)

  ![image-20220520114050229](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220520114050229.png)

  ![image-20220520114112019](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220520114112019.png

​			

## 7.4Write-optimized indices

LSM （lg structured Merge Tree);为了写优化的

consists  of several B+ trees

- insert

  first write into the B+ tree in memory 

  if the b+ tree is full 

  (then L0 is written into disk )

  ​	if(B+ tree in disk is empty)

  ​		create the initial tree L1;

  ​	else

  ​		leaf level of L0 is scanned in increasing key order     -----> merge with leaf level of L1(scanned the same way)

  ​		create a new b+ tree and replaced the old L1

  ​	(using **bottom up** )

  delete old L1 and L0;

- query

  bloom filter

  一个0/1数组 

# 8.Query Processing

overview

![image-20220530114001550](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220530114001550.png)

- find out various equivalent relational algebra

  ![image-20220530114245693](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220530114245693.png)

- 

nr  num of record

br num of record

lr size of a record

fr num of the records that a block can contain

V(A,r) 关系r中的 属性A 所具有的不同值得数目

SC（A，r） 是满足选则条件的记录数

## 8.1 measure of query cost

**cost = Disk access **+ CPU + net workcommunication

- Disk access

  - Num of seek operations performed
  - Num of blocks read * avg cost
  - Num of blocks written * avg cost

  for simplicity  use **Num of blocks and Num of seeks** to mesuere

  cost = b*tT + S * tS;

## 8.2 selection operation

① File  scan  search for algoriths 

②Algorithm

- A1 Linear search

  每个文件块均被扫描看它是否满足条件 Ea1 = br

- A2 binary search

  前提： 该文件按照某一个attribute 进行排序 且 连续存放

  

  Ea2 = [log2(br)] +[SC(A,r) / fr] - 1

  第一项是对第一个元组扫描的代价

  第二项是相同的属性值占据的block数目 - 1 是排除掉最开始搜索到的block

  

​	![image-20220530121608670](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220530121608670.png)

index searching

index 一定要在 attribute上件索引

index 可以为null 但是不重复

- A3(main index, key attribute)

  retrieve 1 record

   Cost = (hi + 1) * (tT + tS )，其中 hi 为索引树高

- A4(primary index, non-key attribute)

  retrieve multiple records(index 唯一 record 不唯一 但是聚簇排列 所以还型)

  ![image-20220530134551484](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220530134551484.png)

  b = num of blocks containing matching records = SC(A,r) / fr;

  Cost = hi * (tT + tS ) + tS + tT * b,

  只寻一次地址 就是最后一次

- A5(secondary index, equilty on nonkey)

  candidate key record 非重复 就只有一个值

  非candidate key

  n 为 bucket 中的值

  ![image-20220530125257191](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220530125257191.png)

  ![image-20220530134959700](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220530134959700.png)



如果没有bucket 中的重复元素没有很多那么代价还行  但是如果像一个学校中的学生年龄这样的attribute（重复性高） 就还不如linear search

selections involving

- index

- A6（primary  index comparison)

  ➢ For A  V (r), use index to find the first tuple A  v and scan relation sequentially  from there.  

  ➢ For AV (r), just scan relation sequentially till first tuple A>v; do not use index

  因为是聚簇的 所以直接从头开始找就行 就是linear search ，找到等于的停止就行

- A7(secondary index comparison)

conjunction

- A8（conjunctive selection, one index)

  ➢ Select a combination of I , and algorithms A1 through A7 that results in the least  cost for i (r). (第一步从n个条件1 … n中选择代价最小的i先执行，返回元组放内 存，然后第二步对这些元组施行其他i .）

   ➢ Test other conditions on tuple after fetching it into memory buffer.

- A9(conjuctive selction ,composite index)

- A10(conjunctive selection, intersection of idextifiers)

## 8.3 join

most important

- nested loop join

  2重循环

  从r s中直接2 重循环

  nr * bs + br Tt  每一条record 外层   内层都要一个block 来匹配  然后外层只transfer 一次block

  nr + br seek （移动磁头， 因为s中为连续排列 所以不算seek  所以对应调整r block 时有br次）

  ​						调整 到s的头头时有 nr 次

- block  nested- loop join

  ![image-20220530140639508](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220530140639508.png)

  (Br * Bs + br)  Tt + 2 * br  Ts（因为里面2重循环时CPU的时间 ，无需考虑）r为外关系

  ①外层读 br次  内层s 读入 br * bs 次，Tt

  ②seeking  调用br 时 br次+每次调用block s时 调到s头头 需要br次  

  

  

  启发： 小的放外层循环

  如果M> 3:

  如果一共只有M块block 在内存中

  M-2给外层  1 个给内层 1 个时缓存（output）

  Data Transfer cost = [br / (M-2)] * bs + br 

  Seeks times= 2 *br / (M-2)

  

  如果 Ｍ>br 直接就是最佳的

  br + bs Tt   

  2 Ts

- Index Nest index join

  对每个tuple r 用index 来找到对应的 tuples in s that 满足条件

  最坏的条件

  br(transfer + seek) + nr * c ;

  nr为r的record数目

  c为最佳的找到等于r.val 的tuples in s using index equity search

- Merge join

  br + bs block transfers + [br / bb ] + [bs / bb ] seek

  +cost of sorting

  （排序一个r的时间是 br *(2[logM-1(br / M) ] + 2); 那么2个都要排序完毕)

  

  if the buffer memory size is M

  br + bs  + cost of sort Tt

  [br/xr] + [bs/xs] Ts

  (xs + sr = M);

  - hybrid merge-join

    (一个已经按照顺序存储 另一个有以可secondary B+树再join attribute 上)

    cong B+树种从头到尾（算是已经sorted）

    ➢ Merge the sorted relation with the leaf entries of the B+ -tree.  

    ➢ Sort the result on the addresses of the unsorted relation’s tuples 
    
    ➢ Scan the unsorted relation in physical address order and merge with previous  result, to replace addresses by the actual tuples 

- hash join

  <img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220530185537741.png" alt="image-20220530185537741" style="zoom:50%;" />
  
  each si should fit in memory size(block)
  
  h and n should make every si block fit on memory size;
  
  ➢ Typically **nh** is chosen as **bs /M** * f where f is a “fudge factor”, typically  around **1.2**
  
   For each i: 
  
  ​	(a) Load si into memory and build an in-memory hash index  on it using the join attribute. This hash index uses a  different hash function than the earlier one h. 
  
  ​	(b) Read the tuples in ri from the disk one by one. For each  tuple t r locate each matching tuple ts in si using the inmemory hash index. Output the concatenation of their  attributes
  
   
  
  是否需要迭代哈希
  
  ![image-20220530191909630](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220530191909630.png)
  
  M  > nh + 1
  
  M > (bs/M) + 1
  
  M >根号bs
  
   ![image-20220530192553475](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220530192553475.png)
  
  ![image-20220530192612975](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220530192612975.png)

# 9.Query  Optimization

## 9.1intro

cost-vased query opt:

- generate logically equivalent expressions
- anaotate resultant expressions oin alternative way s to get alternatives query plans
- choose the cheapest plan based on estimated costl

based on:

- num of tuples , and  SC(A,r);

## 9.2 trans on relational expressions

equivalence Rules:

①Conjunctive selection <--> sequence of individual selections

![image-20220530194747654](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220530194747654.png)

②交换顺序 选择

​	![image-20220530194840514](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220530194840514.png)

③可忽略的

![image-20220530194914684](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220530194914684.png)

④笛卡尔积再选择 可以变成  相等join

![image-20220530195047203](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220530195047203.png)

⑤交换顺序 join

⑥![image-20220530195150631](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220530195150631.png)



⑦

a

![image-20220530195809791](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220530195809791.png)

大多数先select再join有利

在θ0在E1上没有index时不利 

b

![image-20220530195910512](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220530195910512.png)

⑧projection 可分配 先连后投 = 先投后连

![image-20220530200444612](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220530200444612.png)

![image-20220530200519800](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220530200519800.png)



⑨并和交可交换

⑩单独并 单独交的多项式 可结合

11

![image-20220530201525895](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220530201525895.png)

### 9.2.1 pratical rules

**performing selection projection 早些**

- 中间的projection 有时需要保存外部需要的和join需要的

  ![image-20220530202233918](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220530202233918.png)

join的中间值要小一些

## 9.3 cost estimation

![image-20220530203514655](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220530203514655.png)

仅仅在查询优化时才更新上述数据  不是插入一次九更新

- selection estimation

  ​	nr / V(A,r);

  c = nr * v - min / max - min 相当于均匀分布的概率 * 总数

- complex seletion

  ①满足条件θi 的概率为 满足条件的个数si / 总数nr

  ②Conjunction

  nr *概率1 * 概率2 * 概率3.。。。。

  ![image-20220530204900047](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220530204900047.png)

  ③disjunction

  ![image-20220530205019003](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220530205019003.png)

  ![image-20220530205013154](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220530205013154.png)

- join

  ①没有公共属性  

  与 笛卡尔积一样

  ②有一个公共key for R

  S中的tuples最多join到R中的1个tuple

  ​	大小 <= ns

  

  ③如果有外键R在 s中 references r那么

  ​	==ns

  ④R ∩ Ｓ＝｛A｝不是任何一个的key

  先计算平均每个r 有多少个s会join  ns / V(key,s)

  再乘上nr

  前者：如果每个tuple in R 都produce tuples in R交S

  后者：                              S 。。。。

  ![image-20220530205836601](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220530205836601.png)![image-20220530205840573](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220530205840573.png)

  更小的那个可能时更精确的

- projection V(A,r)

- Aggregation V(A,r) 

  在A上group by

  ![image-20220601100355519](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220601100355519.png)

- outer join

  ![image-20220530210410754](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220530210410754.png)

  能连接上的 + 不能连接上的

- distinct value

  ![image-20220530210710029](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220530210710029.png)

  join 的 distinct value

   ![image-20220530210853283](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220530210853283.png)

  ![image-20220530212406228](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220530212406228.png)

  projection 的 V

  ![image-20220530212824164](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220530212824164.png)



# 10.Transaction

## 10.0concept

- concurrent excetions 
- failure of various kinds

e.g 同时有2个售票员在出售同一个车次的车票

- Transaction  is a unit of program execution that accesses and  possibly updates various data items.

   

  Usually a transaction is of a number of SQL statements, ended with commit（提 交） or rollback（回滚）statement. 

- Properties（**ACID**）

  - atomicity

    要么都正常执行要么都不执行

  - consistency

  - isolation

    用户无法体会到正在并发执行的其他transaction

  - durability

    transaction 完成后 即使有failure 所产生的数据也会永久存在在database 里

  e.g:

   Transaction to transfer $50 from account A to account B: 

  1. read(A) 
  2. A := A – 50 
  3. write(A) 
  4. read(B) 
  5. B:= B + 50 
  6. write(B)

  - Atomicity :

    如果在3 后 6 前 fails 那么此次的transaction全部将不会更新在database中

  - durability

    一旦当50 转账成功了那么update to the database by transaction 必须存在 及时有failure

  - consistency

    the sum of A and B 不变 在transaction 前后

    During transaction execution the database may be temporarily inconsistent

    when it completes the database must be consistent

  - isolation

    如果在3 - 6 之间有另一个transaction T2 正在进行并处理database

    如read (A) read(B) print(A+B) 则会看到此时的sum 会小于 usual

     

    isolation can ensured  transaction 一个一个的按顺序进行

## 10.1 Transaction state

- Active 

  最初始的状态  ，在开始执行时

- Partially committed

  在最后一个statement 被执行之后 （此时结果可能还在buffer中）

- Failed

- Aborted

  在transaction 被roll back ，database 回transaction 执行前的咋混柜台

  **2 optiions after Abortion**

  - Restart the transaction
  - Kill the transaction

- Committed

  在成功之后

![image-20220531034030740](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220531034030740.png)

## 10.2 implementation of Ato and Dur

support: **recovery - management  component** of a database sys 

- shadow - database

  simple but inefficient

  a ptr **db_pointer** always points to **the current consistent copy** of the db

  - all the updates 被建立在一个新的db copy上

    the original copy --- shadow copy 并没有被触碰（被db_pointer 指着）

    如果aborted 直接删除new copy

    如果committed  ①将所有的page在new copy中 送到 disk中

    ​								② dp_poiter 改变到指向new copy 并将old copy 删除

  **必须保证**： 无并发的transaction ， 假设disk不会fail， 

## 10.3Concurrent Executions

① schedules

sequences that 表示并发的transaction以那种顺序被执行

- 必须保持指令在各个transaction中的顺序	不被改变

第一种  serial schedule

第二种concurrent schedule

![image-20220531035949105](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220531035949105.png)



## 10.4Serializability

基本前提： 所有的transaction 都保持database 的consistency

只考虑read write 操作

① conflicting Instructions

只有同时read一个Item不conflict 其他对同一个item操作都conflict

如果2个instruction 时连续且不冲突 那么 交换 不会影响结果

![image-20220531043000684](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220531043000684.png)

②view serializability

满足对所有的item Q

首读1 in S ,Ti reads initial value Q, in S' also Ti must read initial value of Q

写读2 in S Ti read(Q), (was 被Tj产生的)， 在S'中也必须Ti read(Q)被Tj产生

末读3 都有执行最后的write (Q)

## 10.5 recoverability

可回复的调度： Tj 读了 在Ti中写的item， 那么 Ti必须在Tj前commit

- Cascadiless Rollbacks

   Ti and Tj such that Tj reads a data item  previously written by Ti , 

  the commit operation of Ti appears before  the read operation of Tj .

## 10.6 独立性实现

- schedule 必须是 conflict or view serializable and recoverable 
- Concurrency-control schemes tradeoff between the amount of  concurrency they allow and the amount of overhead that they incur. - --- Chpt18

## 10.7 Transaction DDL in SQL

 A transaction in SQL ends by: 

➢ Commit work commits current transaction and begins a new one. 

➢ Rollback work causes current transaction to abort.



## 10.8 可串行测试

有环路不可串

else：

拓扑结构：标准 t之间有冲突操作  并且先 指向 后

![image-20220531045647825](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220531045647825.png)

然后就按照拓扑排序来进行就行

如此时T5 可以在任何时间进行 T2 T3 必须在T1之后执行

# 11.Concurrency Control 

## 11.1Lock

1)exclusive Lock

如果事务Ti 获得了 Q上的（X）则Ti 即可读又可写Q

2)shared lock

如果获得了Q上的（S） 只能读 不饿能写Q

每次操作前都要申请Lock  申请到了才能的到操作

X能和X相容 但是其余都不相容

①不相容的锁必须等到the other one is released 才能申请



1. 基本的两阶段transaction

   保证了**conflict-serializable**

   事务释放锁之后就不能申请锁了

   ①	增长阶段

   ②	减少阶段

   ![image-20220531205433561](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220531205433561.png)

   ![image-20220531225003676](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220531225003676.png)

   1.1如果 Ti --> Tj

   那么LP(Ti) < LP(Tj);(point that apply for the lock)

   所以遵循lock的transaction都可以串行

   <img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220531223757734.png" alt="image-20220531223757734" style="zoom:50%;" />

   可以按照lock point 顺序来进行schedule 从而遵从了可串行化

   

2. 拓展

   保证recoverability 和 无 cascading roll-back

   ①strict 严格的2阶段封锁

   一个transaction必须hold all X locks till commit/abort

   ②rigorous强2阶段封锁

   hold all locks till commit / abort

3. 2阶段协议 为 可串行的充分非必要条件

   ![image-20220531231259802](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220531231259802.png)

   此时并没有遵循2阶段分所协议但是还是可以进行

4. Lock conversions

   两阶段锁with 锁交互

   - 阶段一

     可acquire 一个S or X 锁

     可convert S--> X;升级

   - 阶段二

     可release S or X

     可convert X --> S降级

## 11.2 Lock implement

![image-20220531235423809](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220531235423809.png)

Lock Table

![image-20220531232513308](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220531232513308.png)

有一个链表在lock 上表示正在运行或者等待的transaction

①lock

​	先hash 找到对应的数据项

​	如果没有对应的  就直接新建一个lock 地址

else  。。。

②unlock

## 11.2 deadlock Handle

循环的等待（前序图有环）

处理：

1.prevention

①non / all lock can be greanted

​	先把一个transaction锁需要的所有的lock 给到lock manager 进行判定是否可以全部获得

②lock data items only in the order

基于 顺序

2.timeout-Based schemes

 如果transaction 等待lock 超过了一个限定的时间就直接roll back

可能产生**starvation** 老是得不到该Q数据(当该transaction 总是被选择当作victim来rollback 是)



3.detection on deadlock

根据lock table 构建一个新的wait graph

Ti ---> Tj意味着Ti 在等待这Tj的锁

检测里面是否有环

4.Deadlock Recovery

选择transactioon as victim that will incur minium cost

rollback 

- Total  : Abort it and restart it
- Partial: only as far as necessary  ot break deadlock

 

## 11.3 **partial ordering**

避免保持lock 时间过长

但是保证了可串行和free of 死锁



graph protocol

- tree-protocol

  ​	只有x锁

  从任何一个节点开始都可以

  如果要加lock  在node 上 呢么在node的父节点必须是locked状态

  

  并不能保证可恢复性（recovery）

  - 需要接入commit dependencies：

    如果T1 读了最后为T2写 的数据 那么必须T1 在T2 上加了一个T1的 cd ， 必须T1先commit T2才commit

    一个T1 必须全部加载在其他T上的 T1 cd 的T被commited 了才能commited

    如果其中一个abort了那么该T也必须abort

    

## 11.4 Multiple Granularity

越上层 颗粒越粗

![image-20220601003807326](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220601003807326.png)

粗粒度的锁无法上锁 如果其细粒度子node已经locked

- 必要引入： **intention  Lock Modes**

  Intention locks are put on all the ancestors of a node before  that node is locked explicitly.

  ![image-20220601004404242](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220601004404242.png)

  ![image-20220601005414852](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220601005414852.png)

  相容性：

  ![image-20220601004532848](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220601004532848.png)

  在一个node 上要做lock时候注意父节点是否已经在正确的 intention lock mode

  SIX 下可以有IX

  需要是 S / IS mode 那么 parent 为IS / IX

  需要时X / SIX / IX 那么parent IX / SIX

# 12.Recovery Sys

## 12.1 failure classification

![image-20220601011750152](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220601011750152.png)

transaction 记录日志 

sys crash

disk failure 备份

回复操作

①action during normaltransaction processsing （日志以及备份）

②action taken after a failure to recover and to ensure ACD

严格两阶段锁协议 保证了没有dirty read

idempotent（幂等性）：做n次recover都跟做一次一样

（防止在recover 中发声failure）



## 12.2 Log Based Recover

如何记好日志

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220601013223247.png" alt="image-20220601013223247" style="zoom: 80%;" />

X为广义的，可以是value 也可以是一个地址或者else

V 可以是NULL V1为NULL 表示插入  V2 为delete

其他还有<T,commit> <T.abort>

先写log 再 update

观察是否已经commit 如果已经commit 那么就直接重新做（可能reflect 也可能中途crash）

​																										而重做也没有风险

如果没有commit 放到undo list

如果碰到了Ti commit 就把之前的对应Ti的undo list 清空

直到没有commit，把有余量的undolist 进行undo 操作

记得是从再undo list 中从后往前做

然后最后后加上<Tj, abort>;

![image-20220601014842123](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220601014842123.png)



redo T3 T1 undo T2 T4

到绿色之前发声crash

- Transaction Commit

  一个transaction被标记为committed 当提交日志被放到stable storage 中（且前面的log也已经commited完毕

  此时可能performance还在buffer中

  

- Check points

  将main memory中的log record清空，放入stable storage

  将buffer blocks 放到disk中

  在checkpoint 前的已经commit or abort的Ti in 前一个checkpoints的L  都可以从L中去除

  如果crash了，那么就找到最后一个checkpoints L 

  - 如果出现  Ti commit or abort 那么就redo Ti
  - 其他的undo就行
  
  
  
  从end往上scan 到checkpoint停止
  
  1.碰到 Ti commit 添加到redo-list
  
  2.碰到start且没有commit 或者 碰到abort 放到undo-list
  
  碰到checkpoints之后 L里的Ti查看是或否已经commit 如果已经commit 就不必考虑，其他的放入undo-list 
  
  - undo
  
    但凡在undo list 里的T 的操作  都做一个物理的rollback
  
  



**recovery**



①out put all logs in main memory into stable storage

② output all modified buffer blocks to disk

③write record<checkpoint L>  L 是一个表记录着所有活跃的transaction再记录时

（活跃意味着还没有提交）

所有update都要停止 当checkpointing时

![image-20220601021659020](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220601021659020.png)



如果突然发声了failure 那么从checkpoints开始repeating就行了

undo list 继承checkpoints的L

边repeat边检查是否有T commit abort则删除T from undo list 

碰到start  就添加一个进取undo list



recovery from concurrent Transaction （遵循严格2PL）

- redo

  从transaction开始

  repeate每一个instruction，使用物理重做

  没碰到一个start就加紧undo list

  没碰到一个commit abort 就从undo 中删除

- undo

  如上面

三阶段的recovery

​	逻辑日志 Logical Unodo Logging

​	在每一个operation end 后 加上一个恢复的操作提示

​	在需要abort时，

​		如果此时operation没有结束，那么利用物理操作进行重置

​		如果已经完成了operation 那么就进行提示的恢复操作





## 12.3 Buffer

- Log Record Buffer

  log record 先被存放在 main memory 中
  
  - 1 block 满了
  
  - 2 log force operation 像checkpoints 时
  
    则组成blocks 放到 stable storage
  
  4rules:
  
  - 按照他们被created 的顺序输
  - 当<Ti commit> 进入stable storage 则 Ti 进入commit state
  - 在Ti commit 进入stable storage之前，其他与Ti有关的records必须先到stable storage
  - 日志先于数据写道磁盘中
  
- Database Buffer

  - 恢复算法支持 no-force policy

    如 已经updated 的block不需要再被写入disk when it commits

  - 恢复算法支持stral policy

    如含当blocks中的transaction没有被commit ，也可以写入disk

  - 如果rule2中情况发生，那么就要写如undo info 进入log stable storage

  - 再写入disk过程中不能有update 发生

- 如何 output a block to a disk

  - 需要一个exclusive latch on the block

    保证没有update in block

  - log flush

  - output to disk

  - relase the latch on the block



## 12.4Failure with Loss of Nonvolatile Storage

**Fuzzy Checkpoints**

- 暂时的暂停所有update
- 直接写一个checkpoints L 并把该log to stable storage
- Note list M of modified buffer blocks ➢ 
- Now permit transactions to proceed with their actions ➢
- Output to disk all modified buffer blocks in list M
- 在磁盘中有一个指针指向last ——checkpoints（确定的）



如果发生了非挥发性故障

一个方法是备份多分

另一个就是dump

- 将所有的log record 在main memory中的  放到stable storage
- ouput buffer 到disk
- 将databese 内容copy到storage
- 《dump》tolog on stable storage

recover

- restore from最近的dump
- redo all transaction 在dump之后
- ❑ Can be extended to allow transactions to be active during dump;  known as fuzzy dump or online dump，

## 12.5ARIES

<img src="C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220604152340697.png" alt="image-20220604152340697" style="zoom:80%;" />

- 用log sqquence number to 标记log record

- page LSN   means block LSN

  反应这个block LSN对应的record 以及之前的被反应到这个block中

- checkpoints with not only L but also dirty page table

  以及每个active transaction 的最后一个LSN

  算是fuzzy checkpoints 没有把所有buffer内内容都放入disk

  所以需要一个记录last checkpoint

  

- dirty page table 

  记录目前最新的更新对page的instruction 的LSN 和已经check过的LSN



recovery process

- analysis phase

  分析并记录如下数据

  - undo list

  - dirty pagetable  at time of crash

  - redoLSN (start point)

    dirty page table中的recLSN 的最小值

- redo phase

  物理恢复

  有RecLSN 和PageLSN的可以用来优化   避免重复的redoing

  碰到新的update record 时

  如果page 不在dirtypagetable or LSN of record 小于 recLSN------------skip

  （或者直接抓取page form disk，比较PageLSN和该条record LSN 如果大于PageLSN redo log）

- undo

  till start of earlist incomplete transaction

  每一个record 都有一个PrevLSN记录该T的上一个record方便redo

  

![image-20220604155825389](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220604155825389.png)

![image-20220604160224734](C:\Users\22470\AppData\Roaming\Typora\typora-user-images\image-20220604160224734.png)

先读取checkpoints的dirtypage 和L 再更新

第二站图为analysis pass时的dirty page table 和active T
