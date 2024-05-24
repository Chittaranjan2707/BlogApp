# Use an official Node runtime as a parent image
FROM node:20-alpine

# Set the working directory in the container
WORKDIR /app

# Copy package.json and possibly package-lock.json for better caching
COPY package.json package-lock.json* ./

# Install dependencies, suppress npm warnings
RUN npm install --loglevel=error

# Copy the rest of your app's source code from your host to your image filesystem.
COPY . .

# Build the application
RUN npm run build

# Expose the port the app runs on
EXPOSE 3000
