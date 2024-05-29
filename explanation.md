# 1 THE CHOICE OF BASE IMAGE.

The choice base image is the Node.js alpine image since they are suitable for resource-constrained environments or when minimizing image sizes is a priority of which in this case is a requirement.

# 2 THE DOCKERFILE DIRECTIVE.

Dockerfile directive is that  the base images is node:14-alpine,which the create a working directory to in the path client/app and backend/app ,afterwards the images copy the dependencies from the package.json file run npm install to install any other required dependencies for running the image .The image then copies the files in the root of the project .In backend the port 5000 is exposed for viewing results as well as in client the port 3000 is exposed and the results can be viewed from there.
Lastly the CMD commands are run once the image is run.

# 3 DOCKER-COMPOSE NETWORKING.

Since the containers created need to be communicating a network is created for which mine is yolo_net which enable the containers to communicate once lauched .
I also applied the ports for viewing of the results.

# 4 DOCKER-COMPOSE VOLUME

Docker volumes that I created enable the data of the containers to be stored outside the container that way to enable persistence even when the container are not running.
For the client-container1 the data is to be stored ("./client:/var/www/client") in this directory while for the backend ("./backend:/var/www/backend") and finally for the yolo.db (mongo-data:/data/db) in this directory.

# 5 GIT WORKFLOW USED FOR ACHIEVEMENT.

I changed directory to the client and built a Dockerfile to produce the image.To ensure the container was running successfully, I utilized the docker build command to build the image and the docker run program to create and use the container. I carried out the same actions in the backend directory, and the exposed ports demonstrated that the containers were operating without a hitch. As you can see from the snapshot attached, I removed the generated images and container and set up the docker-compose file in the root directory to react to them. I also executed docker-compose push to present the images on the Dockerhub.