# use this empty Dockerfile to build your assignment

# This dir contains a Node.js app, you need to get it running in a container
# No modifications to the app should be necessary, only edit this Dockerfile

# Overview of this assignment
# use the instructions from developer below to create a working Dockerfile
# feel free to add command inline below or use a new file, up to you (but must be named Dockerfile)
# once Dockerfile builds correctly, start container locally to make sure it works on http://localhost
# then ensure image is named properly for your Docker Hub account with a new repo name
# push to Docker Hub, then go to https://hub.docker.com and verify
# then remove local image from cache
# then start a new container from your Hub image, and watch how it auto downloads and runs
# test again that it works at http://localhost


# Instructions from the app developer
# - you should use the 'node' official image, with the alpine 6.x branch
# - this app listens on port 3000, but the container should launch on port 80
  #  so it will respond to http://localhost:80 on your computer
# - then it should use alpine package manager to install tini: 'apk add --update tini'
# - then it should create directory /usr/src/app for app files with 'mkdir -p /usr/src/app'
# - Node uses a "package manager", so it needs to copy in package.json file
# - then it needs to run 'npm install' to install dependencies from that file
# - to keep it clean and small, run 'npm cache clean --force' after above
# - then it needs to copy in all files from current directory
# - then it needs to start container with command '/sbin/tini -- node ./bin/www'
# - in the end you should be using FROM, RUN, WORKDIR, COPY, EXPOSE, and CMD commands

FROM node:alpine3.10

#Just expose the port that it's needed for Node.js, durin the run of the container it will be forwarded to
# port 80, using -p 80

EXPOSE 3000


RUN apk add --update tini 

RUN mkdir -p /usr/src/app

WORKDIR /usr/src/app

COPY package.json package.json

RUN npm install && npm cache clean --force

# - then it needs to copy in all files from current directory, meaning that we will copy all the files from the host
# to the current directory /usr/src/app on the image of the dockerfile.
# To copy all this files, instead of using *, it's better to use ".", so the final instance will be "COPY . ." 

COPY . .

#- then it needs to start container with command '/sbin/tini -- node ./bin/www'
#To do this, it's needed the CMD
#IMPORTANT: on CMD, all the parameters that are separated by SPACE need to be 
#ENCAPSULATED using "", so instead of writting "/sbin/tini -- node ./bin/www", NEEDS TO BE WRITTEN:
#               CMD ["sbin/tini", "--", "node", "./bin/www"]

CMD ["/sbin/tini", "--", "node", "./bin/www"]

# IMPORTANT!!. Before to run "docker push" it's needed to tag image to your account, for example:

# docker tag node_js_test:latest pdus/node_js_test:version1

# AND THEN IT'S POSSIBLE TO PUSH IT TO MY REPOSITORY. LIKE THIS:
# docker push pdus/node_js_test:version1


    




# Bonus Extra Credit
# this will not have you setting up a complete image useful for local development, test, and prod
# it's just meant to get you started with basic Dockerfile concepts and not focus too much on
# proper Node.js use in a container. **If you happen to be a Node.js Developer**, then 
# after you get through more of this course, you should come back and use my 
# Node Docker Good Defaults sample project on GitHub to change this Dockerfile for 
# better local development with more advanced topics
# https://github.com/BretFisher/node-docker-good-defaults
