# Deploying-Nodejs-App-in-Docker

### Creating a Docker project to deploy a Node.js app that involves several steps.



Create a Project Directory and Navigate
```bash
mkdir docker-project
cd docker-project
```

Clone to repo
'''bash
git clone https://github.com/saeedalig/Deploying-Nodejs-App-in-Docker.git
```

Navigate to the Repo you cloned
'''bash
cd Deploying-Nodejs-App-in-Docker
```

Once you have accessed the concerned repository, you have to create a Dockerfile in order to build  a Docker image.

Create a Dockerfile (vscode)
'''dockerfile
touch Dockerfile
```

Write the set of instructions to the Dockerfile
```dockerfile
# Base Image.
FROM node:latest

#  app directory, where your it will live .
WORKDIR /app

# A wildcard is used to ensure both package.json AND package-lock.json are copied
COPY package*.json ./

# Installing the packages while the image is building
RUN npm install

# Copy rest of the files 
COPY . .

# The app binds to port 3000, so exposing port 3000 to be used by the docker network
EXPOSE 3000

# Runtime command to be executed when the container is launched
CMD ["node", "app.js"]
```












# Dockerfile for Nodejs Webapp

Almost a complete Dockerfile required to make your Nodejs web app run inside a Docker container.

The Dockerfile:

```dockerfile
# we will use the latest version of node available from the Docker Hub.
FROM node:latest

# Create app directory, where your app will live its lifetime.
WORKDIR /usr/src/app

# Install app dependencies
# A wildcard is used to ensure both package.json AND package-lock.json are copied
COPY package*.json ./

# Installing the packages while the image is building
RUN npm install

# Bundle app source, i.e. copying all your required files for the app
# Note: files & folders inside .dockerignore will not be copied.
COPY . .

# The app binds to port 3000, so exposing port 3000 to be used by the docker network
EXPOSE 3000

# Runtime command to be executed when the container is launched
CMD ["node", "app.js"]
```

### Running the demo nodejs app on your machine

Step 1: 

```
git clone https://github.com/trulymittal/nodejs_dockerfile.git
```

Step 2: cd into the repo

```
cd nodejs_dockerfile
```

Step 3: Build the docker image

```
docker build -t IMAGE_NAME .
```

Step 4: Run the docker container from the image

```
docker run -d -p 3000:3000 IMAGE_NAME
```

Thats all you need to do, to run this basic example.


