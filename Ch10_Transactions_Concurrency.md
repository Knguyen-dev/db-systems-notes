# Transaction Management and Concurrency Control:

## Transaction:
An operation that must be completed in its entirety, or entirely cancelled. [More here](https://github.com/Knguyen-dev/CS-Programming-Notes/blob/main/Backend-notes/MongoDB_notes/using_shell_intermediate/transactions/ex1_intro.md)

## Transactions with SQL:
SQL uses 'COMMIT' and 'ROLLBACK' to do ACID transactions. The former is used to save the changes made by a transaction and is used when it completes successfully. The rollback is used to undo changes made by the transaction, and is used in the case the transaction fails.