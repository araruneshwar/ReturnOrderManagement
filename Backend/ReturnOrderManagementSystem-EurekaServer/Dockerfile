#building
FROM maven:3.8.4-openjdk AS build
COPY src /home/app/src
COPY pom.xml /home/app
RUN mvn -f /home/app/pom.xml -DskipTests=true  package

#packaging
FROM openjdk:8-jdk-alpine
COPY --from=build home/app/target/ReturnOrderManagementSystem-EurekaServer-0.0.1-SNAPSHOT.jar /home/app/ReturnOrderManagementSystem-EurekaServer.jar
WORKDIR /home/app
EXPOSE 8761
ENTRYPOINT java -jar ReturnOrderManagementSystem-EurekaServer.jar