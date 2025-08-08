# Databases: 

What is a database?

Database for dummies book defines it as: self-describing collection of integrated
records.
- self describing: contains description of it's own structure (metadata)
- integrated: contains info on relationships within the db
- records: records contains attributes

Computers are great at storing and retrieving information. 

Database management software
- used to define, administer, and process databases
- To talk to the data we have database management software.

There are two main types of databases: 
- relational databases (SQL) - structured data
- non-relational databases (noSQL) - non structured data

Relational database mangement systems (RDMS) are for relational databases
examples include Postgres, mysql, sqllite. 

Where are they held?
- sqlite holds entire db in one file
- post gres - multiple files in a data cluster directory 

Relational database have tables that are independant of each other. Allows
independant manipulation of tables as long as it doesn't have a child table. We call them relational databases because they have relations with lots
of tables 

SQL can be used to query a database, define the database schema, control access
to the database and manipulate entries. SQL is also implemented differently between different database systems so a
query or code that works in one won't necessarily work in another.

An important acroymn when talking about databases is CRUD (Create, Read, Update,Read). These are the common tasks a database needs to be able to do.

database schema is blueprint of database and defines how data is organised within the database including:
- data types
- constraints

Sql alchemy is a python library that lets you abstract away from a relational
database management software. SQL alchemy lets you map python objects to SQL
queries. 

In SQL alchemy,  the enigine is the start. The engine acts as a central source of connections to
the database. It's an object created once to connect - sort of like a door
opening. A session is a python object that establishes and maintains all converstations
between app and the databse. It's a sort of holding spot for all the mapped
objects. It manages any changes to objects and commits them to the datbas -
maages orm operatios, transcactions. Now the fun stuff, the metadata. The tables you code up e.g. the rows and column
info is called the Metadata. All the table info gets stored in one metadata
instance.



