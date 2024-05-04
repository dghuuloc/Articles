# <p align="center">Mastering Backend Development with Java Spring Boot: Best Practices and Pro Tips</p>
---

Spring Boot is a widely used and very popular enterprise-level high-performance framework. Here are some best practices and a few tips you can use to improve your Spring Boot application and make it more efficient. This article will be a little longer, and it will take some time to completely read the article.

## Proper packaging style
- Proper packaging will help to understand the code and the flow of the application easily.
- You can structure your application with meaningful packaging.
- You can include all your controllers into a separate package, services in a separate package, util classes into a separate package…etc. This style is very convenient in small-size microservices.
- If you are working on a huge code base, a feature-based approach can be used. You can decide on your requirement.

__Based on type__
<p align="center"><img src="https://github.com/dghuuloc/Articles/blob/main/images/based-on-type.png"/></p>

__Based on feature__
<p align="center"><img src="https://github.com/dghuuloc/Articles/blob/main/images/based-on-feature.png"/></p>

## Use design patterns
- No complaints. Design patterns are already best practices.
- But you must identify the place where you can use them.
- Please check this article to understand “how to use the Builder design pattern” in our Spring Boot applications.

## Use Spring Boot starters
- This is a cool feature of Spring Boot.
- We can very easily use starter dependencies without adding single dependencies one by one. These starter dependencies are already bundled with the required dependencies.
- For example, if we add __spring-boot-starter-web__ dependency, by default it is bundled with __jackson__, __spring-core__, __spring-mvc__, and __spring-boot-starter-tomcat__ dependencies.
- So we don’t need to care about adding dependencies separately.
- And also it helps us to avoid version mismatches.

## Use proper versions of the dependencies
- It is always recommended to use the latest stable GA versions.
- Sometimes it may vary with the Java version, server versions, the type of the application…etc.
- Do not use different versions of the same package and always use <properties> to specify the version if there are multiple dependencies.

<p align="center"><img src="https://github.com/dghuuloc/Articles/blob/main/images/version-dependencies.png"/></p>

## Use Lombok
- As a Java developer, you have probably heard of the __Lombok project__.
- Lombok is a Java library that can be used to reduce your codes and allow you to write clean code using its annotations.
- For example, you may use plenty of lines for getters and setters in some classes like entities, request/response objects, dtos…etc.
- But if you use Lombok, it is just one line, you can use __@Data__, __@Getter__ or __@Setter__ as per your requirement.
- You can use Lombok logger annotations as well. @Slf4j is recommended.
- Check this file for your reference.

## Use constructor injection with Lombok
<p align="center"><img src="https://github.com/dghuuloc/Articles/blob/main/images/lombok-constructor.png"/></p>

- When we talk about dependency injection, there are two types.
- One is __“constructor injection”__ and the other is __“setter injection”__. Apart from that, you can also use __“field injection”__ using the very popular __@Autowired__ annotation.
- But we highly recommend using __Constructor injection__ over other types. Because it allows the application to initialize all required dependencies at the initialization time.
- This is very useful for unit testing.
- The important thing is, that we can use the __@RequiredArgsConstructor__ annotation by Lombok to use constructor injection.

## Use slf4j logging
<p align="center"><img src="https://github.com/dghuuloc/Articles/blob/main/images/logger.png"/></p>

- Logging is very important.
- If a problem occurs while your application is in production, logging is the only way to find out the root cause.
- Therefore, you should think carefully before adding loggers, log message types, logger levels, and logger messages.
- Do not use System.out.print()
- Slf4j is recommended to use along with logback which is the default logging framework in Spring Boot.
- Always use slf4j { } and avoid using String interpolation in logger messages. Because string interpolation consumes more memory.
- Please check this file for your reference to get an idea about, implementing a logger.
- You can use Lombok @Slf4j annotation to create a logger very easily.
- If you are in a micro-services environment, you can use the ELK stack.

## Use Controllers only for routing
<p align="center"><img src="https://github.com/dghuuloc/Articles/blob/main/images/use-controller.png"/></p>

- Controllers are dedicated to routing.
- It is __stateless__ and __singleton__.
- The DispatcherServlet will check the _@RequestMapping_ on Controllers
- Controllers are the ultimate target of requests, then requests will be handed over to the service layer and processed by the service layer.
- The business logic __should not be__ in the controllers.

## Use Services for business logic
- The __complete business logic goes here__ with validations, caching…etc.
- Services communicate with the persistence layer and receive the results.
- Services are also singleton.

## Avoid NullPointerException
<p align="center"><img src="https://github.com/dghuuloc/Articles/blob/main/images/null.png"/></p>

- To avoid __NullPointerException__ you can use __Optional__ from java.util package.
- You can also use null-safe libraries. Ex: __Apache Commons StringUtils__
- Call __equals()__ and __equalsIgnoreCase()__ methods on known objects.
- Use __valueOf()__ over __toString()__
- Use IDE-based __@NotNull__ and __@Nullable__ annotations.

