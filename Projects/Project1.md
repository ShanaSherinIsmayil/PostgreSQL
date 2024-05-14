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
     id | name | address
    ----+------+---------
    (0 rows)
### Insert values to table
    insert into class (name,address) values ('shana','tirur');
    student=# insert into class (name,address) values ('shana','tirur');
INSERT 0 1
student=# select * from class;
 id | name  | address
----+-------+---------
  1 | shana | tirur
(1 row)

    insert into class values ('2','niha','malappuram');
INSERT 0 1
student=# select * from class;
 id | name  |  address
----+-------+------------
  1 | shana | tirur
  2 | niha  | malappuram
(2 rows)

    insert into class values ('3','sherin','palakkad');
INSERT 0 1

    insert into class values ('4','bob','alappuzha');
INSERT 0 1

    insert into class values ('5','john','trivandrum');
INSERT 0 1
student=# select * from class;
 id |  name  |  address
----+--------+------------
  1 | shana  | tirur
  2 | niha   | malappuram
  3 | sherin | palakkad
  4 | bob    | alappuzha
  5 | john   | trivandrum
(5 rows)

### To display output in a sorted order 
