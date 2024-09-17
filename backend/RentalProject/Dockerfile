# Stage 1: Build
FROM maven:3.8.5-openjdk-17 AS build
# WORKDIR /app

# Copy only the backend project (RentalProject) to the build context
COPY backend/RentalProject .
RUN mvn clean package -DskipTests

# Stage 2: Runtime
FROM openjdk:17.0.1-jdk-slim
COPY --from=build /target/roomiehub-docker-0.0.1-SNAPSHOT.jar roomiehub-docker.jar
# WORKDIR /app

# Copy the generated JAR file from the build stage
# COPY --from=build /app/target/roomiehub-docker.jar roomiehub-docker.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "roomiehub-docker.jar"]


# FROM maven:3.8.5-openjdk-17 AS build
# COPY . .
# RUN mvn clean package -DskipTests

# FROM openjdk:17.0.1-jdk-slim
# COPY --from=build /target/demo-0.0.1-SNAPSHOT.jar demo.jar
# EXPOSE 8080
# ENTRYPOINT ["java","-jar","demo.jar"]