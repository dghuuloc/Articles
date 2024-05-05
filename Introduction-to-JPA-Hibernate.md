# <p align="center">Introduction to JPA and Hibernate</p>
---

## What is JDBC (Java Database Connectivity)?
JDBC is the standard Java API for connecting to relational databases. Unlike JPA and Hibernate, JDBC is lower level and requires developers to write SQL queries and handle result sets manually. While it offers more control, it also demands more code. JDBC is often used when fine-grained control over database interactions is required, or when working with databases not covered by higher-level frameworks.

## What is Persistence?
Today’s application requires persistent data, meaning the data needs to be reliably stored in a database. Then the application should be able to retrieve the data from the database and convert it into java objects whenever needed. As you know, there are several databases today like SQL databases, NoSQL databases, time-series databases and so on. This tutorial will only be talking about the SQL databases (relational database) like `MySQL`, `Oracle Database`, `MS-SQL`, `H2`, etc.

> [!NOTE]
> Object persistence means, individual objects living in the application memory (RAM), can be saved in a data store and be recreated later as and when needed.

## What is ORM?
An ORM (Object-relational mapping) is the programming technique to map __application domain model objects to the relational database tables__. Technically, ORM is a wrapper on top of the JDBC layer that automates a lot of boilerplate code. There are several ORM tools available in Java such as `Jboss Hibernate`, `Oracle TopLink`, `EclipseLink`, `OpenJPA`, etc.

<p align="center"><img src="https://github.com/dghuuloc/Articles/blob/main/images/orm.png"/></p>

ORM tools are used for Relational databases like MySql, Oracle database, db2 and etc. For NoSQL databases, we make use of OGM tools which is out of scope for this tutorial.

## What is Hibernate?
Hibernate is a Java based ORM tool which is used in your __DAO (data access layer) layer__. It provides a framework for mapping application domain objects to relational database tables in the Spring Boot application. 

Hibernate provides JPA implementation thats maps your database records to Java objects and generates the required SQL statements to replicate all operations to the database. (Hibernate is an implementation of JPA guidelines.).

Hibernate uses JDBC for all database communications. Hibernate uses JDBC to interact with the database. 

Hibernate acts as an additionall layer on top of JDBC and enables you to implement a database-independent persistence layer.

### How Hibernate works behind the scenes?
Whenever we persist or store an object using Hibernate, then Hibernate will generate SQL queries and execute those SQL queries with respect to the database  using JDBC, we just have to play with the objects.

### Hibernate Architecture
<p align="center"><img src="https://github.com/dghuuloc/Articles/blob/main/images/hibernate-architecture.png"/></p>

Hibernate has a layered architecture which helps the user perform operations without touching anything under the hood. Hibernate provides ORM for persistence service.

__Configuration Object__:
Usually, the Configuration Object is created once during the application lifecycle; additionally, it is the first hibernate object that is created. It represents the database and other configurations.

__SessionFactory Object__:
SessionFactory object is created using Configuration Object. The SessionFactory object is a heavyweight object. It is usually created when the application is initialized. Additionally, The SessionFactory is a thread-safe object and is used by other threads.

__Session Object__:
The session object is used to provide the database connection. It was designed as a lightweight object that is to be created each time when database interaction is required. In addition, SessionObject is not recommended to be retained for later use because it is not thread-safe.

__Transaction Object__:
The Transaction object is used whenever we want to perform operations on an entity, committing or rolling back changes according to the result.

__Query Object__:
The query object uses SQL or HQL (Hibernate Query Language) to retrieve data from the database. The query instance is obtained by calling the createQuery method that belongs to the Session object.

__Criteria Object__:
It usually uses dynamic queries that are obtained from Session objects.

## What is JPA?
JPA stands for __Java Persistent API_, JPA facilitates object-relational mapping to manage relational data in Java applications. It provides a platform to work directly with objects instead of using SQL statements. In easy terms, JPA is a specification and it's implemented by Hibernate or other ORM tools.

