FROM schoolofdevops/maven:spring as build
WORKDIR /app
COPY . . 
RUN mvn package -DskipTests

FROM build as test
CMD mvn clean tests

FROM openjdk:8-alpine as run
COPY --from=build target/spring-petclinic-2.3.1.BUILD-SNAPSHOT.jar /run/petclinic.jar
EXPOSE 8080
CMD java -jar /run/petclinic.jar