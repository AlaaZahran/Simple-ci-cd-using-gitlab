
# Project Title

This repository contains a simple CI/CD pipeline for testing, building, and deploying a Python app inside a container on EC2 instance on AWS.

# Prerequisites

Before you begin, you will need the following:

1- An AWS account

2- An EC2 instance running Docker  => you can use this repo to create an ec2 using terraform and install docker inside  [ec2 creation](https://github.com/AlaaZahran/Create-automated-infrastruture-on-aws-using-terraform..git)

3- Dockerhub account

# Pipeline Overview
The CI/CD pipeline consists of the following stages:

1- Test

This stage runs tests for your Python app 

- using runner that will be container using python image 
- install make tool which reposible for test 
- run test .

2- Build

This stage builds a Docker image for your Python app and pushes it to your dockerhub account .

- using runner that will be container using docker client image  to get command and pass it to docker demaon.

- using service container use docker demaon image to execute docker command

- Before script login to dockerhub using variables present your actual credentials  

- build image with image name and tag

- push to dockerhub

Deploy
This stage deploys the Docker container to your EC2 instance on AWS.

- using runner with default image ruby

- use ssh key to connect to ec2 which stored as variable

- execute ssh command with this commads

  - StrictHostKeyChecking=no => to avoid asked you for approve to add fingerprint add this automatic

  -  login to dockerhub using variables present your actual credentials

  -  docker ps -aq => id of all running container in our case it is one so pass this id to next command 

  - xargs docker stop => to stop this container 

  - xargs docker rm => to remove this container 

  - finally run container with port 5000 (host side) and map port 5000 (container side)


# Running the Pipeline
Any changes will commit will run pipeline.

# Conclusion

Congratulations! You have successfully set up a simple CI/CD pipeline to test, build, and deploy your Python app in a container on EC2 instance on AWS. Feel free to customize the pipeline to fit your specific needs.










