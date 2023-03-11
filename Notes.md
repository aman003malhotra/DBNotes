## SQL
- This database is based on the relational data model, which stores data in the form of rows(tuple) and columns(attributes), and together forms a table(relation).

- A relational database uses SQL for storing, manipulating, as well as maintaining the data. Each table in the database carries a key that makes the data unique from others. Examples of  Relational databases are MySQL, Microsoft SQL Server, Oracle, etc.

## ACID Properties
 
- Set of properties that guarantee that database transactions are processed reliably, referred to as ACID.

### What is a transaction
- In the context of databases, a single logical operation on the data is called a transaction. For example, a transfer of funds from one bank account to another. involving multiple changes such as debiting one account and crediting another, is a single transaction.

- CRUD - Create Read Update Delete.

### Atomicity
- Atomicity refers to the ability of the database to guarantee that either all of the tasks of a transaction are performed or none of them are.
- Database modifications must follow an all or nothing rule.
- Each transaction is said to be atomic if when one part of the transaction fails, the entire transaction fails.

### Consistency
- Consistency means that database systems have to enforce business rules defined for their databases.
- The consistency property ensures that the database remains in a consistent state before the start of the transaction and after the transaction is over (whether successful or not).
    
    - Columns only store values of a particular type (int
    - columns store only ints, etc)
    - Primary keys and unique keys are unique
    - Check constraints are satisfied
    - Foreign key constraints are satisfied
    
### Isolation 
- Isolation refers to the requirement that other operations cannot access or see the data in an intermediate state during a transaction. This constraint is required to maintain the performance as well as the consistency between transactions in a database. Thus, each transaction is unaware of another transactions executing concurrently in the system.

- Events within a transaction must be hidden from other transactions running concurrently. Providing isolation is the main goal of concurrency control.


### Durability

- Durability refers to the guarantee that once the user has been notified of success, the transaction will persist, and not be undone. It refers to the ability of the system to recover committed transaction updates if either the system or the storage media fails. Features to consider for durability:

    - recovery to the most recent successfu/commit after a databases software failure
    - recovery to the most recent successfu/commit after an application software failure
    - recovery to the most recent successfu/commit after a CPU failure
    - recovery to the most recent successfu/backup after a disk failure
    - recovery to the most recent successfu/commit after a data disk failure

### Database Storage
- Databases typically store large amounts of data that must persist over long periods of time, and hence the data is often referred to as persistent data. 
- Parts of this data are accessed and processed repeatedly during the storage period. 
- This contrasts with the notion of transient data, which persists for only a limited time during program execution.
- The data stored on disk is organized as files of records. Each record is a collection of data values that can be interpreted as facts about tables, their columns, and their relationships.
- Records should be stored on disk in a manner that makes it possible to locate them efficiently when they are needed.

### NoSQL Databases
- NoSQL systems are also sometimes called Not only SQL to emphasize the fact that they may support SQL-Iike query languages.
- The data structures used by NoSQL databases are different from those used by default in relational databases which makes some operations faster in NoSQL.

#### Key Value Database
- The key-value pair storage databases generally store data as a hash table where each key is unique. The value can be of any type (JSON, BLOB(Binary Large Object), strings, etc). This type of pattern is usually used in shopping websites or e- commerce applications.

    - ADVANTAGES - Can handle large amounts of data and heavy load, Easy retrieval of data by keys.
    - DISADVANTAGES - Complex queries may attempt to involve multiple key-value pairs which may delay performance.

#### Column Store Databases
- Rather than storing data in relational tuples, the data is stored in individual cells which are further grouped into columns. Column-oriented databases work only on columns.

- They store large amounts of data into columns together. Format and titles of the columns can diverge from one row to other. Every column is treated separately. But still, each individual column may contain multiple other columns like traditional databases

- Aggreagate functions can be easily performed.

#### Graph Databases
- Graphs are basically structures that depict connections between two or more objects in some data. The objects or entities are called nodes and are joined together by relationships called Edges. Each edge has a unique identifier. Each node serves as a point of contact for the graph.


## Sub Language of SQL
- ### DDL (Data Definition Language)
    - CREATE, ALTER, DROP, RENAME, TRUNCATE.

- ### DML (Data Manipulation Language)
    - INSERT, DELETE, UPDATE

- ### DRL/DQL (Data Retrieval/Query Language)
    - SELECT

- ### TCL (Transaction Control Language)
    - COMMIT, ROLLBACK, SAVEPOINT

- ### DCL (Data Control Language)
    - GRANT, REVOKE

