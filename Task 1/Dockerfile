# Declare image to use as Base Image during Build process
FROM node:lts-alpine3.20

# Set the working directory to required location to node js copy files
WORKDIR /app

# Copy all package json files
COPY package*.json ./

# Install NPM and other dependencies as per requirements
RUN npm install

# Copy the application code. This will copy all files in current directory to WORKDIR set above. here it is /app.
COPY . .

# Expose the port the app runs on
EXPOSE 3000

# Command to run the application
CMD ["node", "app.js"]
