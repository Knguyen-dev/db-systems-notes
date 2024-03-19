# Relational Database Modeling

## Logical View of Data:
A relational data model allows us to see a database in a logically like with relationships of data and rather than focus on how its physically stored.
- Domain: In this sense, it's a set of allowed values for an attribute. 


## Types of keys and key rules:
- Primary key: Attribute or sometimes combination of attributes that uniquely identify a row/record in the database. 
- Foreign key: A key from a different 'foreign' table.
- Composite key: Key composed of multiple attributes. Note that an attribute that's used to compose a key is a 'key attribute'
- Superkey: Key that uses multiple columns to identify a record. It may have redundant data that isn't necessary for uniqueness.
- Candidate key: A super key with the fewest attributes possible, so it has no redundant data.

## Relational Operations
1. SELECT: Used to get rows
2. PROJECT: Used to get columns
3. UNION: Merges two tables, with the same schema into one, dropping duplicate row. 
4. INTERSECT: Get the duplicate rows from two union-compatible tables.
5. DIFFERENCE: Get all rows from one table that aren't in another. Both tables should be union-compatible.
6. PRODUCT: Gets the cartesian product, so we get all possible pairs of rows from two tables.
7. JOIN: Combining rows from two or more tables.

- NOTE: Union compatible means they just have the same database schema.

## Data dictionary:
Stores info about the design of the database. Things such as why certain decisions were made about the structure, the relationships betweeen tables, attributes, names, etc. Very helpful to a database designer.

## Entity relationships
You can review chapter 2 data modeling for a review on relationships. [Here](https://www.freecodecamp.org/news/crows-foot-notation-relationship-symbols-and-how-to-read-diagrams/) is a review of Crow's foot and the notation.

## Indexes
A data structure that allos dbms to quickly locate rows in a table, based on the values of one or more columns. Akin to indexes in a book where we can find a specific topic (the index) rather than scanning through the entire book. However, the idea is we index attributes that we use often, to effectively make use of this.