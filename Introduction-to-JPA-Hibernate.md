## <p align="center">Introduction to JPA and Hibernate</p>
---

## What is Persistence?
Today’s application requires persistent data, meaning the data needs to be reliably stored in a database. Then the application should be able to retrieve the data from the database and convert it into java objects whenever needed. As you know, there are several databases today like SQL databases, NoSQL databases, time-series databases and so on. This tutorial will only be talking about the SQL databases (relational database) like `MySQL`, `Oracle Database`, `MS-SQL`, `H2`, etc.

> [!NOTE]
> Object persistence means, individual objects living in the application memory (RAM), can be saved in a data store and be recreated later as and when needed.

## What is ORM?
An ORM (Object-relational mapping) is the programming technique to map application domain model objects to the relational database tables. Technically, ORM is a wrapper on top of the JDBC layer that automates a lot of boilerplate code. There are several ORM tools available in Java such as `Jboss Hibernate`, `Oracle TopLink`, `EclipseLink`, `OpenJPA`, etc.

ORM tools are used for Relational databases like MySql, Oracle database, db2 and etc. For NoSQL databases, we make use of OGM tools which is out of scope for this tutorial.

## What is Hibernate?
Hibernate is an ORM tool which is used in your __DAO (data access layer) layer__. It makes use of Hibernate API to effectively `load`, `store`, `update`, `delete` and `query`, etc its domain objects.

As you can see in the diagram, ORM seats between your database and DA Layer.

> [!NOTE]
> Remember, Hibernate is a JPA compliant ORM tool.

## What is JPA?
JPA stands for Java Persistent API. It is an official specification from Java that dictates the APIs to be used to persist Entities (Java Objects) in the database. This specification is implemented by Hibernate and other ORM tools.

As mentioned earlier, there are several ORM tools that implement their own API. This becomes a portability problem if you want to switch between them for any reason. This is where JPA helps you by providing an API layer on top of ORM tools. Just like JDBC API vs various database core drivers.

> [!NOTE]
> JPA/ORM tools are only for RDBMS, not for schemaless databases.

## What Is Spring Data JPA?
Spring Data is a part of the __Spring Framework__. The goal of Spring Data JPA  repository module is to significantly reduce the amount of boilerplate code required to implement data access layers for various persistence stores.

Spring Data JPA is not a JPA provider. It is a library/framework that adds an extra layer of abstraction on the top of our JPA provider (like Hibernate).

## What Is the Difference Between Hibernate and Spring Data JPA?
- Hibernate is a __JPA implementation__, while Spring Data JPA is a __JPA Data Access Abstraction__.
- Spring Data offers a solution to `GenericDao` custom implementations. It can also generate JPA queries on your behalf through method name conventions. With Spring Data, you may use Hibernate, Eclipse Link, or any other JPA provider.
- Spring Data JPA is not an implementation or JPA provider, it's just an abstraction used to significantly reduce the amount of boilerplate code required to implement data access layers for various persistence stores.
- Hibernate provides a reference implementation of the Java Persistence API that makes it a great choice as an ORM tool with the benefits of loose coupling.

> [!NOTE]
> Remember, Spring Data JPA always requires the JPA provider such as Hibernate or Eclipse Link.

## Why do use Spring Data JPA?
In typical three-layer Spring application architecture, we create three layers (__Controller__, __Service__, and __DAO/REpository layer__).

If we use JPA/Hiberante then write a lot of coding while implementing DAO/Repository layer.

<p align="center"><img src="https://github.com/dghuuloc/Articles/blob/main/images/application-architecture.png"/></p>

Spring Data JPA provides a solation to reduce a lot of boilerplate code. We can use Spring Data JPA to reduce the amount of boilerplate code required to implement the data access object (DAO) layer.


  


