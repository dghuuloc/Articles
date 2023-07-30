# <p align="center">How To Write Automation Tests With Java</p>
---

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