``` 
create database pesto_database;
use pesto_database;
-- Case Insensitive 
-- Data Definition Language
create table emp(
	empNo int(4) primary key,
    ename varchar(50) not null,
    job varchar(50) not null,
    mgr int(4),
    hiredate date,
    -- DECIMAL (total num of digits, digits after decimal) 
    sal decimal(10,2),
    comm decimal(10,2),
    deptno int(2)
);


-- insert valules
--  DATA MANIPULATION LANGUAGE
insert into emp values
(7369, 'SMITH', 'CLERK', 7902, '93/6/13', 800.0, 0.00, 20);

-- DELETE DATA VALUES
TRUNCATE TABLE emp;

-- ROLLBACK DOES not work after a commit.

create TABLE dept(
	deptno int(4) primary key,
    dname varchar(40) not null,
    location varchar(50) not null
);

create table salgrade(
	grade int(4) primary key,
    losal decimal(10,2),
    hisal decimal(10,2)
);

-- DROP COMMAND DELETE THE VALUES
drop table salgrade;


-- CONDITIONAL OPERATOR
 -- WHERE - condition
SELECT * FROM emp WHERE deptno = 10;

-- WHEN WE WANT TO SEE SPECIFIC COLUMNS
SELECT ename, job, sal FROM emp WHERE sal = 1600;

-- CONCATENATE TWO COLUMNS
SELECT concat(dname," ", location) as RandomColumName from dept;

-- DISTINCT OPERATOR
select distinct(deptno) from emp;

-- LOGICAL OPERATORS
-- AND OPERATOR
SELECT * FROM salgrade where grad < 4 and hisal > 4000;

-- OR OPERATOR
SELECT * FROM emp where deptno = 20 or deptno = 30;

-- NOT OPERATOR
SELECT * FROM emp WHERE deptno != 30;

-- BETWEEN OPERATOR
SELECT * FROM emp WHERE sal between 2000 and 6000;

-- IN OPERATOR
SELECT * FROM emp WHERE deptno = 10 or deptno = 20; 
-- IT can be written as 
SELECT * FROM emp WHERE deptno in (10,20);

-- SINGLE QUOTE
SELECT * FROM emp WHERE ename = 'ALLEN';

-- LIKE OPERATOR PATTERN MATCHING
SELECT * FROM emp WHERE ename like'S%'; -- START WITH S

SELECT * FROM emp WHERE ename like 'a%'; -- STARTS WITH A CASE INSENSITIVE

SELECT * FROM emp WHERE ename like '%n'; -- ENDS WITH N

SELECT * FROM emp WHERE ename like '%in'; -- ENDS WITH in

SELECT * FROM emp WHERE ename like '%l_%'; -- second character should be L 

SELECT * FROM emp WHERE ename like 'A___N'; -- Starts with A 3 character between and Ends with N.

SELECT * FROM emp WHERE ename like 'k%n'; -- starts with k ends with n in between any charcaters.


-- UPDATE OPERATIONS
UPDATE emp set job = 'analyst', deptno=30 where empno=7876; -- UPDATE job, deptno from empno 7876.

UPDATE salgrade set losal = 1000; -- sets all the values of losal to 1000

update dept set deptno=25; -- as dept no is primary key so ther cannot be repeated gives error.

UPDATE emp SET mgr = NULL where empno=7876; -- updates the value to the null.

-- DELETE OPERATIONS
DELETE from salgrade where grade > 5; -- DELETE ROWS from grade greater than 6.

DELETE from salgrade WHERE grade > 3 and losal < 3000;

DELETE from salgrade; -- SAME as truncate operation. but truncate is faster.alter

-- AGGREGATE FUNCTIONS

-- count 
SELECT count(*) from emp; -- returns the number of rows.

-- min
SELECT min(salary) from emp; -- returns the minimum salary.

-- max
SELECT max(salary) from emp; -- returns the maximum salary,

-- avg
SELECT avg(salary) from emp; -- returns the average salary.

-- GROUPBY CLAUSE

SELECT job, avg(sal) from emp GROUP By job; -- will make group of same job and give average of their salary.

-- Order By clause

SELECT * FROM emp Order by sal; -- will order the result in ascending order according to the salary.

SELECT * FROM emp Order by sal desc; -- will order the result in descending order according to the salary.

SELECT job, count(*) as number_of_employee from emp group by job; -- count people for a particular job.

SELECT job, count(job) as number_of_employee from emp group by job; -- count people for a particular job.

SELECT Deptno, sum(Sal), min(sal), max(sal), count(*) from emp Group by deptno;

-- JOINS

-- Inner join - only intersection data can be retrieved.
-- Left Outer Join - left table data and common data.
-- right outer join - right table data and common data.

SELECT e.empno, e.ename, d.dname, e.job
FROM emp as e
LEFT JOIN dept as d
on e.deptno = d.deptno
UNION
SELECT e.empno, e.ename, d.dname, e.job
FROM emp as e
RIGHT JOIN dept as d
ON e.deptno=d.deptno; 

-- full outer join - left, right and common data



```
