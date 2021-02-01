FROM node

WORKDIR /app

# Tip - when re-building images, each layer gets checked for changes. If there are none in each layer, the layer gets skipped
# and moves on to save time. Since package-lock.json is huge, if we copy package.json over first, then run an nmp install, docker
# will see that package.json and package-lock havent changed, and therefore when we make changes just to source code, there is
# no need to re-run npm install just for application code changes
COPY package.json /app

# The run command is run while the image is being created. In this case thats good because it will npm install and copy
# the node_modules dir into the image automatically. It happens at the image level, not the container level
RUN npm install

# The first dot says 'copy everything from same dir as this Dockerfile'
# Second dot creates a folder to copy to , and is relative to container root
COPY . /app

# Expose port 3000 for http connection
EXPOSE 80/tcp

# This cmd command we dont want to happen during image creation, we want it to happen during the run of the container
# so that is why we use cmd vs run here, because we dont want to run node server.js until we have a container spun up
CMD ["node", "server.js"]

# Finally, get the image id by using docker image ls, then to run, docker run -p 3000:80 <imgId>
# The -p maps localhost port 3000 to internal container port 80, where the node app is listening