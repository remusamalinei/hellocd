# hellocd

To create the application visit [Spring Initializr](https://start.spring.io/) and generate with the following settings:

- Project: Maven
- Language: Java
- Spring Boot: 3.0.1
- Artifact: hellocd
- Packaging: Jar
- Java: 17
- Dependencies > Add dependencies
    - Spring Web. Build web, including RESTful, applications using Spring MVC. Uses Apache Tomcat as the default
      embedded container.

### Run with Podman

```
cd
git clone {this repository}
podman volume create m2
podman container run \
    --rm \
    --interactive \
    --tty \
    --volume m2:/root/.m2 \
    --volume ~/hellocd:/app \
    --publish=8080:8080 \
    docker.io/maven:3.8-openjdk-17-slim \
    mvn spring-boot:run --file /app/pom.xml
```