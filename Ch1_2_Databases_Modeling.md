# Chapter 1: Intro to Data & Databases 

## Data vs Information:
- Data: Raw/unprocessed facts, statistics, numbers. Use it to uncover patterns and get 'information'
- Information: The result of processing data and the meaning behind it.
- Data management: Focuses on creating, storing, and retrieving data.

## Introducing the database:
- Database: A computer structure that stores data.
1. End-user data: Data about the end user.
2. Metadata: Data about data. Such as file size, when a piece of data was created
- Database management sysetm (DBMS): Programs that manages the database and controls access to the data stored in it. Examples are like MongoDB, MySQL, Microsoft Access, Redis. All of these are programs or interfaces that we use to query, and interact with a database.

## Types of databases:
- Single-user: Supports one user at a time. An example is a 'desktop' database where it's stored on a personal computer
- Multi-user: Supports multiple users at a time. So like a 'workgroup' database tha supports a group of users.
- Classified by location: 
1. Centralized: Supports data at a single location
2. Distributed: Works at multiple different sites
3. Cloud: Created and maintained using cloud services.
- General-purpose: Contains a wide variety of data used in multiple disciplines. So like mySQL, Sqlite, Mongodb, these databases can be used for anything.
- Discipline-specific: Contains data about certain subjects. For example, 'ChemSpider' is a popular database that has data about many different chemical compounds. Or PubMed, which is a database that contains many different articles on Biomedical literature.
- Operational database: Personalized to support a company's operations
- Analytical Database: Stores data for a business to make decisions. It has two parts:
  1. Data wareouse: Stores data 
  2. Online analytical processing: Tools for getting, processing, and displaying the data
- Types of structured data:
  1. Unstructured: Exists in original/raw state
  2. Structured: Has been formatted and processed, so it's ready for use and analysis.
  3. Semi-structured: Processed to some extenet.
- NoSQL (Not only sql): Dbms that isn't only restricted to the use of tables like in relational databases. 

## File System:
Some people do process data in file system, where all data is contained within a file, but this has obvious drawbacks compared to using a dbms.
- Field: A single piece of data. Such as a 'name', 'age', 'username', etc.
- Record: A single object or thing in the database. A 'person', 'user', or 'item'.
- File: A collection of related records. So like a file could contain data about the students enrolled at a certain school.

## Data dependence:
- Structural dependence: Reliance of one schema on another. Changes in the structure of one necessitate changes in another schema that depends on the former. For example, if a certain table's structure is changed, your queries built on that table may also need to be changed.
- Structural independence: Even if you change the structure of one it doesn't change naother schema. 
- Data independence: How the data is stored doesn't affect the programs using the data. There are two types of this:
  1. Logical: Changes in logical structure (schema), doesn't affect program.
  2. Physical: Changes in physical method of storing data, doesn't affect program.
- Data dependence: How the data is stored, affects the programs using the data. So like if the format of the data changes in storage, you'll need to change the programs that access that data.

## Data Redundancy:
When the same data is stored unnecessarily at different places. As a result, we could have data inconsistency and integrity issues.

## What is a 'database system':
Refers to an organization of components that are in charge of collecting, storing, and managing data within a database.
1. Hardware: Servers and computers that keep the database operational.
2. Software: Things such as DBMS and middleware in between collecting data and storing it.
3. People: Programmers, data analysts, designers, admins, and even end users.
4. Procedures: How we store, format, and rules for dealing with data.
5. Data


# Chapter 2: Intro to data modeling

## What are models and modeling
- Data modeling: Process of creating a specific 'model' or structured representation of data in a database. Examples could be for a social media platform where models could be a 'user' or 'post'.
- Data model: The visual or mathematical representation of the structure of the data. It shows logical relationships and rules between different data elements and models. You may see models in an entity-relationship diagram.
- Entity: A person, place, or thing that we will collect data about.
- Attribte: A characteristic/property of an entity
- Relationship: Describes an association or link among entities.
  1. One to many (1:M or 1..*): An example, for every 1 user, they can have many posts. But each post can only be linked to one user
  2. Many-to-many: A student can be in many classes, and a class can have many students.
  3. One to one: A user has only one shopping cart, and each shopping cart is associated with one user.
- Constraint: Rules for our data. Such as the gpa must be between 0 and 4.00, or each class must have only one teacher.

## Business rules:
An easy to understand rule or policy for your use-case or organization. These are then used to define entities, attributes, relationships, and constraints. An example would be "Each employee is assigned to only one department". 
1. Entities: It's your employee and department
2. Attributes: List the attributes of your employee such as name email, etc. and also the attributes for the department.
3. Relationship: It's a one-to-many relationship in the sense that, one department can have many employees, but an employee can only be linked to one department.
4. Constraints: You'd likely have a foreign key to the department table like 'department_id' that would link the employee and the department.


## Relational model:
Database is represented as rows and columns, similar to an excel spreadsheet. Each row is called a 'tuple' and each column represents an attribute

## Entity-Relationship Model:
A graphical/visual representation of our database. There are three types of notations "Chen notation", "Crow's foot", and "Uml class diagram notation". Meaning an entity relationship is simply a ER-Diagram, but you can use those types of notation.


## Object oriented data model:
Data and relationships are represented by classes and programming objects. There could be hierarchy, inheritance, and methods. These are usually shown with UML class diagrams. 

## Degrees of Data abstraction:
This just defines three levels of how we can abstract our database to improve understanding across different groups of people. T

1. External: Mostly what end-users. So this would be ER-diagrams and visual representations.
2. Conceptual: Provides bird's eye view of entire database. Again would be an ER-diagram of some type 
3. Internal: What the DBMS handles and sees. SO this would be database comamnds that make changes to the database.

### Review on independence:
1. Physical independence: When you can change physical model without affecting internal model.
2. Logical independence: When you can change internal model without affecting conceptual model