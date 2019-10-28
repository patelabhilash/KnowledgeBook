## 1
Following is the high-level flow of how spring boot works.

From the run method, the main application context is kicked off which in turn searches for the classes annotated with @Configuration, initializes all the declared beans in those configuration classes, and based upon the scope of those beans, stores those beans in JVM, specifically in a space inside JVM which is known as IOC container. After the creation of all the beans, automatically configures the dispatcher servlet and registers the default handler mappings, messageConverts, and all other basic things.

[SO how spring boot works internally](https://stackoverflow.com/questions/44172261/how-spring-boot-application-works-internally)

## 2

MANAGE AND RELOAD SPRING APPLICATION PROPERTIES ON THE FLY

using <artifactId>spring-boot-starter-actuator</artifactId>
@RefreshScope annotation(in class level) along with @Value

## 3

[Spring Boot Initialization 12 Steps
](https://stackoverflow.com/questions/39209924/spring-boot-which-piece-of-code-actually-register-dispatcher-servlet-for-sprin)
