---
Title: DBS101 flipped Class 12
categories: [DBS101, Flipped_Class12]
tages: [DBS101]
---

### Topic : recovery Agorithms
----

Recovery algorithms in Database Management Systems (DBMS) are crucial for maintaining the consistency and durability of data in the event of failures such as system crashes, hardware failures, or network issues. These algorithms ensure that the database can recover to a consistent state after such failures. 

![alt text](<../Screenshot 2024-06-04 053851.png>)

Here are some common recovery algorithms:

Write-ahead Logging (WAL):

In WAL, changes to the database are first recorded in a log file before they are applied to the actual database.
Before a transaction makes any changes to the database, it writes a log record indicating the changes it intends to make.
After the changes are applied to the database, a commit record is written to the log.
During recovery, the system replays the log from the last checkpoint to restore the database to a consistent state.

Checkpointing:

Periodically, the DBMS writes a checkpoint record to the log indicating the state of the database at that point.
Checkpoints help in reducing the amount of log to be replayed during recovery.
During recovery, the system starts from the last checkpoint and replays only the log records after that point.

Shadow Paging:

In shadow paging, the database is represented by two pages: the actual database pages and the shadow pages.
Whenever a transaction makes a change, it writes the changes to a new set of shadow pages.
After the transaction commits, the pointer to the database pages is updated to point to the new shadow pages.
During recovery, if a transaction aborts, the changes made by that transaction can be discarded simply by not updating the pointer to the shadow pages.

Immediate Update:

In this scheme, changes are applied directly to the database without first writing them to a log.
In case of a failure, the recovery process involves undoing the changes made by incomplete transactions and redoing the changes made by committed transactions.
Immediate update requires careful management of transactions to ensure durability.

Logging and Recovery Protocols:

These protocols define the rules for logging and recovery in a DBMS. Examples include ARIES (Algorithm for Recovery and Isolation Exploiting Semantics) and Write-Ahead Logging protocol.
These protocols specify the format of log records, the actions to be taken during normal operation, and the steps for recovery after a failure.

Each recovery algorithm has its advantages and trade-offs in terms of performance, complexity, and overhead. The choice of algorithm depends on factors such as the requirements of the application, the size of the database, and the characteristics of the underlying hardware.

### Aries
----
ARIES (Algorithm for Recovery and Isolation Exploiting Semantics):

ARIES is a recovery algorithm designed to ensure both correctness and efficiency during database recovery. It was proposed by C. Mohan, D. Haderle, B. Lindsay, H. Pirahesh, and P. Schwarz in the late 1990s. ARIES is widely used in commercial relational database management systems, including IBM's DB2.

![alt text](<../Screenshot 2024-06-04 054351.png>)

Key features of the ARIES algorithm include:

Write-Ahead Logging (WAL):

ARIES follows the write-ahead logging protocol. Before a database page is modified, the corresponding log records are written to the log buffer in stable storage.
This ensures that the log records are persisted before the corresponding database modifications, which is crucial for recovery.

Logging and Recovery Phases:

ARIES has distinct logging and recovery phases.
During normal operation, ARIES logs all updates to the database. It uses a special kind of log sequence number (LSN) to order log records and ensure atomicity and durability.
During recovery, ARIES uses a combination of redo and undo operations to bring the database to a consistent state.

Undo and Redo Operations:

During the redo phase of recovery, ARIES reapplies logged updates that were not already present in the database.
During the undo phase, ARIES rolls back the effects of incomplete transactions that were active at the time of the crash.
ARIES uses a logical undo mechanism to undo changes efficiently without accessing the original data pages.

Checkpoints:

ARIES uses checkpoints to minimize the amount of log to be analyzed during recovery.
During a checkpoint, ARIES flushes dirty pages to disk and writes a checkpoint record to the log, indicating the state of the transaction and database at that point.
During recovery, ARIES starts the redo phase from the most recent checkpoint to reduce the amount of log to be analyzed.

Logging and Buffer Management:

ARIES carefully manages the logging and buffer management to ensure efficiency.
It uses a combination of volatile and stable storage for logging to minimize overhead while ensuring durability.
ARIES employs a steal/no-force buffer management policy to maximize concurrency and throughput.

ARIES is known for its robustness, efficiency, and ability to handle a wide range of failure scenarios. It is widely used in production database systems and has been the subject of extensive research and optimization over the years.

### DB logging
----
Database logging, often referred to as transaction logging or write-ahead logging (WAL), is a fundamental mechanism used by Database Management Systems (DBMS) to ensure the durability and recoverability of data. Here's an overview:

Purpose:

The primary purpose of database logging is to maintain a record of changes made to the database over time. This log serves as a persistent record of transactions that can be used for recovery in the event of a system failure.

Key Components:

Log Records:

A log record contains information about a single operation or action performed on the database. This typically includes details such as the type of operation (e.g., insert, update, delete), the affected data (e.g., table, row), and any additional metadata necessary for recovery.

Log Sequence Number (LSN):
Each log record is assigned a unique identifier called the Log Sequence Number (LSN). LSNs are used to maintain the order of log records and to identify the point in the log from which recovery should start.

Write-Ahead Logging (WAL):

The most common approach to database logging is Write-Ahead Logging (WAL). In WAL:

Before Modification:

Any modification to the database (e.g., insertion, update, deletion) is first recorded in the log buffer in volatile memory.

Commit Record:

When a transaction commits, a commit record is written to the log buffer. This indicates that all changes made by the transaction have been successfully applied to the database.

Flush to Disk:

Periodically or when the log buffer is full, the contents of the log buffer are flushed to stable storage (e.g., disk).
Durability:

Once a log record is written to stable storage, it is considered durable. This ensures that even in the event of a system crash, the changes recorded in the log will not be lost.

Recovery:

In the event of a system failure, the database system uses the information in the log to recover the database to a consistent state. 

This typically involves two phases:

Redo Phase:

During the redo phase, the system replays the log from the last checkpoint (or from the most recent log record) forward, reapplying all committed changes to the database. This ensures that any changes that were recorded in the log but not yet applied to the database are re-applied.

Undo Phase:

During the undo phase, the system identifies any incomplete transactions that were active at the time of the crash and rolls back their changes. This ensures that any changes made by transactions that were not committed are not applied to the database.

Database logging is essential for maintaining data integrity and ensuring recoverability in the face of system failures. It provides a reliable mechanism for tracking changes to the database and allows DBMS to recover to a consistent state following a failure.




