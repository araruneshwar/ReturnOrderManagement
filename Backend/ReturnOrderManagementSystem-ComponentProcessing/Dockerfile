#building
FROM maven:3.8.4-openjdk AS build
COPY src /home/app/src
COPY pom.xml /home/app
RUN mvn -f /home/app/pom.xml -DskipTests=true  package

#packing
FROM openjdk:8-jdk-alpine
COPY --from=build home/app/target/ReturnOrderManagementSystem-ComponentProcessing-0.0.1-SNAPSHOT.jar /home/app/ReturnOrderManagementSystem-ComponentProcessing.jar
WORKDIR /home/app
EXPOSE 9090
ENTRYPOINT java -jar ReturnOrderManagementSystem-ComponentProcessing.jar