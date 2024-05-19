# Distributed Database Management Systems
Controls the operations for data over many different computer systems.

## Distributed processing and databases
- Distributed processing: The logic and for processing data is shared among multiple sites via a network.
- Distributed database: Stores a logically related database over multiple sites via a network.

## Single-Site Processing AND Single-Site Data
Here all processing is done on a single host computer. All data is then stored on the host computer's local disk. Here the DBMS is accessed by terminals connected to the host computer.

- NOTE: When we talk about processing, we talk about all of the tasks performed by the DBMS. Such as inserting, updating, retrieving, etc. Things such as indexing, query optimization, managing transactions, etc.

## Mult-site Processing AND Single-Site Data (MPSD)
Multiple processes run on different computers that share a single data repository. As a result, the data processing operations are allocated to different computers, getting things done faster. So you have multiple computers that communicate with the 'file server', the computer directly communicating with the database, through a network.

## Multi-site Processing AND Multiple-Site Data
This describes a fully realized distributed DBMS. So you'd have multiple computers for processing data and operations, and then multiple places where data copies or subsets of the data is stored. 