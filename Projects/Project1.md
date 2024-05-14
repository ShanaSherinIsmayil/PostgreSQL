## **Create <br>a) Database :Student <br>b) Table :class  <br>c) Attributes :1. id - bigserial - primary key , 2. name - varchar(50) - not null , 3. address - varchar(50)**
### Start the docker
    docker start my_postgres
### Connect to Docker
    docker exec -it my_postgres psql -U postgres
### Create database student
    create database student;
### display details of database
    \l
### Connect to database student
    \c student
  You are now connected to database "student" as user "postgres".
### Create table class
    create table class (id bigserial primary key, name varchar(50) not null, address varchar(50));
### Display table
    select * from class;
-
     id | name | address <br>
    ----+------+--------- <br>
    (0 rows) <br>
### Insert values to table
    insert into class (name,address) values ('shana','tirur');
    student=# insert into class (name,address) values ('shana','tirur');
INSERT 0 1<br>
student=# select * from class; <br>
 id | name  | address <br>
----+-------+---------<br>
  1 | shana | tirur<br>
(1 row)<br>

    insert into class values ('2','niha','malappuram');
INSERT 0 1<br>
student=# select * from class;<br>
 id | name  |  address<br>
----+-------+------------<br>
  1 | shana | tirur<br>
  2 | niha  | malappuram<br>
(2 rows)<br>

    insert into class values ('3','sherin','palakkad');
INSERT 0 1

    insert into class values ('4','bob','alappuzha');
INSERT 0 1

    insert into class values ('5','john','trivandrum');
INSERT 0 1<br>
student=# select * from class; <br>
 id |  name  |  address <br>
----+--------+------------ <br>
  1 | shana  | tirur <br>
  2 | niha   | malappuram <br>
  3 | sherin | palakkad <br>
  4 | bob    | alappuzha <br>
  5 | john   | trivandrum <br>
(5 rows) <br>

### To display output in a sorted order 
-    For ascending order
  
    select * from class order by name;
 id |  name  |  address <br>
----+--------+------------ <br>
  4 | bob    | alappuzha <br>
  5 | john   | trivandrum <br>
  2 | niha   | malappuram <br>
  1 | shana  | tirur <br>
  3 | sherin | palakkad <br>
(5 rows) <br>

    select * from class order by address;
 id |  name  |  address <br>
----+--------+------------ <br>
  4 | bob    | alappuzha <br>
  2 | niha   | malappuram <br>
  3 | sherin | palakkad <br>
  1 | shana  | tirur <br>
  5 | john   | trivandrum <br>
(5 rows) <br>

- For descending order

      select * from class order by address desc;
 id |  name  |  address <br>
----+--------+------------ <br>
  5 | john   | trivandrum <br>
  1 | shana  | tirur <br>
  3 | sherin | palakkad <br>
  2 | niha   | malappuram <br>
  4 | bob    | alappuzha <br>
(5 rows) <br>

### To display first two rows
    select * from class limit 2
student-# ; <br>
 id | name  |  address <br>
----+-------+------------ <br>
  1 | shana | tirur <br>
  2 | niha  | malappuram <br>
(2 rows) <br>

    select * from class offset 2;
 id |  name  |  address <br>
----+--------+------------ <br>
  3 | sherin | palakkad <br>
  4 | bob    | alappuzha <br>
  5 | john   | trivandrum <br>
(3 rows) <br>
### Retrieve using where cases:

    select * from class where address='palakkad';
 id |  name  | address <br>
----+--------+---------- <br>
  3 | sherin | palakkad <br>
(1 row) <br>

    select * from class where id='3';
 id |  name  | address <br>
----+--------+---------- <br>
  3 | sherin | palakkad <br>
(1 row) <br>

    select * from class where id>3; <br>
 id | name |  address <br>
----+------+------------ <br>
  4 | bob  | alappuzha <br>
  5 | john | trivandrum <br>
(2 rows) <br>

    select * from class where id>3 and id<2;
 id | name | address <br>
----+------+--------- <br>
(0 rows) <br>

    select * from class where id>3 and id<1;
 id | name | address <br>
----+------+--------- <br>
(0 rows) <br>

    select * from class where id<3 and id>1; <br>
 id | name |  address <br>
----+------+------------ <br>
  2 | niha | malappuram <br>
(1 row) <br>

    select * from class where id='4' or id='3';
 id |  name  |  address <br>
----+--------+----------- <br>
  3 | sherin | palakkad <br>
  4 | bob    | alappuzha <br>
(2 rows) <br>

    select * from class where id='4' and id='3';
 id | name | address <br>
----+------+--------- <br>
(0 rows) <br>

### To add new attribute to a table
    alter table class add std integer;

student=# select* from class <br>
student-# ; <br>
 id |  name  |  address   | std <br>
----+--------+------------+----- <br>
  1 | shana  | tirur      | <br>
  2 | niha   | malappuram | <br>
  3 | sherin | palakkad   | <br>
  4 | bob    | alappuzha  | <br>
  5 | john   | trivandrum | <br>
(5 rows) <br>
### To update data in a table
-Update data :

    update class set std = '2' where id='3';
UPDATE 1 <br>
student=# select* from class <br>
; <br>
 id |  name  |  address   | std <br>
----+--------+------------+----- <br>
  1 | shana  | tirur      | <br>
  2 | niha   | malappuram | <br>
  4 | bob    | alappuzha  | <br>
  5 | john   | trivandrum | <br>
  3 | sherin | palakkad   |   2 <br>
(5 rows) <br>

    update class set std = '8' where id!='3';
UPDATE 4 <br>
student=# select* from class <br>
; <br>
 id |  name  |  address   | std <br>
----+--------+------------+----- <br>
  3 | sherin | palakkad   |   2 <br>
  1 | shana  | tirur      |   8 <br>
  2 | niha   | malappuram |   8 <br>
  4 | bob    | alappuzha  |   8 <br>
  5 | john   | trivandrum |   8 <br>
(5 rows) <br>
### To delete all rows in a table

    truncate table class;
TRUNCATE TABLE <br>
student=# select* from class; <br>
 id | name | address | std <br>
----+------+---------+----- <br>
(0 rows) <br>

### To drop a table
    drop table class;
Note: A database cannot be deleted if we are inside that database
-    so connect to another dtaabase
-    eg: \c postgres
-    From there drop database student

    drop database student;
