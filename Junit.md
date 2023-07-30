# <p align="center">How To Write Automation Tests With Java</p>
---

## Test life cycle
Below is life cycle sequence in which annotation methods are called. Junit does not require to us to override any method but to just mark methods with annotations
- __@BeforeAll__ : Before any test starts to execute. Executes only once. Its optional to define.
- __@BeforeEach__ : Before every test method marked with @Test annotation.Its optional to define.
- __@Test__ : Run tests in the sequence of declaration the test method. Its required to mark methods a test case.
- __@AfterEach__ : After every test method marked with @Test annotation.Its optional to define.
- __@AfterAll__ : At last when all tests in class complete. Executes only once.Its optional to define. Number unit-tests is equal to number of methods marked with this annotation.

- JUnit Platform: a foundation for launching testing frameworks on JVM. It provides support for most of the popular IDEs (IntelliJ IDEA, Eclipse, NetBeans, and Visual Studio Code) and build tools (Gradle, Maven, and Ant).
- JUnit Jupiter: a new programming model for test automation in `JUnit5`
- JUnit Vintage: a backward-compatible test engine which supports running `JUnit3` and `JUnit4` tests

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

