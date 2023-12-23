# Microservices with Spring Cloud Advanced Demo Project 


In this project I'm demonstrating you the most interesting features of [Spring Cloud Project](https://spring.io/projects/spring-cloud) for building microservice-based architecture.

## Getting Started 
Currently you may find here some examples of microservices implementation using different projects from Spring Cloud. 

### Usage

Build the apps with images (we need ji for `config-service` since it contains `curl`):
```shell
$ mvn clean package -Pbuild-image jib:dockerBuild
```

Then run all the containers with `docker-compose`:
```shell
$ docker-compose up
```

## Architecture

Our sample microservices-based system consists of the following modules:
- **gateway-service** - a module that Spring Cloud Netflix Zuul for running Spring Boot application that acts as a proxy/gateway in our architecture.
- **config-service** - a module that uses Spring Cloud Config Server for running configuration server in the `native` mode. The configuration files are placed on the classpath.
- **discovery-service** - a module that depending on the example it uses Spring Cloud Netflix Eureka or Spring Cloud Netlix Alibaba Nacos as an embedded discovery server.
- **employee-service** - a module containing the first of our sample microservices that allows to perform CRUD operation on in-memory repository of employees
- **department-service** - a module containing the second of our sample microservices that allows to perform CRUD operation on in-memory repository of departments. It communicates with employee-service. 
- **organization-service** - a module containing the third of our sample microservices that allows to perform CRUD operation on in-memory repository of organizations. It communicates with both employee-service and organization-service.

The following picture illustrates the architecture described above.

<img src="https://piotrminkowski.files.wordpress.com/2018/04/spring-cloud-1.png" title="Architecture"><br/>

