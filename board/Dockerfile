# Build stage
FROM maven:3.9.9-eclipse-temurin-11 AS builder

WORKDIR /build
COPY board/pom.xml .
COPY board/src ./src

RUN mvn clean package -DskipTests


# Runtime stage
FROM eclipse-temurin:11-jre-jammy

WORKDIR /app

COPY --from=builder /build/target/*.jar app.jar

EXPOSE 8080

ENTRYPOINT ["java","-jar","app.jar"]
