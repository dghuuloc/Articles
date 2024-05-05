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
Hibernate is an ORM tool which is used in your __DAO (data access layer) layer__. It makes use of Hibernate API to effectively `load`, `store`, `update`, `delete` and `query`, etc its domain objects. As you can see in the diagram, ORM seats between your database and DA Layer.

Hibernate inherits the core of JPA : `EntityManagerFactory`, `EntityManager`, `EntityTransaction` and implements them. Hibernate, internally, uses JDBC to interact with relational database after connecting to the database.

> [!NOTE]
> Remember, Hibernate is a JPA compliant ORM tool.

The main feature of Hibernate is to map the Java classes to database tables. Following are some key features of Hibernate:
- Hibernate is an implementation of JPA guidelines.
- It helps in mapping Java data types to SQL data types.
- It is the contributor of JPA.

Now you must be wondering out why there is need for JPA, right. So as illustrated, JPA is a specification. It gives common functionality and prototype to ORM tools. All ORM tools (such as Hibernate) follow the common standards, by executing the same specification.

## What is JPA?
JPA stands for __Java Persistent API_, JPA provides mechanism for Java ORM(Object-RelationalMapping) technology. In easy terms,it is a specification from Java that dictates the APIs to be used to persist Entities (Java Objects) in the database. This specification is implemented by Hibernate or other ORM tools.

Let us do discuss some key features of JPA which are as follows:
- JPA is only a specification, it is not an implementation.
- It is a set of rules and guidelines to set interfaces for implementing object-relational mapping.
- It needs a few classes and interfaces.
- It supports simple, cleaner, and assimilated object-relational mapping.
- It supports polymorphism and inheritance.
- Dynamic and named queries can be included in JPA.

> [!NOTE]
> JPA/ORM tools are only for RDBMS, not for schemaless databases.

## What Is Spring Data JPA?
Spring Data is a part of the __Spring Framework__. Spring Data JPA provides Repository Interface that wraps JPA into another abstraction. This Spring Data JPA uses JPA implementations such as Hibernate to utilize JPA. With this, developers can easily access data.

<p align="center"><img src="https://github.com/dghuuloc/Articles/blob/main/images/spring-data-jpa.png"/></p>

The goal of Spring Data JPA repository module is to significantly reduce the amount of boilerplate code required to implement data access layers for various persistence stores.

Spring Data JPA is not a JPA provider. It is a library/framework that adds an extra layer of abstraction on the top of our JPA provider (like Hibernate).

## What Is the Difference Between Hibernate and Spring Data JPA?
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

