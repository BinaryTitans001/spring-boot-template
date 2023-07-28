
# Template for Spring Boot application
Includes web-server on port 9080 

## Prerequisites:
- Maven 3
- JDK 17

## How to build:
    mvn clean install

#### Build Docker image with application inside:
    docker build ./ -t backend-template-app

## Start application using starting script:
Use [run.bat](./run.bat) script

## Start application (vs in-memory DB H2) by running executable jar:
    java -jar target/spring-boot-template-0.0.1-SNAPSHOT.jar \
     --spring.datasource.url=jdbc:h2:mem:testdb \
     --spring.datasource.username=sa \
     --spring.datasource.password=password \
     --spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.H2Dialect \
     --spring.datasource.driver-class-name=org.h2.Driver

## Same thing but using Spring profile to determine properties:
    java -jar target/spring-boot-template-0.0.1-SNAPSHOT.jar \
     --spring.profiles.active=dev

## Start application (vs in-memory DB H2) using Maven:
    mvn spring-boot:run -Dspring-boot.run.arguments="\
    --spring.datasource.url=jdbc:h2:mem:testdb \
    --spring.datasource.username=sa \
    --spring.datasource.password=password \
    --spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.H2Dialect \
    --spring.datasource.driver-class-name=org.h2.Driver"

## Same thing but using Spring profile to determine properties:
    mvn spring-boot:run -Dspring-boot.run.arguments=--spring.profiles.active=dev

## Start application in Docker container (vs Postgres DB in Docker):
    docker-compose up

## Start application in Docker container (vs Postgres DB in Docker) with rebuild service image:
    docker-compose up --build --force-recreate --no-deps

## Link for quick check:
    http://localhost:9080/articles

## Swagger documentation:
    http://localhost:9080/swagger-ui.html

### Get endpoint
```
curl -i http://localhost:9080/api/v1/hello
```
