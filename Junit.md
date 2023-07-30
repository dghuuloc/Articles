# <p align="center">How To Write Automation Tests With Java</p>
---

## What Is JUnit 5?
JUnit 5 is more than just another unit testing framework. It has several sub-projects, namely the JUnit Platform, the JUnit Jupiter, and the JUnit Vintage. Each of these three components has unique modules which work together to improve testing for Java programmers.

The JUnit 5 platform is available in the latest versions of the top Java Integrated development platforms (IDE). The Java IDEs that support JUnit 5 are:
- IntelliJ IDEA
- Eclipse
- NetBeans
- Visual Studio Code

## Test life cycle
Below is life cycle sequence in which annotation methods are called. Junit does not require to us to override any method but to just mark methods with annotations
- __@BeforeAll__ : Before any test starts to execute. Executes only once. Its optional to define.
- __@BeforeEach__ : Before every test method marked with @Test annotation.Its optional to define.
- __@Test__ : Run tests in the sequence of declaration the test method. Its required to mark methods a test case.
- __@AfterEach__ : After every test method marked with @Test annotation.Its optional to define.
- __@AfterAll__ : At last when all tests in class complete. Executes only once.Its optional to define. Number unit-tests is equal to number of methods marked with this annotation.

##  Basic components of the JUnit 5 project
JUnit5 comprises several different modules from three different sub-projects:
- JUnit Platform: a foundation for launching testing frameworks on JVM. It provides support for most of the popular IDEs (IntelliJ IDEA, Eclipse, NetBeans, and Visual Studio Code) and build tools (Gradle, Maven, and Ant).
- JUnit Jupiter: a new programming model for test automation in `JUnit5`
- JUnit Vintage: a backward-compatible test engine which supports running `JUnit3` and `JUnit4` tests

## JUnit5 Setup
To start using JUnit5 in your Java project, you have to start by adding the _junit-jupiter-engine_ dependency to your project's classpath.
If you're using __Maven__, you can simply add the following to your `pom.xml`:

```xml
<dependency>
    <groupId>org.junit.jupiter</groupId>
    <artifactId>junit-jupiter-engine</artifactId>
    <version>5.0.0-M4</version>
</dependency>
```

## Writing Test Script
Make sure that your local machine runs on JDK8 or newer. Create a new Java file called `SimpleTest.java`

### Import
First and foremost, you need to import a few JUnit Jupiter core modules to your Java file. The simplest test case requires at least the following modules:

```java
import static org.junit.jupiter.api.Assertions.assertEquals;
import org.junit.jupiter.api.Test;
```
### Annotation

```java
@Test
void singleAssertion() {
	assertEquals(2, 1 + 1);
}
```

