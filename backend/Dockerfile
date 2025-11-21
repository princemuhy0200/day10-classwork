# stage 1: build with maven

FROM maven:3.8.6-openjdk-11 as build

WORKDIR /app

COPY pom.xml .

COPY src ./src

RUN mvn clean package -DskipTests

# stage 2: run the build with eclipse

FROM eclipse-temurin:11-jre

WORKDIR /app

COPY --from=build /app/target/demo-1.0.0.jar app.jar

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "app.jar"]