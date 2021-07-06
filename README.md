# Database Fundamentals Course
## History of data persistence
Cloud storage has a great pro compared to other storage methods because it is accessible from anywhere in the world. It is also centralized and can be used by several people at the same time.
Databases come in when we transition to digital media.
Types of databases:
Relational: In the industry there are several companies dedicated to be relational database managers such as SQL Server, Oracle, MariaDB, among others.
Non-relational: They are still advancing and there are very different examples such as cassandra, elasticsearch, neo4j, MongoDB, among others.

## Services:
Self-managed: This is the database that you install yourself and take care of updates, maintenance, etc.
Managed: Services offered by modern clouds such as Azure and you don't have to worry about maintenance or updates.

## Database origin
Databases arise from the need to conserve information beyond what exists in RAM memory.
File-based databases were data stored in plain text, easy to store but very difficult to query, and relational databases were born out of the need to improve on this. Their inventor Edgar Codd left certain rules to ensure that the whole philosophy of databases was not lost, standardizing the process.

## Relational database components

##Entity
An entity is something similar to an object (object-oriented programming) and represents something in the real world, even something abstract. They have attributes which are the things that make them an entity and by convention are put in plural.
<br>
<img src="https://github.com/brendamrdz/week2-course6-batabase/blob/main/images/entity.jpg?raw=true" alt="alt text" width="30%" height="auto">
- Compound attributes are those that have attributes themselves.
- Key attributes are those that identify the entity and cannot be repeated. They exist:
  - Natural: they are inherent to the object such as the serial number.
  - Artificial key: is not inherent to the object and is assigned arbitrarily.
  - Strong entities: are entities that can survive on their own.
  - Weak entities: cannot exist without an entity. 
  - Weak identities by identity: they do not differ from each other except by the key of their strong identity.
  - Weak identities by existence: they are assigned a key of their own.
<img src="https://github.com/brendamrdz/week2-course6-batabase/blob/main/images/chen's%20notation%20model.png?raw=true" alt="alt text" width="50%" height="auto">

