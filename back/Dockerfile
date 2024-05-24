# Use an OpenJDK base image
FROM openjdk:17-slim

# Set the working directory in the container
WORKDIR /app

# Copy the built jar file into the Docker image
COPY target/blogs-0.0.1-SNAPSHOT.jar myapplication.jar

# Expose port 9090 for the application
EXPOSE 9090

# Command to run the application
CMD ["java", "-jar", "myapplication.jar"]

