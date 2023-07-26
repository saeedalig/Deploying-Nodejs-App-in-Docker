# Deploying-Nodejs-App-in-Docker

### Creating a Docker project to deploy a Node.js app that involves several steps.



Create a Project Directory and Navigate
```bash
mkdir docker-project
cd docker-project
```

Clone to repo
```bash
git clone https://github.com/saeedalig/Deploying-Nodejs-App-in-Docker.git
```

Navigate to the Repo you cloned
```bash
cd Deploying-Nodejs-App-in-Docker
```

Once you have accessed the concerned repository, you have to create a Dockerfile in order to build  a Docker image.

Create a Dockerfile (vscode)
```bash
touch Dockerfile
```

Write the set of instructions to the Dockerfile

```Dockerfile
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

Since you have created the Dockerfile, its time to build the Docker image from the Dockerfile you created in order to create a Docker container that will allow you to deploy your application.

Build the Docker image
```bash
docker build -t nodejs-app-img .
```





Step 4: Run the docker container from the image

```
docker run -d -p 3000:3000 IMAGE_NAME
```

Thats all you need to do, to run this basic example.


