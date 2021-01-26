# Sobre Java

## Spring Boot

### Jackson local date time deserialize

Si se recibe el error `Failed to convert value of type 'java.lang.String' to required type 'java.time.LocalDate'` se debe a que no se esta serializando el contenido de los parametos.

Ejemplo para aceptar parametros de tipo fecha serializados:

```java
@RestController
public class Controller {
    @GetMapping("/")
    public void get(
        @RequestParam
        @DateTimeFormat(pattern = "yyyy-MM-dd")
        LocalDate date,
        @RequestParam
        @DateTimeFormat(pattern = "kk:mm:ss")
        LocalTime time,
        @RequestParam
        @DateTimeFormat(pattern = "yyyy-MM-dd kk:mm:ss")
        LocalDateTime dateTime) {}
}
```

Si se esta usando un objeto como parametro y se recibe el siguiente error `Failed to instantiate [com.example.demo.DateType]: No default constructor found` se debe a que hay que especificar la forma de serializar las propiedades.

Ejemplo para deserealizar parametros envueltos en un objeto:

```java
public class DateType {
    @DateTimeFormat(pattern = "yyyy-MM-dd")
    private LocalDate date;
    @DateTimeFormat(pattern = "kk:mm:ss")
    private LocalTime time;
    @DateTimeFormat(pattern = "yyyy-MM-dd kk:mm:ss")
    private LocalDateTime dateTime;

    public LocalDate getDate() {
        return date;
    }

    public void setDate(LocalDate date) {
        this.date = date;
    }

    public LocalTime getTime() {
        return time;
    }

    public void setTime(LocalTime time) {
        this.time = time;
    }

    public LocalDateTime getDateTime() {
        return dateTime;
    }

    public void setDateTime(LocalDateTime dateTime) {
        this.dateTime = dateTime;
    }

    public DateType(LocalDate date, LocalTime time, LocalDateTime dateTime) {
        this.date = date;
        this.time = time;
        this.dateTime = dateTime;
    }

    public DateType() {}
}

@RestController
public class Controller {
    @PostMapping("/")
    public void post(@RequestBody DateType dateType) {}
}
```

#### Deseralización personalizada

```java
@Configuration
public class JacksonConfig {
    @Bean
    public Module jsonMapperJava8DateTimeModule() {
        SimpleModule module = new SimpleModule();

        module.addDeserializer(LocalDate.class, new JsonDeserializer<LocalDate>() {
            @Override
            public LocalDate deserialize(JsonParser jsonParser, DeserializationContext deserializationContext) throws IOException {
                return LocalDate.parse(jsonParser.getValueAsString(), DateTimeFormatter.ofPattern("yyyy-MM-dd"));
            }
        });

        module.addDeserializer(LocalTime.class, new JsonDeserializer<LocalTime>() {
            @Override
            public LocalTime deserialize(JsonParser jsonParser, DeserializationContext deserializationContext) throws IOException {
                return LocalTime.parse(jsonParser.getValueAsString(), DateTimeFormatter.ofPattern("kk:mm:ss"));
            }
        });

        module.addDeserializer(LocalDateTime.class, new JsonDeserializer<LocalDateTime>() {
            @Override
            public LocalDateTime deserialize(JsonParser jsonParser, DeserializationContext deserializationContext) throws IOException {
                return LocalDateTime.parse(jsonParser.getValueAsString(), DateTimeFormatter.ofPattern("yyyy-MM-dd kk:mm:ss"));
            }
        });

        return module;
    }
}

public class DateType {
    @JsonDeserialize(using = LocalDateTimeDeserializer.class)
    @JsonFormat(pattern = "yyyy/MM/dd kk:mm:ss")
    private LocalDateTime dateTime;

    public LocalDateTime getDateTime() {
        return dateTime;
    }

    public void setDateTime(LocalDateTime dateTime) {
        this.dateTime = dateTime;
    }
}
```

**Referencias:**

- [Formatting Java Time with JSON](https://touk.pl/blog/2016/02/12/formatting-java-time-with-spring-boot-using-json/)
- [Sobre el uso de parametros de tipo fecha](https://www.baeldung.com/spring-date-parameters)
- [Formato json de LocalTime](https://touk.pl/blog/2016/02/12/formatting-java-time-with-spring-boot-using-json/)
