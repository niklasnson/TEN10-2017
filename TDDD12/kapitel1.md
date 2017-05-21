### Database Technology
## Functional dependencies and Normalization

  * *Data:* known facts that can be recorded and that have implicit meaning.
  * *Database:* collection of related data (logically corherent). Represents some aspects of the real world. Built for a specific purpose.


### Problems that database approach adress

  * redundancy: multiple copies
  * inconsistency: independent updates
  * inaccuracy: concurrent updates
  * incompability: multiple formats
  * insecurity: proliferation
  * inaduditability: poor chain of responsibility
  * inflexibilty: changes are difficult to apply

### Defining a Database

  * Specifying the datatypes, structures and constraints of the data to be stored.
  * *meta-data* database definition or descriptive information

### Phases for designing a DB

  * *conceptual design* - using the entity-relationship model
  * *logical desgin* - using the relation model
  * *physical design*

#### An Example

  * data records
    + film
    + person
    + role
    + honors
  * define structure of each type of data record by specifing data elements to include and data type for each element.
    + string
    + numeric
    + date
    + etc


### Characteristics of the DB Approach

  * programs isloated from data through *abstraction*
  * datasharing through multiple *views*
  * multiuser *transaction* processing
  * data is *self-defining* (meta-data)

### Summary
Defined database as a collection of related data, where data means recorded facts. A typical database represents some aspect of the real world and is used for specific purpose by one or mpre groups of users.

### Questions

### Definitions

  * *DDL* - data definition language
  * *DBA* -
  * *DBMS* - database managment system
  * *SDL* - storage definition language
  * *VDL* - view definition language
  * *DML* - data manipulation language


### Database Technology
## Relational Databases and SQL


### Relational Data Model

Relational database: represent data as a collection of relations.
Schema describes the reelation
Instance denotes the current ontents of the relation (also called state).

#### Relation schema
  * A relation named R and a list of attributes A1, A2, ..., An
  * Denoted by R(A1, A2, ..., An)

#### Attribute Ai
  * Name of the role in the relation schema R
  * Associated with a domain dom(Ai)
  * Attribute names do not repeat within a relation schema, but domains can repeat.

#### Degree (or arity) of a relation
  * Number of attributes n in its relationship schema.

#### NULL Values
  * Each domain may be augmented with a special value called NULL
    + Represents the values of attrubuytes that may be uknnown or may not apply to a tuple.
    + if an attribute of a tuple is NULL, we cannot make any assumption about the value for that attribute (for that tuple)
  * Interpretations for NULL values
    + Nothing is known about the value
    + Value exists but is (currently) not avelibal
    + Value undefiend (i.e attrubute does not applu to this tuple)
  * For instance, Ashley's numer is NULL could mean
    + Ashley dosen´t have a phone
    + Ashley has a phone but we don´t know the number (perhaps withheld)
    + Ashley has a phone that has no number

### Integrity Constarints
What are Integrity Constarints?
  * Constarints are restrictions on the permitted value in a DB state
    + Derived from the rules in the miniworld that the DB represents
  * Inherent model-based constraints (also called implicit constaraints)
    + Inherent in the data model
    + e.g. duplicate tuples are not allowed in a relation
  * Schema-based constraints (also called explicit constaraints)
    + Can be directly expressed in schemas of the data model
    + e.g. films only have one director
    + our focus here
  * Application-based (also sementic constaraints or buisness rules)
    + Not direclty expressed in schemas
    + Expressed and enforced by application program
    + e.g. this years sallary increased can be more than last year´s

Key Constarints

  * Uniqueness constaraints on tuples
    + Key of a relation R is a set K of attributes of R taht has two properties
      + Uniqueness: No two distinct tuples have the same values across all attributes in K (i e it is a super key)
      + Minimality: No subset of K has the uniqueness property
    + Super key: set or attributes that has the uniqueness property
  * Keys declared as property of the schema of a relation
    + Uniqueness must hold in all valid states
    + Serve as a constraint on updates
  * Candidate key: if there is more than one key i a relation, every key is called a candidate key.
  * Primary key: a particular candidate key is chosen as the primary:
    + Diagrammatically, underline its attribute(s)
    + Tuples cannot have NULL for any primary key attribute
  * Other candidate keys are designated as unique
    + non-NULL values cannot repeat, but values may be NULL.
  * Entity integrity constraint: no primary key value can be NULL
  * Domain constraint: declared ny specifying the datatype of attribute
  * Referential integrity constraint
    + Specified between two relations
    + Allows tuples in one relation to refer to tupels in another
    + Maintains consistency among tuples in two relations
  * Foreign key rules:
    + Let PK be the primary key in a relation R1
    + Let FK be a set of attributs for another relation R2
    + The attribute(s) FK have the same domain(s) as the attribute(s) PK
    + Value of FK in a tuple t2 of the current state or R2 either occurs as a value of PK for some tuple t1 in the current state of R1 or it is NULL

