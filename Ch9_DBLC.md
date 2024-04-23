# Database Design

## Information System and how the database ties in:
Database is part of a larger system known as the information system. An information system collects, stores, and retrieves data and it's composed of people, hardware, software, business procedures, etc. 

## Database Life Cycle (DBLC):
1. Initial Study: Analyzes company situation and problem, objective, and the scope of what we can do.
2. Design: Creates conceptual design, DBMS, logical and physical design.
3. Implementation and Loading: Installs DBMS, create databaess, and loads data.
4. Testing and evaluation: Test the database, fine tune, evaluate, etc. 
5. Operation: Start using it to do stuff
6. Maintenance and evolution: We could introduce changes and make enhancements.


## Conceptual Design:
Create model of the database structure. this is the diagramming stage, and at the end of it we sholud have our entities, attributes, relationships, constraints, etc. Here we normalize the tables in our database, and complete our blueprint. This is the first stage, and at this point we haven't picked a DBMS yet, we just have a blueprint for our database.

## Logical Design:
This stage we translate our conceptual design to the constraints or rules of the DBMS we've picked. Make sure things are normalize, make sure everything's meets user requirements and the integrity is still good.

## Physical Design: 
Here we determine the location and physical storage for the database. Here we use tablespaces ,data files, and filegroups. Talks about how we would physically stored on disk.
