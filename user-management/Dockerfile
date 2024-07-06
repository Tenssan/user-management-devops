# Use an official Node runtime as a parent image
FROM node:lts-alpine

# Set the working directory
WORKDIR /usr/src/app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Ensure the database folder is copied correctly
COPY src/database /usr/src/app/src/database

# Build the NestJS application
RUN npm run build

# Expose the port the app runs on
EXPOSE 3000

# Run the app
CMD ["node", "dist/main"]
