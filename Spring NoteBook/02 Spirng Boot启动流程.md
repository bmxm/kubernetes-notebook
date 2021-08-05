

### @SpringBootApplication的原理

@SpringBootApplication开启了Spring的组件扫描和Spring Boot自动配置功能。实际上它是一个复合注解，包含3个重要的注解@SpringBootConfiguration、@EnableAutoConfiguration、@ComponentScan。