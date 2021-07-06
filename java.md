---
title: "Prácticas con Java y sus tecnologías"
description: "Hablemos un poco sobre Java, aquí podrás encontrar tips y respuestas a los problemas comunes con Spring Boot"
category: backend
---

## Spring Boot

### Jackson local date time deserialize

Si se recibe el error `Failed to convert value of type 'java.lang.String' to required type 'java.time.LocalDate'` se debe a que no se esta serializado el contenido de los parámetros.

Ejemplo para aceptar parámetros de tipo fecha serializados:

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

Si se esta usando un objeto como parámetro y se recibe el siguiente error `Failed to instantiate [com.example.demo.DateType]: No default constructor found` se debe a que hay que especificar la forma de serializar las propiedades.

Ejemplo para deserealizar parámetros envueltos en un objeto:

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

## Spring security

- X-XSS-Protection: 1; mode:block, indica al navegador que se active la protección XSS (Cross Site Scripting) y bloquea el contenido.
- X-Content-Type-Options: nosniff, previene que se determine los tipos de archivos, funciona para archivos que no están declarados en la aplicación.
- CSRF Cross Site Request Forgery - se usa una cookie para validar el envió de solicitudes de tipo POST, PUT, DELETE o PATCH, sincroniza un token entre el servidor y el navegador.
- X-Frame-Options: DENY - deshabilita la posibilidad de cargar el contenido en las etiquetas frame, iframe y object
- content-security-policy: default-src

```java
//Seguridad básica
http.authorizeRequests().anyRequest().authenticated()
        .and().httpBasic();

//Desactivar cache
http.requestCache().disable()

//Desactivar headers
http.headers().disable()

//Deny frame options
http.headers().frameOptions().disable()
http.headers().frameOptions().sameOrigin()

//content-security-policy
http.headers().contentSecurityPolicy("script-src: self")
http.headers().contentSecurityPolicy("script-src: http://{domain}...")

//Referrer policy
http.headers().referrerPolicy().policy(ReferrerPolicy.ORIGIN)
```

### Https spring boot

Generar un certificado con la validación expresada en días

```bash
keytool -genkey -alias tomcat -storetype PKCS12 -keyalg RSA -keysize 2048 -keystore keystore.p12 -vadility 400
```

```yml
server:
  port: 8443
  ssl:
    key-store-password: password
    key-store: classpath:keystore.p12
    key-store-type: PKCS12
    key-alias: tomcat

logging:
  level:
    root: WARN
    com.memorynotfound: DEBUG
    org.springframework.web: DEBUG
    org.springframework.security: DEBUG
```

### ACME Automated Certificate Management Environment protocol

#### Requerimientos

- El puerto 80 debe estar habilitado para la verificación
- Python 2.7
- [Instrucciones de letsencrypt](https://letsencrypt.org)

#### Instalar certbot

```bash
git clone https://github.com/certbot/certbot
./certbot-auto certonly -a standalone -d {domain.com}
```

#### Convertir con OpenSSL

```bash
openssl pkcs12 -export -in fullchain.pem -inkey privkey.pem -out keystore.p12 -name tomcat -CAfile chain.pem -caname root
```

[Verificar la seguridad de un hsts](https://hstspreload.org)

### Configurar CSRF en SPA

Hasta las aplicaciones SPA necesitan una protección CSRF para evitar problemas de seguridad.

```java
http.csrf().csrfTokenRepository(CookieCsrfTokenRepository.withHttpOnlyFalse()).and()
```

#### withHttpOnlyFalse()

El navegador debe permite la ejecución de javascript originada desde el mismo origen de la cookie.

### [Encriptar llaves privadas](http://www.jasypt.org/download.html)

```bash
encrypt input="password" password={password_encryption}
```

```xml
<dependency>
    <groupId>com.github.ulisesbocchio</groupId>
    <artifactId>jasypt-spring-boot-starter</artifactId>
    <version>3.0.3</version>
</dependency>
```

```yml
server:
  key-store-password: ENC({encrypted_data})

jasypt:
  encryptor:
    password: { password_encryption } - ${JASYPT_ENCRYPTOR_PASSWORD:}
    iv-generator-classname: org.jasypt.iv.NoIvGenerator
    algorithm: PBEWithMD5AndTripleDES
```

#### Secret Management

- Rotar frecuentemente
- Auditar el uso de las llaves
- Secret sprawl, spring vault
- Centralizar los datos secretos
- Proveer acceso granular a los secretos
- Los datos debe viajar siempre encriptados

**Referencias:**

- [Formatting Java Time with JSON](https://touk.pl/blog/2016/02/12/formatting-java-time-with-spring-boot-using-json/)
- [Sobre el uso de parámetros de tipo fecha](https://www.baeldung.com/spring-date-parameters)
- [Formato json de LocalTime](https://touk.pl/blog/2016/02/12/formatting-java-time-with-spring-boot-using-json/)
- [Google Research](https://research.google/pubs/pub45542/)
