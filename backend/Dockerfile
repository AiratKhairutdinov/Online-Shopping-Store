FROM openjdk:11

WORKDIR /app

COPY src/docker/spring-boot-ecommerce-0.0.1-SNAPSHOT.jar  ./

EXPOSE 8443

ENTRYPOINT ["java", "-jar", "spring-boot-ecommerce-0.0.1-SNAPSHOT.jar"]