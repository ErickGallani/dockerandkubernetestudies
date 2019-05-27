# Specify a base image
FROM node:alpine

# Define a default work directory
WORKDIR /my/app

# Copy files to the intermidiate container in this case package.json
COPY ./package.json ./

# Install dependencies
RUN npm install

# Copy more files, this approach is good to prevent unnecessary re-build because if docker detects that the index.js have changed, than, all the following commands will be executed
COPY ./index.js ./

# Default command
CMD [ "npm", "start" ]