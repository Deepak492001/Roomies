# Stage 1: Build the project using Maven
FROM maven:3.8.5-openjdk-17 AS build
# WORKDIR /app

# Copy the pom.xml and download dependencies only (cache layer)
# COPY pom.xml ./
# RUN mvn dependency:go-offline -B

# Copy the source code
COPY  backend/RentalProject .

# Build the project, skipping tests for faster builds
RUN mvn clean package -DskipTests

# Stage 2: Create a lightweight image with the built JAR file
FROM openjdk:17.0.1-jdk-slim
# WORKDIR /app

# Copy the JAR file from the build stage
# COPY --from=build /target/RentalProject-0.0.1-SNAPSHOT.jar RentalProject.jar
 COPY --from=build /target/*.jar RentalProject.jar
# Expose the necessary port
EXPOSE 8080

# Run the application
ENTRYPOINT ["java", "-jar", "RentalProject.jar"]
