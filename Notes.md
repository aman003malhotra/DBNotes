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