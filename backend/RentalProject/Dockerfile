

# Stage 1: Build
FROM maven:3.8.5-openjdk-17 AS build

# Set working directory and copy the backend project (RentalProject)
WORKDIR /app
COPY backend/RentalProject .

# Build the Spring Boot application and skip tests
RUN mvn clean package -DskipTests

# Stage 2: Runtime
FROM openjdk:17.0.1-jdk-slim

# Copy the generated JAR file from the build stage
COPY --from=build /app/target/roomiehub-docker-0.0.1-SNAPSHOT.jar roomiehub-docker.jar

# Expose the application port
EXPOSE 8080

# Define the entry point to run the Spring Boot application
ENTRYPOINT ["java", "-jar", "roomiehub-docker.jar"]
