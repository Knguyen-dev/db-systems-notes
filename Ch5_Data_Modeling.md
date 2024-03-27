# Advanced Data Modeling 


## Extended Entity Relationship Model
A more advanced version of a regular ER Model.

### Entity supertypes and subtypes 
Think of supertypes and subtypes as inheritance, and the ideas of superclasses and subclasses. Organized in a 'specialization hierarchy', which shows the higher level supertypes and lower-level subtypes. Described with a 'is-a' relationship, which just indicates one is a superclass, and the other is a subclass (inheritance).

- Supertype: A 'generic' entity type, more abtract, and it passes down common info to subtypes. This is the base/abstract class that subclasses inherit from. By using supertypes, we minimize the number of nulls and redundant relationships.
- Subtype: A unique entity that inherits info and characteristics from the supertype. Then like any subclass, it will have its own unique characteristics./

### Inheritance
Subtypes inherits attributes and relationships of its supertype.

### Subtype discriminator
Attribute in the supertype entity that's used to distinguish between the different subtypes. For example, the 'Animal' supertype has 'Dog' and 'Cat' subtypes. To distinguish, the 'Animal' subtype can have subtype discriminator 'species' that could have values 'Dog' or 'Cat' to determine which subtype an entity belongs to. In implementation, the Dog constructor would do 'species = 'Dog'".

## Disjoint and overlapping
Typically a supertype can 'belong' to one and only one subtype at a given time. 

- For example: Supertype 'Shape' has two subtypes 'Circle' and 'Square'. They contain a unique subset of the supertype, which just means a shape instance can either be a circle or a square, not both.

However other times we have overlapping subtypes, meaning an instance of the supertype can 'belong' to or identify as more than one subtype at one time (overlapping subtype constraint).

- For example: A 'Employee' supertype has 'Full-time Employee' and 'Part-time Employee' subtypes. Now we have a 'Manager' subtype, which overlaps/inherits with full and part time, taking characteristics from both.

### Completeness Constraint
Defines whether every instance of the supertype must also be an instance of at least one subtype.

- Partial completeness: Not every supertype instance has a corresponding subtype instance, meaning a supertype instance may exist without being an instance of any subtype
- Total completeness: Every supertype instance is an instance of at least one subtype. For supertype instance to exist, it has to be one of its subtype instances.

- For example: If 'partial', then there could be Employees that aren't classified as 'Full-time' 'Part-time' or 'Manager'. On the other hand, if 'total', then an 'Employee' must be a 'full-time', 'part-time', or a 'Manager'.

### Review of constraint scenarios
- Disjoint partial:
  1. Supertype has optional subtypes
  2. Subtype discriminator can be null
  3. Subtype sets are unique
- Disjoint total:
  1. Every supertype is a member of only one subtype. E.g. 'Circle' or 'Square'.
  2. Subtype discriminator can't be null.
  3. Subtype sets are unique
- Overlap partial: 
  1. Supertype has optional subtypes. 
  2. Subtype discrminators can be null
  3. Subtypes sets are not unique
- Overlap total:
  1. Every supertype is a member of at least one subtype
  2. Subtype discriminators can't be null
  3. Subtype sets aren't unique.


## Specialization vs Generalization
Here are two methods for database design:
- Specialization: Top-down process to identify lower-level (specific) entities, starting from the higher-level supertypes. About breaking down higher level entities into lower level ones.
- Generalization: We start with several common characteristics creating a specific/low-level entity. Then we go up and define the higher-level entities.

## Entity cluster 
A virtual entity, that groups multiple entities.
- For example, in a 'School' ERD, the 'Location' entity could be your entity cluster. It just groups the 'Room' and 'Building' entities and their relationships together. 

## Keys
- Composite keys: Good as idnetifiers in composite entities (joint tables). Where the primary key is the combination of some foriegn keys. Also good as Ids for weak entities, that have strong relationships with their parents.

- Primary key created by database designer to simplify the ID of entity instances. Has no intrinsic meaning as it is just a value created by DBMS for uniqueness.
1. Good when no natural key, or naturally unique attribute we can use.
2. When candidate key is too long.

## Fan trap (Design traps):
A design trap that happens when one entity has two 1:M relationships. This usually happens when we incorrectly identify the relationship. So if this happens, you should know that something is wrong.