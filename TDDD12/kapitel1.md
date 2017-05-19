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

### SQL

### SQL DDL

### SQL Queries

``` sql
CREATE TABLE <tablename> (<colname><datatype>[<constraint>]);
/* example */

```

``` sql

```

``` sql

```

``` sql

```

``` sql

```

### Definitions

  * *atomic* - each value indivisible
  * *tupele*
  * *schema*
  * *attribute*
  * *domain* - set of atomic values
  * *instance*
  * *tuple* -
