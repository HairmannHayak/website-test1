# Step 1: Use an official Node.js runtime as a parent image
FROM node:16 AS build

# Step 2: Set the working directory in the container
WORKDIR /app

# Step 3: Copy the current directory contents into the container
COPY . .

# Step 4: Install dependencies
RUN npm install

# Step 5: Build the React app for production
RUN npm run build

# Step 6: Install the official Nginx image to serve the build
FROM nginx:alpine

# Step 7: Copy the build folder into the Nginx container
COPY --from=build /app/build /usr/share/nginx/html

# Step 8: Expose the port 80 (default for Nginx)
EXPOSE 80

# Step 9: Start the Nginx server
CMD ["nginx", "-g", "daemon off;"]