FROM maven:3.8.5-openjdk-17 AS build
COPY backend/RentalProject .
RUN mvn clean package -DskipTests

FROM openjdk:17.0.1-jdk-slim
COPY --from=build /target/*.jar roomiehub-docker.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "/roomiehub-docker.jar"]
