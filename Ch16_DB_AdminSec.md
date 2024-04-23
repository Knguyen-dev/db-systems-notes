# Database Administration and Security

## Database Administration
- Database administrator (DBA): Responsible for controlling the centralized and shared database.
- Systems administrator: Responsible for coordinating and performing day-to-day data processing activities.
- Data administrator (DA) or information resource manager (IRM): Responsible for managing entire data resource. Has higher degree of responsibility and authority than the DBA.

## Data admin vs Database admin:
- Data admin (DA): Performs planning, sets long-term goals, policies, standards. A broad job in scope and it's DBMS-independent and is more managerial. More about analysis, understanding business stuff, and communication.
- Database admin (DBA): Controls and supervises, executes plans to reach goals, enfores policies, procesdures, and programming standards. Job is more narrow and technical in scope. Here it's DBMS-specific. So this role is more about understanding software development life cycle, programming, creating database diagrams, and knowing about database modeling and design.

## Security:
### Goals:
- Confidentiality: Protecting data against unauthorized access.
- Compliance: Our activities must meet data privacy, security, and other guidelines.
- Integrity: Data needs to be consistent and free of errors or anomalies.
- Availability: Refers to accessibility of our data whenever it's needed by authorized users.
### Security Vulnerabilities:
- Security vulnerability: Weakness in our system that could allow unuathorized access or cause service disruptions.
- Security threat: Imminent security violation.
- Security breach: Exploirts and endangers the integrity, confidentiality, and availability of the system. 
### Database Security:
Refers to DBMS features and other measures that give us security. Have password protection, update to the latest versions of the DBMS, set up audits and logs to know when database was accessed and by who.

Authorization management could also control which users are able to access and do specific things with the database.


## Data dictionary
Repo of information about data, definitions, descriptions, and attributes of data elements. It gives us a detailed description about how a database is organized. 

1. Data element names: Names of individual data elements, such as field names within a table such as 'username', 'password', or objects for a table 'User'.
2. Description: Detailed explanations of the objects in the database and elements in the database. What a 'email' is for a user and why it's here.
3. Data types, constraints, validation: Specifies data types for fields. Constraints such as length of the field, the domain of acceptable values, etc.
4. Relationships: Information about how data elements relate to each other, such as foreign key relationships.
5. Source of data: Can include the origin of the data, such as what system or process creates a piece of data.
6. Usage notes: Additional notes or instructions for using or interpreting the data elements.