## Use best practices for the Collection framework
- Use appropriate collection for your data set.
- Use __forEach__ with Java 8 features and avoid using legacy for loops.
- Use __interface type__ instead of the implementation.
- Use __isEmpty()__ over __size()__ for better readability.
- Do not return null values, you can return an empty collection.
- If you are using objects as data to be stored in a hash-based collection, you should override equals() and hashCode() methods. Please check this article “How does a HashMap internally work”.

## Use pagination
<p align="center"><img src="https://github.com/dghuuloc/Articles/blob/main/images/pagination.png"/></p>

- This will improve the performance of the application.
- If you’re using __Spring Data JPA__, the __PagingAndSortingRepository__ makes using pagination very easy and with little effor

## Use caching
- Caching is another important factor when talking about application performance.
- By default Spring Boot provides caching with __ConcurrentHashMap__ and you can achieve this by __@EnableCaching__ annotation.
- If you are not satisfied with default caching, you can use __Redis__, __Hazelcast__, or any other distributed caching implementations.
- Redis and Hazelcast are __in-memory__ caching methods. You also can use database cache implementations as well.

## Use custom exception handler with global exception handling
<p align="center"><img src="https://github.com/dghuuloc/Articles/blob/main/images/exception-handling.png"/></p>
                                                                                                     
- This is very important when working with large enterprise-level applications.
- Apart from the general exceptions, we may have some scenarios to identify some specific error cases.
- Exception adviser can be created with __@ControllerAdvice__ and we can create separate exceptions with meaningful details.
- It will make it much easier to identify and debug errors in the future.
- Please check this and this for your reference.

## Use custom response object
<p align="center"><img src="https://github.com/dghuuloc/Articles/blob/main/images/custom-reponse-object.png"/></p>
                                                                                                             
- A custom response object can be used to return an object with some specific data with the requirements like HTTP status code, API code, message…etc.
- We can use the __builder design pattern__ to create a custom response object with custom attributes.
- Please check this article for your reference.

## Remove unnecessary codes, variables, methods, and classes.
<p align="center"><img src="https://github.com/dghuuloc/Articles/blob/main/images/remove-unnecessary.png"/></p>

commented code in the production
- __Unused variable__ declarations will acquire some memory.
- Remove unused methods, classes…etc because it will impact the performance of the application.
- Try to avoid nested loops. You can use maps instead.

## Using comments
- Commenting is a good practice unless you abuse it.
- DO NOT comment on everything. Instead, you can write descriptive code using meaningful words for classes, functions, methods, variables…etc.
- Remove commented codes, misleading comments, and story-type comments.
- You can use comments for warnings and explain something difficult to understand at first sight.

## Use meaningful words for classes, methods, functions, variables, and other attributes.
<p align="center"><img src="https://github.com/dghuuloc/Articles/blob/main/images/meaningful-word.png"/></p>

- This looks very simple, but the impact is huge.
- Always use proper __meaningful and searchable__ naming conventions with proper case.
- Usually, we use __nouns or short phrases__ when declaring __classes__, __variables__, and __constants__. Ex: String firstName, const isValid
- You can use __verbs and short phrases with adjectives__ for __functions__ and __methods__. Ex: readFile(), sendData()
- Avoid using __abbreviating variable__ names and __intention revealing__ names. Ex: int i; String getExUsr;
- If you use this meaningfully, declaration comment lines can be reduced. Since it has meaningful names, a fresh developer can easily understand by reading the code.

## Use proper case for declarations
<p align="center"><img src="https://github.com/dghuuloc/Articles/blob/main/images/declaration.png"/></p>

- There are many different cases like __UPPERCASE, lowercase, camelCase, PascalCase, snake_case, SCREAMING_SNAKE_CASE, kebab-case__…etc.
- But we need to identify which case is dedicated to which variable.
- Usually, I follow,
    - classes — __PascalCase__
    - methods & variables — __camelCase__
    - constants — __SCREAMING_SNAKE_CASE__
    - DB-related fields — __snake_case__
- This is just an example. It can be different from the standard you follow in the company.

## Be simple
<p align="center"><img src="https://github.com/dghuuloc/Articles/blob/main/images/simple.png"/></p>
                                                                                                      
- Always try to write simple, readable codes.
- The same simple logic can be implemented using different ways, but it is difficult to understand if it is not readable or understandable.
- Sometimes complex logic consumes more memory.
- Try to use __KISS__, __DRY__, and __SOLID__ principles when writing codes. I will explain this in a future article.

## Use a common code formatting style
<p align="center"><img src="https://github.com/dghuuloc/Articles/blob/main/images/formatting-style.png"/></p>

- Formatting styles vary from developer to developer. Coding style changes are also considered a change and can make code merging very difficult.
- To avoid this, the team can have a common coding format.

## Use SonarLint
<p align="center"><img src="https://github.com/dghuuloc/Articles/blob/main/images/sonar-lint.png"/></p>

- This is very useful for identifying small bugs and best practices to avoid unnecessary bugs and code quality issues.
- You can install the plugin into your favorite IDE.
