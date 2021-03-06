### Database Technology
## Introduction, The Database Approach

  * *Data:* known facts that can be recorded and that have implicit meaning.
  * *Database:* collection of related data (logically corherent).
    + Represents some aspects of the real world.
    + Built for a specific purpose.


### Problems that database approach adress

  * redundancy: multiple copies
  * inconsistency: independent updates
  * inaccuracy: concurrent updates
  * incompability: multiple formats
  * insecurity: proliferation
  * inaduditability: poor chain of responsibility
  * inflexibilty: changes are difficult to apply

### Characteristics of the DB Approach

  * Program isolated from data through _abstraction_
    + Does not expose details of (or where) data is stored or how operations are implemented
    + Data sharing through multiple views
  * Multiuser transaction processing



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
  * *schema*
  * *attribute*
  * *domain* - set of atomic values
  * *instance*
  * *tuple* -





### Database Technology
## Topic 3: Entity Relationship (ER) Modeling

  * Entity: a "thing" in the real world with an independent existence
  * Attributes: properties that describe an entity
  * Entity type: A collection of entities that have the same set of attributes

##### Attributes

  * simple vs composite
  * single-valued vs multivalued
  * stored vs derived

![f 3.14](http://i.imgur.com/0TiJHecl.jpg)

```
(o) : [completeness (or totalness)] this means that the member _of least_ one of the subclass in the specialization.
(d) : [disjointness constraints] this means that the member can be _at most_ one of the subclasses of the specification.
(u) : [union or (category)] this means that the subset must be in _only one_ of the superclasses.

  * Disjoint, total
  * Disjoint, partial
  * Overlapping, total
  * Overlapping, partial
  * Categorry, total - a
  * Category, partial
```

``` sql
<A> - N - 1 <B>  ; lägg id his den som har 1 relationen (här a)
<A> - M - N <B>  : måste ha en egen tabell
```


A week entity is where part of the key belongs to another entity. Example:

```
[Date, Type, Id] (DrivingLicence)

       |

[TaxiCertDate] (Driver)

Where then DrivingLicence is a must in the relation.

```

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

##### Translation of EER to relational schema:

![Translation of EER to relational schema](http://i.imgur.com/3hNAcvRl.jpg)

_notes:_

  * phone becomes a table
  * havefun is a M<>N and also becomes a table


![Translation of EER to relational schema](http://i.imgur.com/SmGE4n5l.jpg)

_notes:_

  * Supply has a N<>1 relation and does not need a special table (supplies) (N -> sid)
  * Supplied has a N<>1 relation and does not need a special table (supplied) (N -> pid)



#### Important

  * What is a weak entity type ?
    + It must use a foreign key in conjunction with its attributes to create a primary key
    + In a ER diagram a weak entity is indicated by a bold (or double-lined) rectangle
  * What is a subclass ?
    + Entity type Y is a subtype (subclass) of an entity type X if and only if every Y is necessarily an X. A subclass entity inherits all attributes and relationships of its superclass entity


### Database Technology
## Topic 4: Mapping of EER Diagrams to Realtions

#### Step 1: Map Regular Entity Types

  * For each regular entity type, create a relation schema R that includes all the single-valued attributes of E
    + Flatten composite attributes
    + Example renames some attributes, but not needed
    + Pick one of the keys as primary key, declare other to be unique
    + Resulting relations are called entity relations
    + Each tuple represents an entity instance

[ todo: behöver mer information ]

#### Step 2: Map Weak Entity Types

  * For each weak entity type, create a relation schema R
    + Include all single-valued attributes of the weak entity type and of the identifing relationship as attributes of R
    + Include primary key attribute of identifying entity as foregin key attribute R
    + Primary key of R is primary key of identifying entity together with partial key from R
  * Omit the identifying relationship when subsequently transalating (other) relationship types to realtion schemas.

[ todo: behöver mer information ]

#### Step 3: Binary 1:1 Relationship Types

  * For each binary 1:1 relationship type R, identify relation schemas that corresponds to entity types participating in R
  * Apply one of three possible approaches:
    + 1) Foregin key approach
      + Add primary key of one participating relation as foregin key attribute of the other, which will aslo be represent R
        + If only one side is total, choose it to represent R
      + Declare foregin key attribute as unique

  * For each binary 1:1 relationship type R, identify relation schemas that correspond to entity types participating in R
  * Apply one of three possible approach
    + Merged relationshop approach
      +


![Transactions to EER](http://i.imgur.com/ELPUWBXl.jpg)

[ todo: behöver mer information ]

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
(ref) Reflexivity: If Y is a subset pf X, then X -> Y

(aug) Augmention: If X -> Y, then XZ -> YZ (we use XY as a short from  for X U Y )

(tra) Transitivity: If X -> Y and Y -> Z, then X -> Y

(add) Additional rules can be derivied:

(dec) Decomposition: If X -> YZ, then X -> Y

(uni) Union: If X -> Y and X -> Z, then X -> YZ

(ptr) Pseudo-transivity: If X -> Y and WY -> Z, then WX -> Z
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


#### Allocating File Blocks on Disk

  * Contiguous allocation: file blocks allocated consecutiverly (one after another)
    + Fast sequential access, but expanding is difficult
  * Linked allocation: each block contains a pointer to the next one
    + Expanding the file is easy, but reading is slower
  * Linked clusters allocation: hybrid of the two above
    + i.e., linked clusters of consecutive blocks
  * index allocation: index blocks contains pointers to the actual file blocks


### File Organization

#### Heap Files

  * Records are added to the end of the file
  * Adding a record is cheap
  * Retriving, removing, and updating a record si expensive because it implies liner search
    + Avrage case: (b/2) block access
    + Worst case: b block accesses (recall, b is the number of blocks of the file)
  * Record removal also implies waste of space
    + Periodic reorganization

#### Sorted Files

  * Records orded according to some field
  * Orded record retrical is cheap
    + All the records: access the blocks sequentially
    + Next record: probably in the same block
    + Random record: binary search (log 2b) block access in the worst case
  * Adding a record is expansive, but removing is less expensive (deletion markers and periodic reorganization)

#### Binary Search


     [ 2, 5, 8 , 12, 16, 23, 38, 56, 72, 91]

23>16
take 1st half:

      L                                  H

     [ 2, 5, 8 , 12, 16, 23, 38, 56, 72, 91]

23 < 56
take 1st half:

                         L               H

     [ 2, 5, 8 , 12, 16, 23, 38, 56, 72, 91]

Found 23

                         L    H
     [ 2, 5, 8 , 12, 16, 23, 38, 56, 72, 91]


Standard version:

``` python
binary_search(A, target):
   lo = 1, hi = size(A)
   while lo <= hi:
      mid = lo + (hi-lo)/2
      if A[mid] == target:
         return mid
      else if A[mid] < target:
         lo = mid+1
      else:
         hi = mid-1

   // target was not found
```


Improved version:

``` python
binary_search(lo, hi, p):
   while lo < hi:
      mid = lo + (hi-lo)/2
      if p(mid) == true:
         hi = mid
      else:
         lo = mid+1

   if p(lo) == false:
      complain                // p(x) is false for all x in S!

   return lo         // lo is the least x for which p(x) is true
```

#### Internal Hashing

  * Choose a field of th erecords to be the hash field
  * Applying hash function h to the vlue x of the hash field returns the position of the record in the file
    + eg. h(x) = x mod r (recall, r is the number of records in the file)
  * Collision: diffrent field values hash to the same position
  * Sollution to deal with collision
    + Check subsequent positions until one is empty
    + Use a second hash function
    + Put the record in an overflow area and link it

#### External Hashing

  * Hashing for disk files
  * Applying hash function to the value of the hash field return a bucket number (insted of a position)
    + Bucket: one or serveral contiguous disk blocks
    + Table converts bucket number into address of block
  * Collisions are typically resolved via overflow area
  * Cheapest random retrival (when searching for equality)
  * Order record retrival is expensive

### Indexes

#### Overview

  * Seen so far: file organization
    + Analogous to organization of books into chapers, ections, etc.
    + Determines primary method to access data in a files
      + e.g., squential search, binary serach
  * Now: index structures
    + Allow for secondary access methods
    + Analogous to the index of a book
    + Goal: speed up access under specific conditions
    + Outline:
      + Single-level ordered indexes (primary, secondary, and clustiring indexes)
      + Multilevel indexes
      + Dynamic multilevel indexes (B+-trees)


The idea behind an orded index is similar to that behind the index used in a textbook, which lists important terms at the end of the book in alphabetical order along with a list of page numbers where the rerm appears in the book. We can search the book index for a certain term in the textbook to find a list of adresses - page numbers in this case- and use these to locate a specified pages first and then search for the term on each speciefied page.

The alternative, if no other guidance is given, would be to sift slowly through the whole textbook word by word to find the term we are interested in; this corresponds to doing a linear search, which scans the whole file.

##### Primary Index

![17.1](http://i.imgur.com/TAGUDnZl.jpg)

A primary index is an ordered file whose records are of fixed length with two fields, and it acts like n access structure to eeiciently search fo and access the data records n a data file.
The first field is of the same data type as the ordering key field - called the primary key - of the data file, and the second field is a pointer to a disk block (a block address).

  * Assumptions:
    + Data file is sorted
    + Ordering field F is a key
  * Primary index: an additional sorted file whose records contain two fields:
    + V - one of the values in F
    + P - pointer to a disk block of teh data file
  * One index record (V,P) per data block such that the first data record in the data block pointed to by P has V as the value of the ordering key F
  * Why is it faster to access a random record via a binary search in the index than in the data file?
    + Number of index records << number of data records
    + Index records smaller than data records (i.e., higher blocking factor for the index file than for the data file)

  * What is the cost of maintaining a primary index ? (if the order of the data records changes?)

##### Clusering Index

![17.2](http://i.imgur.com/bT651f3l.jpg)

If file records are physically ordered on a nonkey field - which does not have a distinct value for each record - that field ins called the _clusering field_ and the data file is called a _clustered file_. We can create a different type of index, called a _clustering index_, to speed up retrival if all the records that have the same value for the clustering field. This differs from a primary index, which requires that the ordering field of the data file have a _distinct value_ for each record.

  * Assumptions:
    + Data file is sorted
    + Ordering field F is _not_ a key (hence we cannot assume distinct values)
  * Clusering index: additional sorted file whose records contain two fields:
    + V - one of the values of F
    + P - pointer to a disk block of teh data file
  * One index record (V,P) for each distinct value V of the ordering field F such that P points to the first data block in which V appears

  * Efficiency gain?
  * Maintence cost ?


![17.3](http://i.imgur.com/kItsnnll.jpg)


##### Index Creation

``` sql
CREATE [UNIQUE] INDEX <index name> ON <table name> (<column name> [<order>] {, <column name} [<order>]})
[CLUSTER];
```

 #### Summary

Three types of ordered single-level indexes were introduced: primary, clustering, and secondary. Each index is specified on a field of the file. primary and clustering indexes are constructed on the physical ordering field of a file, whereas secondary indexes are specified on nonordering fields as additional access structures to improve performace of queries and transactions.

The field for a primary index must also be a key of this file, whereas it is a nonkey field for clustering index. A single-level index is an ordered file and is searcged using binary search.

#### Secondary Indexes on Key Field

  * Index on a non-ordering key field F
    + Data file may be sorted or not
  * Secondary index: additional sorted file whose records contain two fields:
    + V - one of the values of F
    + P - pointer to a disk block of teh data file
  * One index record per data record

#### Secondary Indexes on Non-Key

  *

#### Summary of Single-Level Indexes

```
                                Index field used for            Index field not used for
                                ordering the data file          ordering the data file

Index field is key              primary index                   secondary index (key)

Index field is not key          clustering index                secondary index (non-key)

```

#### Multilevel Indexs

  * Index on index (first level, second level, etc.)
  * Works for primary, clustering, and secondary indexes as long as the first-level index has a distinct index value for every entry
  * How many levels?
    + Until the last level fits into a single disk block
  * How many disk block accesses to retrive a random record?
    + Number of index levels + 1
  * When using a (static) multilevel index , record insertation, deletion, and update may be expensive because all the index levels are _sorted files_
  * Solutions:
    + Overflow area + periodic reorganization
    + Dynamic multilevel indexes taht leave some space in index block for new entries (e.g., B-trees and B+-trees)


### Database Technology
## Dynamix Multilevel Indexes (B-trees and B+-trees)

#### Search Trees

  * Used to guide the search for a record
    + Generalization of binary search

#### B-Trees

  * B-Tree is a variant of a balanced search tree
    + Balanced: all leaf nodes are the same level (why is this good?)
  * Additional constraints:
    + In addition to a tree pointer P(i), each key value K(i) is associated with data pointer Pr(i) to the record with value K(i)
    + Each internal node must have atelast [P/2] tree pointers (i.e., is at least half full)

#### B+-Trees

  * Variation of B-trees, most commonly used
  * In contrast to a B-tree, in a B+tree the leaf nodes are diffrent from the internal nodes; that is:
    + Internal nodes have key values and tree pointers only (no data pointers)
    + Leaves have key values and data pointers
    + Usually, each leaf node additionally has a ponter to the next leaf to alow for ordered access (much like a linked list)
  * Every key value is present in one of the leaves
  * Of course, B+-trees are balanced


#### Summary

  * Storage hierarchy
    + Accessing disk is major bottleneck
  * Organizing records in files
    + Heap files, sorted files, hash files
  * Indexes
    + Additional sorted files that efficient secondary access methods
  * Primary, secondary, and clustering indexes
  * Multilevel indexes
    + Retrival requires reading fewer blocks
  * Dynamic multilevel indexes
    + Leave some space in index blocks for new entries
    + B-tree and B+tree

### Database Technology
## Intoduction to Transaction Processing

##### Motivation

  * A DB is a _shared_ resource accessed by many users and processes _concurrently_
  * Not managing concurrent access to a shared resource will cause problems (not unlike operating systems)
  * Transaction processing is about avoiding problems caused by
    + concurrency
    + failure

##### Transaction

  * An application-speciefied, _atomic_ and _durable_ unit of work (a process) that comprises one or more database accesss operations
  * Example for a banking database: Transfer $100 from a checking account to a savings account
  * Characteristic operations
    + Reads (database retrival, such as SELECT)
    + Write (modify DB, such as INSERT, UPDATE, DELETE)

##### Terminalogy

  * ONline Tranaction Processing (OLTP) systems: large multi-user database systems supporting thousands of concurrent transactions (user processes) per minute
  * Transfer boundaries
    + BEGIN_TRANSACTION
    + END_TRANSACTION
  * Transactions can end in one of two states:
    + Commit: transaction completes successfully and all its results are made permanent
    + Abort: transaction does not complete and none of its actions are reflected on the database


#### Tranaction Processing Model

  *  read_item(X): reads item X into a program variable (for simplicity, assume that the variable is also named X)
  *  write_item(X): write the value of program variable X into the database item named X
  *  These operations take some ammount of time to execute
  *  Basic unit of data transfer between the disk and the computer main memory is a disk block

##### Standalone vs Embedded TAs

  * Tranactions may be _standalone_
    + speciefied in a high-level language like SQL, submitted interactively
  * More typically, transactions are _embedded_ within application programs
    + Application program may include specification of severak transactions, seperated by Begin and End transaction boundaries
    + Tranaction code can be executed several times (e.g., in a loop), spawning multiple transactions

##### ACID Properties
_ACID_ - atomicity, consistency preservation, isolation, and durability or permanency

### Database Technology
## Topic 9: Transactions and Concurrency Control

One criterion for classifying a database system is according to the number of users who can use the system _concurrently_. Single-user DBMS are moslty restricted to personal computer systems; most other DBMSs are multiuser. Multiple users can access database - and user computer systems - simultaneously because of the concept of _multiprogramming_, which allows the operating system of the computer to execute multiple programs - or _processes_ at the same time.

##### Transactions
A _transaction_ is an executing program that forms a  logical unit of database processing. A transaction includes one or more database access operations - these can include insertation, deletion, modification (update), or retrieval operations. One way of doing this is using _begin transaction_ and _end transaction_.

If the database operations in a transaction do not update the database but only retrive data, the transaction is called a _read-only transaction_; otherwise it is known as a _read-write transaction_.

##### Steps of Read / Write Operations

  * read_item(x)
    + Find address of the disk block that contrains item X
    + Copy the disk block into a buffer in main memory (if the block is not already in main memory)
    + Copy item X from the buffer to the program variable X

  * write_item(x)
    + Find adress of the disk block that contains item X
    + Copy the disk block into a buffer in main memory (if the block is not already in main memory)
    + Copy item X from the program variable named X into its correct location in the buffer
    + Store the updated block from the buffer back to disk (either immediately or at some later point in time)


#### Example

Initial value on checking is $500;

| # | at ATM window #1            | at ATM windows #2              |
| - | --------------------------- | ------------------------------ |
| 1 | read_item(savings);         |                                |
| 2 | savings = savings - $100;   |                                |
| 3 |                             |                                |
| 4 | write_item(savings);        | read_item(checking);           |
| 5 | read_item(checking);        |                                |
| 6 |                             | checking = checking - $20;     |
| 7 |                             | write_item(checking);          |
| 8 | checking = checking + $100  |                                |
| 9 | write_item(checking);       |                                |
| 10 |                            | dispense $20 to customer       |


#### Discussion

The result will be $600 on checking - #1@5 will overwrite the changes.


##### Why Concurrency Control Is Needed
Take the example with the airline, if two instances passes the IF seats avelibal at the same time, we can overbook (problem!).

###### The lost update problem
This problem occurs when two transactions that access the same database items have their operations interleaved in a way that makes the value of some database items incorrect.

###### The temporary update (or dirty read) problem
This problem occurs when one transaction updates a database item and then the transaction updates a database item and then the transaction fails for some reason. Meanwhile, the updated item is accessed (read)  by another transaction before it is changed back (or rolled back) to its original value.
###### The incorrect summary problem
If one transaction is calculating an aggregate summary function on a number of database items while other transactions are updating some of these items, the aggregate function may calculate some values before they are updated and other after they are updated.


###### Types of Failures

  * A computer failure (system crash)
  * A transaction or system error
  * Local errors or exception conditions detected by the transaction
  * Concurrency control enforcement
  * Disk failure
  * Physical problems and catastrophes

###### Transaction States

  * BEGIN_TRANSACTION
  * READ or WRITE
  * END_TRANSACTION
  * COMMIT_TRANSACTION
  * ROLLBACK or ABORT

#### Summary

The main goal of recovery is to ensure the atomicity property of transactions. If a transaction fails before completing it execution, the recovery mechanism has to make sure that the transaction has no lasting effects on the database.

###### Deferred Update

  * A transaction can not change the database on disk until it reaches it commit point; hence all buffers that have been changed by the tranaction must be pinned until the tranaction commits (this corresponds to a _no-steal policy_)
  * A transaction does not reach its commit point until all its _READO-type_ log entries are recorded in the log and the log buffer is force-written to disk.

Notice that step 2 of this protocol is a restatement of the write.ahead logging (WAL) protocol. Because the database is never updated on disk until after the transaction commits, there is never a need to UNDO any operations. REDO is needed in case the system fails after a transaction commits but all its changes are recorded in the database on disk. In this case, the transaction operations are redone from the log entries during recovery.

###### Immediate Update

In these techniques, when a transaction issues an update command, the database on disk can be updated _immediately_, without any need to wait for the transaction to reach its commit point. Notice that is is _not a requierment_ that every update be applied immediatly to disk; it is just possible that some updates are applied to disk _before the tranaction commits_


![](http://i.imgur.com/hlOzcdRl.jpg)

![](http://i.imgur.com/gFh90PDl.jpg)



#### Accepable Interleavings (Serializability)

##### Confilicts and Equivalance

Defintiion: Two operations conflict if
  * they access the same data item X
  * they are from two diffrent transactions, and
  * at least one of them is a write operation.

Defintiion: Two schedules are conflict equivalent if the relative order of any two conflicting operations is the same in both schedules.

#### Serializability

Definition: A schedule with n transactions is serializable if it is conflict equivalent to some serial schedule of the same (n) transactions.

  * Serializable schedule “correct” because equivalent to some serial schedule, and any serial schedule acceptable
    + Transactions see data as if they were executed serially
    + Transactions leave DB state as if they were executed serially (hence, serializable schedules will leave the database in a consistent state)
  * Efficiency achievable through interleaving and concurrent execution

#### Testing Serializable


  * Construct a serialization graph for the schedule
    + Node for each transaction in the schedule
    + Direct edge from Ti to Tj if some read or write operation in Ti appears before a conflicting operation in Tj
  * A schedule is serializable if and only if its serialization graph has not cycles

![1](http://i.imgur.com/19RoPx9l.jpg)

![2](http://i.imgur.com/IlsrFtel.jpg)

![3](http://i.imgur.com/vwqs2Xgl.jpg)

![4](http://i.imgur.com/WH6oa9gl.jpg)

#### Locking Techniques for Concurrency Control


##### 2PL

  * Sätt alla lås innan de börjar användast (lås i början av tråd, lås upp i slutet)
  * Använd rl om vi bara läser, använd wl om vi skriver (eller läser)
  * Lås upp i slutet av tråden.

##### Deadlock

  * Two or more transactions wait for one another to unlock some data item
    + Ti waits for Tj waits for … waits for Tn waits for Ti
  * Deadlock prevention:
    + Conservative 2PL protocol: Wait until you can lock all the data to be used beforehand
    + Wait-die
    + Wound-wait
    + No waiting
    + Cautious waiting
  * Deadlock detection:
    + Wait-for graph
    + timeouts

##### Starvation

  * A transaction is not executed for an indefinite period of time while other transactions are executed normally
    + e.g., T waits for write lock and other TAs repeatedly grab read locks before all read locks are released
  * Starvation prevention:
    + First-come-first-served waiting scheme
    + Wait-die
    + Wound-wait
    + etc.

##### Summary

  * Characterizing schedules based on serializability
    + Serial and non-serial schedules
    + Conflict equivalence of schedules
    + Serialization graph

  * Two-phase locking
    + Guarantees conflict serializability
    + Possible problems: _deadlocks and starvation_

##### Questions

  * Is the schedule above serializable ? Explain why or why not.
  * 2. If the transactions in a schedule interleave the same before and after applying the two-phase locking protocol, then the schedule is serializable. True or false ?

##### Notes

  * Starvation and deadlocks are possible
  * Sätt rl i samma ordning som wl, lås sedan upp i samma ordning (good practice)
  * Lös så att den inte är cirkulär genom att både läsa och skriva ex (y) i samma tråd. Men att bara ha läs och skriv av (x) i den andra.
  * Något serializable är inte nödvändigt serial. Men tvärt om!
  * Two-Phase Locking (2PL)
    + Definition: A transaction follows the two-phase locking (2PL) protocol if all of its read_lock() and write_lock() operations come before its first unlock() operation
    +  A transaction that follows the 2PL protocol has an expansion phase and a shrinking phase

### Database Technology
##  Topic 10: Recovery of Database

#### Types of Failures

Database nay become unavailable for use due to:

  * Transaction failures
    + e.g., incorrect input, deadlock, incorrect synchronization
    + Result: tranaction abort
  * System failures
    + e.g., application error, operating system fault
  * Media failures
    + e.g., RAM failure, disk head crash, power disruption

#### Situations after System Failure

  * DBMS is halted abruptly
  * Processing of in-progress SQL commands halted abruptly
  * Connections to application programs (client) are broken
  * States of executing programs unkown
  * Contents of memory buffers are lost
  * Database files are _not_ damaged

#### Purpose of Database Recovery

  * Bring the database into the most recent consistent state that existed prior to a failure
  * Atomicity and Durability of the ACID properties
    + Abort (and restart) TA:s activate at time of failure
    + Ensure changes made by committed TAs are not lost
  * Complication due to database execution model:
    + Data items packed into I/O blocks (pages)
    + At time of write updated data first stored in main memory buffer
    + Actually written to disk some time later

#### Logging

  * Append-only file
    + Keep track of all operations of all transactions
    + In the order in which operations occurred
  * Stored on disk
    + Presistent except for disk catastropic failures
    + Periodically backed up (to guard against disk and catastropic failures)
  * Log buffer
    + Holds log records being appended in main memory
    + Occasionally whole buffer appended to end of log file on disk (flush)

#### Log Records
  * [start_transaction, T]
    + Transaction T has started execution
  * [write_item, T, X, old_value, new_value]
    + Transaction T has changed the value of item X from old_value to new_value
    + old_value (before image) needed to _undo(x)_
    + new_value (after image) needed to _redo(x)_
  * [commit, T]
    + T has completed successfully and commited
    + Effects (writes) of T must be durable
  * [abort, T]
    + T has been aborted
    + Effects (writes) of T must be ignored and undone


#### Commit Point
  * A transaction reaches its commit point when:
    + all of its operations are executed, and
    + all its log records are flushed to disk (where the last is the commit record)
  * Beyond its commit point
    + the transaction is said to be commited, and
    + its effect must be permanently recorded in the DB

### Questions

  * What does a commit instruction mean ?
    + Until you commit a transation, you can see any changes you have made during a transation, but other users cannot see the changes. After you have commited the transaction changes are visible to other users statements that execute after the commmit instruction.

  * What does a checkpoint instruction mean ?
    + A checkpoint creates a known good point from which the DBMS can start applying changes contained in the log during recovery after an unexpected shutdown or crash.


#### Write-Ahead Logging (WAL)
  * Used to ensure that the log
    + is consistent with the DB, and
    + can be used to recover the DB to a consistent state

  * Two rules
    + Log record(s) for a pahe must be written before corresponding page is flushed to disk, and
    + All log records must be written before commit
  * Rule 1 for atomicity
    + each operation is known and can be undone if needed
  * Rule 2 for durability
    + the effect of a committed transaction is known

### Recovery Process

#### Deferred Update (no-undo/redo)
  * gör om alla som finns i "comitted" i samma ordning som de dyker upp i loggen.

#### Immediate Update 1 (undo/no-redo)
  * gör alla som står i active, gör de i bakvänd ordning.
#### Immediate Update 2 (undo/redo)
  * gör först alla som står i active, i bakvänd ordning och sedan alla de som finns i commited i samma ordning som i deferred.

##### Examples

![Tranactions and rollbacks](http://i.imgur.com/7dkEpiCl.jpg)

### Database Technology
##  Topic 11: Query Processing and Optimization

#### Outline

  * Query representations
    * Logical plans
    * Physical plans
  * Query processing steps
  * Examples for physical operators
    * Table scan
    * Sorting
    * Dublicate elimination
    * Nested loop join
    * Sort-merge join
    * Hash join

#### Query Representaions

  * While it is processed by a DBMS, a query goes through multiple representations

  * Usually, these are:
    * An expression in the query language (e.g., SQL) 2. Parse tree
    * Logical plan
    * Physical plan
    * Compiled program


#### Query Processing Steps

##### Parsing
  * Input: SQL query
  * Output: internal representation (e.g., based on relational algebra)

##### Query Validation
  * Checking whether:
    * mentioned tables, attributes etc., exists
    * comparisons are feasible (e.g., compabilty of attribute types)
    * aggregation queries have a valid SELECT clause
    * etc.

##### View Resolution
  * Substitute each reference to a view by the corresponding view definition

##### Optimization
  * Consider possible query execution plans (QEPs)
    * Different QEPs have different costs (i.e., resources needed for their execution)
  * Output: an efficient QEP
    * i.e., estimated cost is the lowest or comparatively low
  * This task is all but trivial ...

##### Optimization

  * ... this task is all but trivial!
  * Set of all possible QEPs is huge Optimizers enumerate only a restricted subset (search space)

  * A desirable optimizer:
    * Cost estimation is accurate
    * Search space has low-cost QEPs
    * Enumeration algorithm is efficient

##### Plan Compiation
  * Translate the selected QEP into a representation ready for execution
    *  e.g., compiledmachinecode, interpreted language

##### Execution
  * Execute the compiled plan
  * Return the query result via the respective interface


#### Examples for Physical Operators

##### Table Scan

  * Leaves of physical operator trees are (physical) tables
  * Accessing them completely implies a sequential scan
    * Load each page of the table
    * Sequentially scanning a table that occupies n pages has n I/O cost

![Table scan]()


#### Summery

  * For each query, different physical operators can be combined into different, semantically equivalent QEPs
  * Every physical operator comes with an algorithm
  * Commonly used techniques for many of these algorithms:
    * Combining: multiple tasks may be combined once some input data has been read in
    * Partitioning: by sorting or by hashing, we can partition the input(s) and ignore many irrelevant combinations (less work)
    * Indexing: existing indexes may be exploited to reduce work to relevant parts of the input
  * Each of these algorithms has a specific cost
  * Thus, different QEPs have different costs
  * Actual cost can only be estimated (w/o executing the QEP)

![](http://i.imgur.com/U0NCNi0l.jpg)

![](http://i.imgur.com/WH6oa9gl.jpg)

![](http://i.imgur.com/MuwITfql.jpg)
