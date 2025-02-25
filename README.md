# Tender-Management-System
User Login: babi@gmail.com/Babi@123
	Admin Login: Admin/Admin
Whenever a company  requires a service / merchandise , a tender is floated. Company maintains an empaneled list of Vendors. An empaneled vendor can only bid for a tender. Every vendor can bid only once against   each tender. Against each tender there may be   bids from several vendors. The company will then select the most suitable bid and places the order to that vendor.
<!--
**There are 2 users in the system**

1.	Administrator and
2.	Vendor

**The Role of Administrator is**

1.	Create new Vendor.
2.	View all the vendors.
3.	Create new tenders.
4.	View All the Tenders.
5.	View All the Bids of a tender.
6.	Select a Bid.

**The Role of a Vendor is**
1.	View all the current Tenders.
2.	Place a Bid against a Tender.
3.	View status of a Bid(Whether Selected or Not)
4.	View his own Bid History.

### Technologies used:-
1. Front-End Development:
- Html
- Css
- Javascript
- BootStrap

2. Back-End Development
- Java
- JDBC
- Servlet
- JSP
- MySQL

### ==== Software And Tools Required ======
- : MySQL
- : Eclipse EE
- : Java JDK 8+
- : Tomcat v9.0
- : Apache Maven
- 
### ========== Dummy Database Initialization USing SQLDUMP =====================

STEPS: If you want to create table structure with dummy database, then follow the Steps given <a target="_blank" href="https://github.com/balaram3834/Tender-Management-System/blob/master/DataBase/how-to-import-sql-dump-file.md">Here Inside DataBase/how-to-import-sql-dump-file</a>

### ================= Dummy Database Initialization USING QUERY =================

STEP 1: Open MySQL Command Prompt or MySQL Workbench

STEP 2: Login to the administrator user as : ```mysql -u <username> -p``` (Enter Password if asked)

STEP 3: Copy paste the following MySql Commands-
```MySQL
create database tender;

commit;

use tender;

create table notice(id int(3) not null auto_increment, title varchar(35),info varchar(300), primary key(id));

alter table notice AUTO_INCREMENT = 1;


create table vendor(vid varchar(15) primary key,password varchar(20),vname varchar(30),vmob varchar(12),
		vemail varchar(40),company varchar(15),address varchar(100));


create table tender(tid varchar(15) primary key,tname varchar(40),ttype varchar(20),tprice int,
		    tdesc varchar(300),tdeadline date,tloc varchar(70));

create table bidder (bid varchar(15) primary key,vid varchar(15) references vendor(vid),tid varchar(15) references tender(tid),
		bidamount int,deadline date,status varchar(10));


create table tenderstatus(tid varchar(15) primary key references tender(tid),bid varchar(15) references bidder(bid),
		status varchar(15) not null,vid varchar(15) references vendor(vid));
  
  INSERT INTO tender VALUES ('T20190725022124','Hyderabad Metro','maintainence',50000,'lkjhgfd','2019-07-19','Patna, Bihar'),('T20190725022416','MEGA CITY CONNECTING ROAD CONTRUCTION','construction',100000,'mega city road contruction','2019-09-14','Delhi');


INSERT INTO notice VALUES (2,'Hyderabad Metro ','Repairing work is going to be started tommorow'),(3,'BRIDGE CONTRUCTION','ASSINGNED ENGINEER NEED TO REPORT on time');

INSERT INTO vendor VALUES ('V20190725020951','Balaram','Krishna','07501 070485','babi@gmail.com','hd','Kukatpally,Hyderabad'),

INSERT INTO bidder VALUES ('B20190725022953','V20190725022813','T20190725022124',51000,'2019-07-19','Pending'),('B20190725023010','V20190725022813','T20190725022124',52000,'2019-07-19','Accepted'),('B20190725023248','V20190725022813','T20190725022416',100001,'2019-09-14','Rejected'),('B20190725101554','V20190725022813','T20190725101322',160000,'2019-07-19','Accepted');

INSERT INTO tenderstatus VALUES ('T20190725022124','B20190725023010','Assigned','V20190725022813'),('T20190725022416','B20190725023512','Assigned','V20190725023446'),('T20190725022601','B20190725024243','Assigned','V20190725022813'),('T20190725101322','B20190725101554','Assigned','V20190725022813');

commit;
