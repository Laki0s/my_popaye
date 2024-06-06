FROM maven:3.9.6-eclipse-temurin-21-alpine as builder
WORKDIR /app
COPY pom.xml .
RUN mvn dependency:resolve && mvn package
COPY . /app
RUN mvn package
FROM eclipse-temurin:21-jre-alpine
WORKDIR /app
COPY --from=builder /app/target/worker-jar-with-dependencies.jar /app
CMD ["java", "-jar", "worker-jar-with-dependencies.jar"]