---
title: "Tips y prácticas para el uso de Docker"
description: ""
tags: backend
---

Comandos básicos de Docker para la ejecución de contenedores de aplicaciones de para el entorno de desarrollo.

## Elasticsearch

Versión que usa AWS Open Search Service

```bash
docker run --name es7.9 -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" -it docker.elastic.co/elasticsearch/elasticsearch-oss:7.9.0
```

Versión que usa Spring Cloud Data Elasticsearch

```bash
docker run --name es7.14 -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" -it docker.elastic.co/elasticsearch/elasticsearch:7.14.0
```

### Dependencias de Spring Cloud Data Elasticsearch

```bash
+--------------+----------------------------+----------------+-------------+
| Spring Data  | Spring Data Elasticsearch  | Elasticsearch  | Spring Boot |
+--------------+----------------------------+----------------+-------------+
| 2020.0.0     | 4.1.x                      |          7.9.3 | 2.3.x       |
| Neumann      | 4.0.x                      |          7.6.2 | 2.3.x       |
| Moore        | 3.2.x                      |          6.8.4 | 2.2.x       |
| Lovelace     | 3.1.x                      |          6.2.2 | 2.1.x       |
| Kay          | 3.0.x                      |          5.5.0 | 2.0.x       |
| Ingalls      | 2.1.x                      |          2.4.0 | 1.5.x       |
+--------------+----------------------------+----------------+-------------+
```

### Elasticsearch Client y Spring Boot

Soporte para cambiar la version del cliente de Elasticsearch en Spring Boot

```groovy
buildscript {
    ext {
        set('elasticsearch.version', '7.12.1')
    }
}

dependencies {
    compileOnly (
//          downgrade to spring-data-elasticsearch:4.2.7 and avoid the OpenSearch error "Elasticsearch version 6 or more is required"
          "org.springframework.data:spring-data-elasticsearch:4.2.7",
    )
```