#### Cardinality Ratios for Binary Relationships
The *cardinality ratio* for a binary relationship specifies the maximum number of relationship that an entity ca participiate in. Example in a WORK_FOR binary relationship type, DEPARTMENT:EMPLOYEE is of carinatality 1:N meaning a department can have many employees but a emplyee can only be a part of one department.

  * 1:1
  * 1:N
  * N:1
  * M:N

### Database Technology
## Introduction to SQL Programming Techniques

### SQL

#### Cursors

A cursor is a variable that refers to a single tuple (row) from aquery result that retrives a collection of tuples. The cursor is declered when the SQL query is declared.

### SQL DDL

### SQL Queries

``` sql
CREATE TABLE <tablename> (<colname><datatype>[<constraint>]);

CREATE TABLE Persons (
    PersonID int,
    LastName varchar(255),
    FirstName varchar(255),
    Address varchar(255),
    City varchar(255)
);

```

``` sql
SELECT    (distinct) <return list>
FROM      <table list>
[WHERE    <condition>];

LOGICAL OPERATORS: <and> <or> <not>
PATTER MATCHING  : '%<like>%'
```

``` sql
SELECT    <return list>
FROM      <table list> (E)
UNION
SELECT    <return list>
FROM      <table list> (D)

(E)(D) << will return values matching in both E and D
```

``` sql
SELECT A,B
FROM X,Y
/* selcting A(x), B(y) */
```


``` sql
SELECT * FROM customer LEFT JOIN sale ON customer.id = sale.custid;
```

``` sql
SELECT lname FROM emplyees WHERE ssn NOT IN (SELECT id FROM works_on WHERE ssn = essn)
```

``` sql
AVG()
SUM()
MIN()
MAX()
COUNT()
```

``` sql
WHERE IS NULL
WHERE <> NULL
```

``` sql
INSERT INTO <table> (<attr>, ...) VALUES (<val>, ...);
```

``` sql
UPDATE <table> SET <attr> = <val>, ...
       WHERE <condition>;
UPDATE <table> SET (<attr>, ...) = (<subquery>)
       WHERE <condition>;
```

``` sql
DELETE FROM <table> WHERE <condition>;
```

#### Views

``` sql
CREATE VIEW <name> AS
       SELECT <attr>
   FROM <table>
   GROUP BY <attr>
```

### Definitions

  * *atomic* - each value indivisible. i.a simple, can not be split to smaller parts.
  * *tupele*
  * *schema*
  * *attribute*
  * *domain* - set of atomic values
  * *instance*
  * *tuple* -





### Database Technology
## Entity Relationship (ER) Modeling

  * Entity: a "thing" in the real world with an independent existence
  * Attributes: properties that describe an entity
  * Entity type: A collection of entities that have the same set of attributes

##### Attributes

  * simple vs composite
  * single-valued vs multivalued
  * stored vs derived

