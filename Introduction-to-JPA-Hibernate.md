## <p align="center">Introduction to JPA and Hibernate</p>
---

## What is Persistence?
Today’s application requires persistent data, meaning the data needs to be reliably stored in a database. Then the application should be able to retrieve the data from the database and convert it into java objects whenever needed. As you know, there are several databases today like SQL databases, NoSQL databases, time-series databases and so on. This tutorial will only be talking about the SQL databases (relational database) like `MySQL`, `Oracle Database`, `MS-SQL`, `H2`, etc.

> [!NOTE]
> Object persistence means, individual objects living in the application memory (RAM), can be saved in a data store and be recreated later as and when needed.

## What is ORM?
An ORM (Object-relational mapping) is the programming technique to map __application domain model objects__ to __the relational database tables__. Technically, ORM is a wrapper on top of the JDBC layer that automates a lot of boilerplate code. There are several ORM tools available in Java such as `Jboss Hibernate`, `Oracle TopLink`, `EclipseLink`, `OpenJPA`, etc.

<p align="center"><img src="https://github.com/dghuuloc/Articles/blob/main/images/orm.png"/></p>

ORM tools are used for Relational databases like MySql, Oracle database, db2 and etc. For NoSQL databases, we make use of OGM tools which is out of scope for this tutorial.

## What is Hibernate?
Hibernate is an ORM tool which is used in your __DAO (data access layer) layer__. It provides a framework to map OOP domain models to relational database tables in the Spring Boot application. As you can see in the diagram, ORM seats between your database and DA Layer.

Hibernate inherits the core of JPA : `EntityManagerFactory`, `EntityManager`, `EntityTransaction` and implements them. Hibernate, internally, uses JDBC to interact with relational database after connecting to the database.

The main feature of Hibernate is to map the Java classes to database tables. Following are some key features of Hibernate:
- Hibernate is an implementation of JPA guidelines.
- It helps in mapping Java data types to SQL data types.
- It is the contributor of JPA.

Now you must be wondering out why there is need for JPA, right. So as illustrated, JPA is a specification. It gives common functionality and prototype to ORM tools. All ORM tools (such as Hibernate) follow the common standards, by executing the same specification.

> [!NOTE]
> Remember, Hibernate is a JPA compliant ORM tool.

### Hibernate Architecture
<p align="center"><img src="https://github.com/dghuuloc/Articles/blob/main/images/hibernate-architecture.png"/></p>

Hibernate has a layered architecture which helps the user perform operations without touching anything under the hood. Hibernate provides ORM for persistence service.

__Configuration Object__
Usually, the Configuration Object is created once during the application lifecycle; additionally, it is the first hibernate object that is created. It represents the database and other configurations.

__SessionFactory Object__
SessionFactory object is created using Configuration Object. The SessionFactory object is a heavyweight object. It is usually created when the application is initialized. Additionally, The SessionFactory is a thread-safe object and is used by other threads.

__Session Object__
The session object is used to provide the database connection. It was designed as a lightweight object that is to be created each time when database interaction is required. In addition, SessionObject is not recommended to be retained for later use because it is not thread-safe.

__Transaction Object__
The Transaction object is used whenever we want to perform operations on an entity, committing or rolling back changes according to the result.

__Query Object__
The query object uses SQL or HQL (Hibernate Query Language) to retrieve data from the database. The query instance is obtained by calling the createQuery method that belongs to the Session object.

__Criteria Object__
It usually uses dynamic queries that are obtained from Session objects.

## What is JPA?
JPA stands for __Java Persistent API_, JPA provides mechanism for Java ORM(Object-RelationalMapping) technology. JPA is a standard that persists and retrieves information from a non-volatile storage system, mapping Java objects to tables in a database. In easy terms, JPA is a specification and it's implemented by Hibernate or other ORM tools.

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

JPA uses a similar repository pattern under the hood.

<p align="center"><img src="https://github.com/dghuuloc/Articles/blob/main/images/jpa-repository-pattern.png"/></p>

As you can see, we have entities, and each entity has its own repositories that have been extended from the JpaRepository interface in the background. The JPA repository works with EntityManager, and It works with Hibernate, which works with JDBC.

## What Is Spring Data JPA?
Spring Data is a part of the __Spring Framework__. Spring Data JPA provides Repository Interface that wraps JPA into another abstraction. This Spring Data JPA uses JPA implementations such as Hibernate to utilize JPA. It is very useful to store and retrieve data from the database through Java code without the need to write the query.

<p align="center"><img src="https://github.com/dghuuloc/Articles/blob/main/images/spring-data-jpa.png"/></p>

The goal of Spring Data JPA repository module is to significantly reduce the amount of boilerplate code required to implement data access layers for various persistence stores.

Spring Data JPA is not a JPA provider. It is a library/framework that adds an extra layer of abstraction on the top of our JPA provider (like Hibernate).

## What Is the Difference Between Hibernate and Spring Data JPA?
<p align="center"><img src="https://github.com/dghuuloc/Articles/blob/main/images/hibernate-vs-spring-data-jpa.png"/></p>

- Hibernate is a __JPA implementation__, while Spring Data JPA is a __JPA Data Access Abstraction__.
- Spring Data offers a solution to `GenericDao` custom implementations. It can also generate JPA queries on your behalf through method name conventions. With Spring Data, you may use Hibernate, Eclipse Link, or any other JPA provider.
- Spring Data JPA is not an implementation or JPA provider, it's just an abstraction used to significantly reduce the amount of boilerplate code required to implement data access layers for various persistence stores.
- Hibernate provides a reference implementation of the Java Persistence API that makes it a great choice as an ORM tool with the benefits of loose coupling.

> [!NOTE]
> Remember, Spring Data JPA always requires the JPA provider such as Hibernate or Eclipse Link.

## What is the Difference Between JPa and Hibernate?
As we know that JPA is just a specification, meaning there is no implementation. You can annotate your classes as much as you would like with JPA annotations, however, without an implementation, nothing will happen. Think of JPA as the guidelines that must be followed or an interface, while Hibernate's JPA implementation is code that meets the API as defined by the JPA specification and provides the under the hood functionality. 

## Why do use Spring Data JPA?
In typical three-layer Spring application architecture, we create three layers (__Controller__, __Service__, and __DAO/REpository layer__).

If we use JPA/Hiberante then write a lot of coding while implementing DAO/Repository layer.

<p align="center"><img src="https://github.com/dghuuloc/Articles/blob/main/images/application-architecture.png"/></p>

Spring Data JPA provides a solation to reduce a lot of boilerplate code. We can use Spring Data JPA to reduce the amount of boilerplate code required to implement the data access object (DAO) layer.

## Conclusion
- __JPA__ is API interface for ORM technology in Java Applications.
- __Hibernate__ is the implementations of JPA and uses JDBC internally to connect with database.
- __Spring Data JPA__ is a composite of modules provided by Spring that uses JPA internally.

## References
- [How to Use Jpa Repository in Spring Boot](https://springjava.com/spring-data-jpa/how-to-use-jpa-repository-in-spring-boot/)
