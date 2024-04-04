# Use an official Maven image as the base image
FROM maven:3.8.4-openjdk-11 AS build

# Set the working directory in the container
WORKDIR /app

# Copy the pom.xml and the project files to the container
COPY pom.xml .
COPY src ./src

# Build the application
RUN mvn clean package

# Use an official OpenJDK image as the base image
FROM openjdk:11-jre-slim

# Set the working directory in the container
WORKDIR /app

# Copy the JAR file from the previous stage
COPY --from=build /app/target/springboot-first-app-0.0.1-SNAPSHOT.jar .

# Expose port 8080
EXPOSE 8080

# Set the command to run the application
CMD ["java", "-jar", "springboot-first-app-0.0.1-SNAPSHOT.jar"]
