# Explain Query Plan
An SQL command used to obtain a high-level description of the strategy or plan that SQLite uses to implement a specific SQL query. It also reports on the way in which the query uses database indices as well. 

## How it works
1. Parsing: When you submit a query to a database, a DBMS first parses it to understand what you're asking for.
2. Query optimization: DBMS generates a plan for how to execute the query efficiently. Deciding which index to use, what tables to access first, and in what order.
3. Execution: DBMS executes query according to the plan it generated.

The EQP command allows us to see the execution plan without actually running the query. This helps us understand how the DBMS intends to execute your query and identifies potential bottlenecks or areas for improvement.