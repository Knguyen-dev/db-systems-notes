# Normalization of database tables


## What is Normalization
The process of evaluating and correcting tables to minimize redundancy. It works through a series of stages called 'normal' forms. As we progress and normalize, we go to a 'higher' normal form, and most times we only need to go as high as '3NF'.

1. First Normal Form (1NF): Eliminate duplicate columns in your tables, each table has a primary key. Essentially start creating your tables.
2. Second Normal Form (2NF): Remove partial dependencies in your tables. Happens when an attribute depends on a portion of a multi-valued PK.
3. Third Normal Form (3NF): Remove transitive dependencies, which is just when the values of non-key attributes depend on another non-key attribute (idea functional dependency). 
4. BCNF (Special 3NF): Every determinant is a candidate key. 
5. 4NF: No independent multi-valued dependencies.
6. 5NF: Can't have lossless decomposition into smaller tables.


- NOTE: 
1. A determinant is an attribute or set or attribute that uniquely determines another attirbute in the table. For example, in an 'Employee' table, the Employee ID could be the determinant for the name and department of the employee because each ID uniquely determines the corresponding employee.
2. A partial dependency is when a column's value depends on a 'component' of the primary key, rather than the entire key. If this is possible, why not just use that component, rather than have an entire primary key (idea of redundant data). For example, the Orders table has "OrderID", "CustomerID", "OrderDate", "ProductID" and quantity. The primary key is OrderID, and the rest are non-key attributes. 


### Need of normalization:
We want to eliminate data anomalies by eliminating unwanted data redundancy.




### Types of dependencies
- Partial dependency: When we got a functional dependence and the determinant is part of the PK.
- Transitive dependency: When attribute is dependent on another attribute that isn't the primary key.


# Database normalization (video)
- Normalization: Process of reducing and removing unnecessary data redundancy. There are levels called 'normal forms' as levels of safety to protect data from redundancy. 

## First Normal Form:
1. Using row order to convey information is bad. 
2. Mixing datatypes for a column will violate 1nf. If you define a column as 'integer' it can only have integer.
3. A primary key must be defined.
4. Groups can't be repeated. At an intersection between row and column, there exists a single value. So John's height is 180cm only. It can't be 183, 192, and 182, or multiple values for that cell.

- For example, let's say we wanted a database to track a gamer's inventory in a certain game. Call the table  'Player_inventory', which has Player_ID, Item_type, and qty. the PK here is Player_ID and Item_type. We'll use the Player_ID and Item_Type fields to create the primary key, and then uniquely identify the qty of the item a player has.

## Second Normal Form:
Each non-key attribute must depend on the entire primary key. For example, the ID and TYPE of item are both required to determine the qty, you can't just one use of them. Denoted by {ID, TYPE} => {qty}. Each unique value set of attributes for ID and TYPE, are linked to exactly one 'qty' value. This is full dependence.

However, let's add player 'rating' to the table. So now it's Player_ID, Item_Type, qty, and rating. You can probably merely use 'ID' of the player to determine their rating, you don't need to know the Item_Type of what's in their inventory. You're using a part of the PK, and not using 'TYPE', to determine the rating. So this is partial dependence, because we only use a part of the primary key to determine the value of a column. As a result this can cause problems, and the reason this happens is because we inserted the 'rating' of a player in the 'inventory table'. To fix this create your own table for player. As a result, all of our non-key attributes, 'Rating' and 'Qty', are determined by using their entire primary keys, just just a piece of them like earlier.

- Player table: Player_ID, Rating; where {Player_ID} => {Rating}
- Player inventory: Player_ID, Item_Type, Qty; where {Player_ID, Item_Type} => {Qty}

### Third Normal Form:
Let's add a new column 'skill_level' so now the table looks like this. Let's say skill_level is an integer between 1 to 9, where 1-3 is beginner, 4-6 intermediate, and 7-9 is advanced.
- Player table: Player_ID, Rating, skill_level; where {Player_ID} => {Rating}
However an issue can arise when databaes operations go wrong and you have a skill_level = 4 and a rating of 'Beginner'.  The issue arises with how the dependencies are made:
1. {Player_ID} => {Player_Skill_Rating}; The rating fully depends on the ID
2. {Player_ID} => {Player_Rating} => {Player_Skill_Level}; 

- ISSUE: However, the skill level is more so dependent on the rating rather than the player's ID. This is called a transitive dependency, and third normal form forbids this. The rating and skill level are both no key attributes, and we can have a non-key attribute depending on another non-key attribute.

- SOLUTION: Removing player rating from the player table, and create a new table called 'Player_Skill_Level'. Now, the Player table has no partial dependencies and transitive dependencies, because the non-key attributes, Player_Skill_Level, are determined by the entire primary key alone rather than other non-key attributes. The same for the skill levels table, the Player_Rating is solely dependent on the entire primary key (no partial), rather than other non-key attributes (no transitive dep).
1. Player Table: {Player_ID} => {Player_Skill_Level}
2. Player_Skill_Levels Table: {Player_Skill_Level} => {Player_Rating} 

- Takeaway: For 3NF, every non-key attribute should depend on the entire primary key, and nothing but the key. We depend on the entire to prevent partial dependencies, and also to prevent our non-key attributes from being determined/depending on other non-key attributes. 

### Boyce-Codd:
Every attribute in a table should depend on the entire primary key. Actually the difference between Boyce-Codd and Third Normal form is very tiny, and in almost all cases they are the same. So just follow the rule about all attributes needing to depend on the entire primary key for both.

At this point, Third Normal Form is the highest that we would typically go for things such as companies and businesses. However there are rare cases where we'd go for the further normal forms.


### Fourth Normal Form 
- Given the example For 