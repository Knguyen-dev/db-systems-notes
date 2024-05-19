# Performance Tuning and Query Optimization
Database performance tuning is the process of reducing the response time of a database system.

## Client and Server
- Client: Handles getting SQL query that returns the correct info in the least amount of time, using the minimum amount of resources on the server's end. This is also known as SQL performance tuning.
- Server: The DBMS environment that gives us our data.

## DBMS Architecture
- Data files: All data in a database is stored in these. Grouped in 'file groups' or 'table spaces'
- Table space: Group of several data files that store data with similar characteristics
- Data blocks: Smallest logical units of assignable storage space in the database.
- Extents: Collections of ata blocks that are shared in database objects
- Data/buffer cache: Memory area that stores the most recently executed SQL statements or procedures.

## Optimization modes
Most algorithms for query optimization follow two principles:
- Selecting the best execution order to achieve the fastest time.
- Selecting the right places to minimize communication costs between tables and other places.
We then rank them on operation modes

### Operation modes
- Automatic query optimization: DBMS finds the most cost-effective access path without user intervention
- Manual query optimization: Requires that optimizaiton be selected and scheduled by the programmer.

### Optimization techniques
- Statically based query optimization: Uses statistical information about hte DBMS to determine the best access strategy.
- Rule-based query optimization: Based on a set of user-defined rules for optimization.

## Indexes
Help speed up data access. An index is just a data structure that allows for efficient data retrieval based on certain columns/attributes. If you want to create an index, create one that's frequently used in your queries.

For example, in SQL use an index on columns frequently used in WHERE clauses or JOIN conditions.

## Conditionals and operations
- Use simple columns or literals as operands.
- Numeric field comparisons are faster than character, date, and NULL comparisons.
- Equality comparisons are faster tha ninequality comparisons
- Write equality conditions first hwen using multiple conditional expressions
- Whenever possible try to avoid the use of NOT logical operator.
- When using multiple AND conditions, write the condition most likely to be false first.
- When using multiple OR conditions put the condition most likely to be true first.


## Conditions
- AND: Place the condition that's most likely to eliminate the largest portion of the dataset first. This helps reduce the number of rows that need to be evaluated by the subsequent steps. By placing the condition that's most likely to be false first, we filter out most rows quickly.
- OR Condition: Place the most likely to be true first. 

### Conditional Example
Let's say we have a table of employees with attributes usch as name, age, departmnet, and salary. Let's find all employees who work in IT or earn more 
than $100,000 annually. So first we're doing an OR operator.
```
SELECT * FROM Employees 
WHERE Department = 'IT' OR Salary > 100000;
```
1. Since it's an OR operator we want to place the condition that's most likely to be true first. In this case if we think a large portion of employees work in IT, place that condition first. As a result, the OR condition is more easily satisified (done quicker), and we can move onto the second condition which is doing salaries.
2. Well maybe earning 100000 isn't as likely to be true for most employees, which is why we place this second. 
This optimizies the query because it's more likely that many employees will meet the ocndition of working in IT than earning over $100,000 per year, so it's quicker or just more obvious to check that.

### Conditional Example 2
Now we want all employees who work in IT AND have a salary greater than $80,000 per year. 
```
SELECT * FROM Employees 
WHERE Department = 'IT' AND Salary > 80000;
```
1. Place the condition that's most likely to be false first, so let's assume now that most employees don't work in IT. Considering the scenario where the majority doesn't satisfy that condition. So this quickly filters out a majority of our rows as non-candidates, and for the few ones that's left, we do the salary comparison.

### Conditional Example 3
I also want to show that this also works in mongodb. Let's find all employees who work in IT and have a salary greater than $80,000. Okay so this is an AND operation, so we put our query that's most lilkey to be false FIRST, to weed out most rows. So we're thinking it's more uncommon to be in 'IT' than to have a salary greater than $80,000. 
```
const employees = Employee.find({
  department: 'IT',
  salary: {$gt: 80000}
});
```
1. Assuming that most employees don't work in IT, place this condition first. 
2. Then our second condition follows.
By following this strategy we optimize the query to quickly filter out employees who aren't in IT, which is most of them, before evaluating the salary condition. This can potentially reduce the number of documents MongoDB needs to fully examine to fulfill the query.
