Migrar-a-spring-boot3

I have migrated/updated this course from Spring boot version 2.6.0 to Spring boot version 3.0.0:

Two important changes in Spring boot 3:

- Spring Boot 3.0 requires Java 17 as a minimum version.
- Spring Boot 3.0 migrated Java EE to Jakarta EE APIs for all dependencies.

Here are the steps I did to update this course:

1. I have changed the Spring boot version from 2.6.0 to 3.0.0

```xml
<parent>
   <groupId>org.springframework.boot</groupId>
   <artifactId>spring-boot-starter-parent</artifactId>
   <version>3.0.0</version>
   <relativePath/> <!-- lookup parent from repository -->
</parent>
```

2. I have changed the Java version from 11 to 17

```xml
<properties>
   <java.version>17</java.version>
</properties>
```

3. I have used JPA annotations from `jakarta.peristance.*` (Earlier we referred from `javax.peristance.*`)

```java
import jakarta.persistence.*;
import lombok.*;
 
@Entity
@Table(name = "employees")
public class Employee {
// code goes here....
}
```

4.  Removed (commented out) Hibernate MySQL Dialect from the application.properties file (Spring Boot 3 uses Hibernate 6 so we don't have to specify Hibernate Dialect for MySQL database in the `application.properties` file. Hibernate automatically detect dialect based on various criteria. Read more about Dialect at Hibernate 6 Dialect)

```Properties
spring.jpa.show-sql=true
 
spring.datasource.url=jdbc:mysql://localhost:3306/demo?useSSL=false
spring.datasource.username=root
spring.datasource.password=Mysql@123
 
#spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQL5InnoDBDialect
 
spring.jpa.hibernate.ddl-auto=update
```

These are the simple 4 changes I made to migrate this course from Spring boot version 2.6.0 to Spring boot version 3.0.0.
