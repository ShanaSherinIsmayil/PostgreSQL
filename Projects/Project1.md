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
