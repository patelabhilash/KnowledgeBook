### Q. when use to @Configuration and @Component?

@Configuration Indicates that a class declares one or more @Bean methods and may be processed by the Spring container to generate bean definitions and service requests for those beans at runtime

@Component Indicates that an annotated class is a "component". Such classes are considered as candidates for auto-detection when using annotation-based configuration and classpath scanning.

@Configuration is meta-annotated with @Component, therefore @Configuration classes are candidates for component scanning