## Relationships 
Relationships allow us to link or unite our different entities and are represented by diamonds. By convention they are defined through verbs.
Relationships have a property called cardinality and it has to do with numbers. How many on one side belong to how many on the other side:<br><br>
![cardinality](https://user-images.githubusercontent.com/26840321/124555721-07aa5580-ddfd-11eb-9e63-da22809bcd87.png)

## Diagrams
A diagram is like a map and helps us to understand which entities we are going to work with, what their relationships and the roles they are going to play in the database applications.
### Physical diagram: data types and constraints
- NOT NULL: Ensures that the column has no null values
- UNIQUE: Ensures that each value in the column is not repeated.
- PRIMARY KEY: Is a combination of NOT NULL and UNIQUE
- FOREIGN KEY: It uniquely identifies a tuple in another table.
- CHECK: Ensures that the value in the column meets a given condition.
- DEFAULT: Places a default value when there is no value specified
- INDEX: Created by column to allow faster lookups.<br><br>
![datatypes](https://user-images.githubusercontent.com/26840321/124557040-a6838180-ddfe-11eb-9466-1fd84911d7ad.png)


## Physical diagram: Normalization
### Relational databases are standardized to:
- Avoid data redundancy.
- Reduce data update problems in the tables.
- Protect data integrity.
- Facilitate data access and interpretation.
- Reduce the time and complexity of database revision.
- Optimize storage space.
- Prevent unwanted data deletion.

Normalization helps us to leave everything in a normal way. This obeys Codd's 12 rules and allows us to separate components in the database:<br><br>
<img src="https://user-images.githubusercontent.com/26840321/124559239-201c6f00-de01-11eb-84b3-a91c883868ed.png" alt="alt text" width="40%" height="auto"><br><br>
First normal form (1FN): Atomic attributes (No repeated fields)<br><br>
<img src="https://github.com/brendamrdz/week2-course6-batabase/blob/main/images/primera-forma-normal.jpg?raw=true" alt="alt text" width="40%" height="auto"><br><br>
Second normal form (2FN): Meets 1FN and each field in the table must depend on a unique key.<br><br>
<img src="https://github.com/brendamrdz/week2-course6-batabase/blob/main/images/segunda-forma-normal.jpg?raw=true" alt="alt text" width="40%" height="auto"><br><br>
Third normal form (3FN): Meets 1FN and 2FN and fields that are NOT keys must NOT have dependencies.<br><br>
![datatypes](![image](![image](https://user-images.githubusercontent.com/26840321/124559670-9620d600-de01-11eb-8ad5-c8e360d8a4b5.png)))<br><br>
<img src="https://user-images.githubusercontent.com/26840321/124559670-9620d600-de01-11eb-8ad5-c8e360d8a4b5.png" alt="alt text" width="40%" height="auto"><br><br>
Fourth normal form (4FN): Meets 1FN, 2FN, 3FN and multivalued fields are identified by a unique key.<br><br>
<img src="https://user-images.githubusercontent.com/26840321/124559710-9f11a780-de01-11eb-90a6-fae36f77731e.png" alt="alt text" width="40%" height="auto"><br><br>

## RDBMS 
RDBMS stands for Relational Database Management System. It is a program that follows Codd's rules and can be used programmatically.
There are two ways to access database managers:
- Install on local machine a relational database manager.
- Have special development environments or cloud services.

## SQL
SQL stands for Structured Query Language and has a clear and fixed structure. Its goal is to make a single language for querying any database handle becoming a major standard.
SQL has two major sub-languages:
### DDL or Data Definition Language which helps us to create the structure of a database. There are three main commands:
- Create: Helps us to create databases, tables, views, indexes, etc.
- Alter: Helps to alter or modify entities.
- Drop: Helps us to delete. It is necessary to be careful when using it.


Three objects that we will manipulate with the DDL language:
- Database
```bash
CREATE DATABASE test_db;
USE DATABASE test_db;
```

```bash
ALTER TABLE people
ADD date_of_birth data;
```

- Tables. They are the SQL translation of the entities
```bash
CREATE TABLE people{
person_id int,
last_name varchar(255),
first_name varchar(255),
address varchar(255),
city varchar(255),
}
```
- View: It offers the projection of the data of the database in an understandable way.
```bash
Create View
CREATE VIEW v_brasil_customers AS
SELECT customer_name,
contact_name
FROM customers
WHERE country = "Brasil";
```

### DML deals with the content of the database. It stands for Data Manipulation Language and its commands are:
- Insert: Inserts or adds new records to the table.
```bash
INSERT INTO people (last_name, first_name, address, city)
VALUES (‘Hernandez’,’Laura’, ‘Calle 21’, ‘Monterrey’)
```
- Update: Updates or modifies existing data.
```bash
UPDATE people
SET last_name = ‘Juan’;
```
- Delete: This statement is risky because it can delete the contents of a table.
```bash
DELETE FROM people
WHERE person_id = 1;
DELETE FROM people;

```
- Select: Fetches information from the database.
```bash
SELECT first_name, last_name, FROM people;
```
## FROM
FROM indicates where the data should be fetched from and can help to make complex statements and filters when you want to join tables. The companion statement that helps us with this process is JOIN.
Venn diagrams are circles that touch at some point to see where the intersection of sets is. They help a lot to be able to formulate the JOIN statement in the right way depending on the query you want to do.
<br><br><img src="https://github.com/brendamrdz/week2-course6-batabase/blob/main/images/join.jpg?raw=true" alt="alt text" width="40%" height="auto"><br><br>
## Queries 
Queries are the way in which we structure the questions to be asked to the database. It transforms queries into syntax.
From Question to Query:
- SELECT: What you want to show
- FROM: Where I am going to take the data from
- WHERE: The filters of the data you want to display
- GROUP BY: The headings I want to group the information by
- ORDER BY: The order in which I want to present my information
  - ASC is used to sort in ascending order.
  - DESC is used to sort descending.
- HAVING: The filters I want my grouped data to have

## What are the types of non-relational databases and what are they?
With respect to non-relational databases, there is no single type even though they fall into a single category.
Types of non-relational databases:
- Key-value: They are ideal for storing and extracting data with a unique key. They handle dictionaries exceptionally well. Examples: DynamoDB, Cassandra.
- Document-based: They are a key-value implementation that varies in the semi-structured way in which the information is treated. Ideal for storing JSON and XML data. Examples: MongoDB, Firestore.
- Network-based: Based on graph theory, they are used for entities that are interconnected by multiple relationships. Ideal for storing complex relationships. Examples: neo4j, TITAN.
- In-memory: They can be of varied structure, but their advantage lies in speed, since living in memory, data extraction is almost immediate. Examples: Memcached, Redis.
- Optimized for searches: They can be of various structures, their advantage lies in the fact that complex queries and searches can be performed in a simple way. Examples: BigQuery, Elasticsearch.
