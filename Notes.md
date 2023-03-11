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