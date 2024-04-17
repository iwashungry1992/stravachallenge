# Use official Node.js image as the base image
FROM node:latest AS build

# Set the working directory in the container
WORKDIR /usr/src/app

# Copy the package.json and package-lock.json files to the working directory
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the entire Angular app to the working directory
COPY . .

# Build the Angular app for production
RUN npm run build

# Use nginx image as the base image for serving Angular app
FROM nginx:latest

# Copy built Angular app from the previous stage to nginx directory
COPY --from=build /usr/src/app/dist/my-angular-app /usr/share/nginx/html

# Expose port 80 to allow outside access to your app
EXPOSE 80