Let us do discuss some key features of JPA which are as follows:
- JPA is only a specification, it is not an implementation.
- JPA is a set of rules and guidelines to set interfaces for implementing object-relational mapping.
- JPA needs a few classes and interfaces.
- JPA supports simple, cleaner, and assimilated object-relational mapping.
- JPA supports polymorphism and inheritance.
- JPA provides a query language that can retrieve objects without writing massive SQL queries

> [!NOTE]
> JPA/ORM tools are only for RDBMS, not for schemaless databases.

### JPA Repository Pattern
The JPA repository pattern contains database operations that make it easier for us. At the same time, the JPA repository can work with Hibernate, Eclipse Link, etc. It is just an abstraction.

<p align="center"><img src="https://github.com/dghuuloc/Articles/blob/main/images/jpa-repository-pattern.png"/></p>

Now you must be wondering out why there is need for JPA, right. So as illustrated, JPA is a specification. It gives common functionality and prototype to ORM tools. All ORM tools (such as Hibernate) follow the common standards, by executing the same specification.

## What Is Spring Data JPA?
Spring Data is a part of the __Spring Framework__. Spring Data JPA provides Repository Interface that wraps JPA into another abstraction. This Spring Data JPA uses JPA implementations such as Hibernate to utilize JPA.

<p align="center"><img src="https://github.com/dghuuloc/Articles/blob/main/images/spring-data-jpa.png"/></p>

The goal of Spring Data JPA repository is to significantly reduce the amount of boilerplate code required to implement data access (DAO) layers for various persistence stores.

Spring Data JPA is not a JPA provider. It is a library/framework that adds an extra layer of abstraction on the top of our JPA provider (like Hibernate).

## What Is the Difference Between Hibernate and Spring Data JPA?
<p align="center"><img src="https://github.com/dghuuloc/Articles/blob/main/images/hibernate-vs-spring-data-jpa.png"/></p>

- Hibernate is a Java based ORM tool that provides a framework for mapping application domain objects to the relational database tables and vice versa.
- Spring Data JPA is an abstraction layer on top of JPA to Reduce the amount of boilerplate code required to implement data access object (DAO) layer.
- Hibernate is a JPA provider (JPA specification implementation). Spring Data JPA is not a JPA provider. It simply __hides__ the Java Persistence API (and the JPA provider) behind its repository abstraction.

> [!NOTE]
> Spring Data JPA always requires the JPA provider such as Hibernate or Eclipse Link.
> Spring Data JPA uses Hibernate as a default JPA provider.
> Spring Data JPA cannot work without a JPA provider.

## What is the Difference Between JPA and Hibernate?
JPA is just a specification (no implementation) that facilitates object-relational mapping to manage ralational data in Java applications. It provides a platform to work directly with objects instead of using SQL statements.

Hibernate is a Java based ORM tool that provides a framework for mapping application domain objects to the relational database tables and vice versa.

In short, JPA provides standard specification (interface). Hibernate provides a implementation for JPA specification.

## Why do use Spring Data JPA?
In typical three-layer Spring application architecture, we create three layers (__Controller__, __Service__, and __DAO/REpository layer__).

If we use JPA/Hiberante then write a lot of coding while implementing DAO/Repository layer.

<p align="center"><img src="https://github.com/dghuuloc/Articles/blob/main/images/application-architecture.png"/></p>

Spring Data JPA provides a solution to reduce a lot of boilerplate code. We can use Spring Data JPA to reduce the amount of boilerplate code required to implement the data access object (DAO) layer.

<p align="center"><img src="https://github.com/dghuuloc/Articles/blob/main/images/application-using-spring-data-jpa.png"/></p>

## Conclusion
- __JPA__ is API interface for ORM technology in Java Applications.
- __Hibernate__ is the implementations of JPA and uses JDBC internally to connect with database.
- __Spring Data JPA__ is a composite of modules provided by Spring that uses JPA internally.

## References
- [How to Use Jpa Repository in Spring Boot](https://springjava.com/spring-data-jpa/how-to-use-jpa-repository-in-spring-boot/)
- [What is Hibernate And JPA?](https://medium.com/@dafikabukcu/what-is-hibernate-and-jpa-ef77ba1dac15)
- [Difference Between Hibernate and Spring Data JPA](https://www.youtube.com/watch?app=desktop&v=4Py9RTVWyvE)
