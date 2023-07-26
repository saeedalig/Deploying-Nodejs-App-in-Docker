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
docker build -t nodejs-app-image .

The -t flag is used to tag the image with the name "nodejs-app-image". The dot (.) at the end indicates the current directory as the build context.
```

To verify that the Docker image has been successfully built or not.
```bash
docker images
```
![Alt text](<Screenshot (60).png>)


Rub the Docker image
```bash
docker run -d -p 3000:3000 --name nodejs-app-app nodejs-app-image

The -p flag maps the port 3000 from the host to the container, allowing you to access the app from your browser
```

![Alt text](<Screenshot (61).png>)

To verify the Docker container
```bash
docker ps
```

![Alt text](<Screenshot (61).png>)




Thats all you need to do, to run this basic example.