![f 3.14](http://i.imgur.com/0TiJHecl.jpg)
![f 3.15](http://i.imgur.com/7Srft4Jl.jpg)

## Enhanced Entity Relationship (EER) Modeling

![f 4.19](http://i.imgur.com/zAANrFKl.jpg)

#### Summary
   * Entity-relationship (ER) model: a graphical way to model the world.
   * Main concepts:
     + Entity type
     + Relationship type
     + Attributes
   * Diffrent types of constraints
   * Enhanced ER model


### Database Technology
## Functional Dependencies and Normalization

#### Motivation
   * How can we be sure that the translation of an EER diagram into a relational schema results in a good database design ?
   * Given a deployed database, how can we be sure that it is well-designed?
   * What is a good database design ?
     + Informal measures
     + Formal measure: normal forms

#### Informal Design Guidelines for Relation Schemas

  * making sure the sematecs of attributes is clear in the schema
  * Reducing the redundant information in tuples
  * Reducing the NULL values in tuples
  * Disallowing the possible of generating spurious tuples


#### Foundations of Formal Measures




``` sql
R(pid, personname, country, continent, continentarea, numbervisitscountry)

fd1: pid -> personname
fd2: pid, country -> numbervisitscountry
fd3: country -> continent
fd4: continent -> continentarea
```

#### Identifying Functional Dependencies


#### Trivial Functional Dependencies
   * Some dependencies must always hold
     + {name, yearofbirth} -> {name, yearofbirth}
     + {name, yearofbirth} -> {name}
     + {name, yearofbirth} -> {yearofbirth}

   * Formally
     + Let R be a relation schema, and
     + Let X and Y be subsets of attributes in R
     + If Y is a subset of X, then X -> Y holds trivially

``` sql
Reflexivity: If Y is a subset pf X, then X -> Y
Augmention: If X -> Y, then XZ -> YZ (we use XY as a short from  for X U Y )
Transitivity: If X -> Y and Y -> Z, then X -> Y

Additional rules can be derivied:

Decomposition: If X -> YZ, then X -> Y
Union: If X -> Y and X -> Z, then X -> YZ
Pseudo-transivity: If X -> Y and WY -> Z, then WX -> Z
```
#### Revisiting Keys

``` sql
```

#### Computing (Super) Keys
``` sql
```

### Database Technology
## Normal Forms and Normalization

#### Overview

  * 1NF, 2NF, 3NF BCNF (4NF, 5NF)
  * Relation in higher normal form also satisfies the conditions of every lower noraml form
  * The higher the normal form, the less the redundancy
  * 3NF and BCNF are our formal measure of good database design
    + Reduce redundancy
    + Reduce update anomalies
  * Normalization: process of turning a set of relations that are in lower normal forms into relations that are in the higher normal forms

#### First Normal Form (1NF)

*Definition:* Relational schema is in 1NF if it does not allow for non-atomic values

First normal form (1NF) is a property of a relation in a relational database. A relation is in first normal form if and only if the domain of each attribute contains only atomic (indivisible) values, and the value of each attribute contains only a single value from that domain.

*First normal form enforces these criteria:*

  * Eliminate repeating groups in individual tables.
  * Create a separate table for each set of related data.
  * Identify each set of related data with a primary key


``` sql
[id, name, livesin]
{1 , petterson, {stockholm, linköping}}

-> (Decompose)

[id, name] => {1, petterson}
[id, livesin] => [{1, stockholm}, {1, linköping}]
```

#### Second Normal Form (2NF)

*Definition:* Relationship schema R is in 2NF if it is in 1NF and it does not have any non-prime attributes that are functionally dependent on a part of a candidate key.

A relation that is in first normal form (1NF) must meet additional criteria if it is to qualify for second normal form. Specifically: a relation is in 2NF if it is in 1NF and no non-prime attribute is dependent on any proper subset of any candidate key of the relation. A non-prime attribute of a relation is an attribute that is not a part of any candidate key of the relation.

A functional dependency on part of any candidate key is a violation of 2NF. In addition to the primary key, the relation may contain other candidate keys; it is necessary to establish that no non-prime attributes have part-key dependencies on any of these candidate keys.

``` sql
[empid, dept, work%, empname]

fd1: empid -> empname
fd2: {empid, dept} -> {work%, empname}
```

  * Why do we want to avoid such a functional dependency in R?
    + Part of the candidate key can have repetade values
    + Then, so will have the non-prime attributes that depend on the part

#### Example 1

``` sql
[empid, dept, work%, empname]

-> (Decompose)

[empid, empname]
[empid, dept, work%]

fd3: {empid, dept} -> {work%}
```

#### Example 2
In this example we can see that redudant data could be in the database if we have same manufactor selling two models, made in the same factory.

``` sql
[manufacturer, model, model_full_name, manufacturer_country]

-> (Decompose)
[manufacturer, model, model_full_name]
[manufacturer, manufacturer_country]

/*
Even if the designer has specified the primary key as {Model Full Name}, the relation is not in 2NF
because of the other candidate keys. {Manufacturer, Model} is also a candidate key, and Manufacturer
Country is dependent on a proper subset of it: Manufacturer. To make the design conform to 2NF, it
is necessary to have two relations.
*/

```


#### Third Normal Form (3NF)

*Definition:* Relation schema R is in 3NF if it is in 1NF and it does not have any non-prime attributes that are functionally dependent on a set of attributes that is not a superkey

Third normal form is a normal form that is used in normalizing a database design to reduce the duplication of data and ensure referential integrity by ensuring that (1) the entity is in second normal form, and (2) all the attributes in a table are determined only by the candidate keys of that relation and not by any non-prime attributes. 3NF was designed to improve database processing while minimizing storage costs. 3NF data modeling was ideal for online transaction processing (OLTP) applications with heavy order entry type of need.

``` sql
[id, name, zip, city]

fd1: zip -> city
fd2: id -> {name, zip, city}
```

  * Why do we want to avoid such a functional dependency in R?
    + Set of attributes that is not a candidate key can have repeted values
    + Then, so will have the non-prime attributes that depend on it
    + Hence, redundancy and, thus, waste of space and update anomalies

#### Example 1

``` sql
[id, name, zip, city]

-> (Decompose)

[zip, city]
[id, name, zip]

fd3: id -> {name, zip}
```

#### Example 2

``` sql
[tournament, year, winner, winner_date_of_birth]

-> (Decompose)

[tournament, yar, winner]
[winner, date_of_birth]

/*

Update anomalies cannot occur in these tables, because unlike before, Winner is now a primary key in the
second table, thus allowing only one value for Date of Birth for each Winner.

*/

```

#### Boyce-Codd Normal Form (BCNF)

*Definition:* Relation schema R is in BCNF if it is in 1NF and for every FD X -> Y on R we have that X is a superkey

``` sql
Example: Let R(_A_,_B_,C,D) be a relation schema with AB -> CD and C -> B
AB is a candidate key and so is AC
R is in 3NF (D is the only non-prime attribute and AB is cand. key)
R is not BCNF (becouse C is not a candidate key)

```

### Database Technology
## Triggers and Stored Procedures

#### Triggers

*What are Triggers?*

  * Specify actions to be performed by the DBMS when certain events and conditions occur
  * Used to monitor the DB and enforce buisness rules
    + Raise an alarm
    + Enforce a constraint
    + Update derived data in (possible some other) table
  * Typicallu, triggers consist of three components
    + Event: update operations that activate the trigger
    + Condition: determinates if action should be executed
    + Acton: specifies what to do (e.g., execute stored procedure, perform sequence of SQL statements)

``` sql
CREATE TRIGGER <name>
BEFORE {INSERT|UPDATE|DELETE} ON <table>
FOR EACH ROW
WHEN <statement>

SHOW TRIGGERS;
DROP TRIGGER <trigger>;
```

#### Stored Procedures

*Stored Procedures - What and Why*

``` sql
CREATE PROCEDURE <proc. name> (<params>)
<local declarations>
<procedure body>;
```

``` sql
CREATE FUNCTION <function name> (<params>)
RETURNS <return type>
<local declarations>
<procedure body>;
```

  * SQL/PSM: a set of extensions to SQL
    + General-purpose programming constructs in SQL
    + Can be used to write stored procedures
  * Lots of features
    + Conditinal branching
      + IF ... THEN ... [ ELSE ... ] END IF;
      + CASE ... WHEN ... THEN ... [ ... ] END CASE;
    + Looping
      + WHILE ... DO ... END WHILE;
      + REPEAT ... UNTIL ... END REPEAT;
  * etc

### Summary

  * Triggers: specify actions to be performed by DBMS when certain events and conditions occur
    + Used to monitor the DB, enforce buisness rules
    + Consist of event, condition, and action
  * Stored procedures: program modules stored in DBMS
    + SQL commands
    + General-purpose programming constructs

### Database Technology
## Data Structures for Databases

#### Storage Hierarchy

Properties of Using Magnetic Disks

  * Formatting divided the hard-coded sector into equal-size blocks
    + Block is the unit of data transfer between disk and main memory
    + Typlical block sizes: 512-8192 bytes
  * Read/write from/to disk i a major bottleneck!
    + r/w time = seektime + rotational delay + block transfer time
    + cpu intruction: ca 1 ns
    + main memory access: ca 10 ns
    + disk access: 1 ms

### Files and Records

#### Terminology

  * Data stored in files
  * File is a sequence of records
  * Records are allocated to file blocks
  * Record is a set of field values
  * For instance,
    + File = relation
    + Record = row
    + Field = attribute value

#### Blocking Factor

  * Blocking factor (bfr) is the number of records per block
  * Assume
    + r is the number of records in a file
    + R is yje size of a reecord, and
    + B is the block size in bytes,
    + then
    + bfr = [B/R]
  * Blocks needed to store the file = b = [r/bfr]
  * Space wasted per block = B - bfr * R

#### Buffer Replacement Strategies

  * Least recentlyused (LRU)
  * Clock policy
  * First-in-first-out (FIFO)
  * Most recently used (MRU)

##### Spanned Records

  ... avoid wasting spaace


![16.6](http://i.imgur.com/ehmpV8gl.jpg?216.6)
