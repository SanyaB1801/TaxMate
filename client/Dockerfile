# Frontend Dockerfile
# Stage 1: Build the React application
FROM node:18 AS build

# Set the working directory
WORKDIR /app

# Copy package.json and package-lock.json (if available)
COPY client/package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY client/ .

# Build the application
RUN npm run build

# Stage 2: Serve the application using a lightweight server
FROM nginx:alpine

# Copy the built application from the build stage
COPY --from=build /app/dist /usr/share/nginx/html

# Expose port 80
EXPOSE 80

# Start Nginx
CMD ["nginx", "-g", "daemon off;"]