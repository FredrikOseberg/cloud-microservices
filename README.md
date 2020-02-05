# Udagram microservices assignment

This assignment consisted of breaking down a monolith app into microservices. After breaking up the services, I 
configured docker images for each of the services, which are hosted publicly at my docker hub account. 

The CI process works in the following manner: 
- The .travis.yml file defines the steps to go through
- First we set up the tools we need
- We build the docker images and push them to docker hub
- We decrypt the kubeconfig and set the KUBECONFIG environment variable
- We use kubectl to deploy the new images

## Running locally

In order to run the application locally you need to setup a amazon RDS database and set the following 
environment variables in your shell:

```
export UDAGRAM_POSTGRESS_USERNAME=value
export UDAGRAM_POSTGRESS_PASSWORD=value
export UDAGRAM_POSTGRESS_DATABASE=value
export UDAGRAM_POSTGRESS_HOST=value
export UDAGRAM_AWS_REGION=value
export UDAGRAM_AWS_PROFILE=value 
export UDAGRAM_AWS_MEDIA_BUCKET=value
export UDAGRAM_JWT_SECRET=value
export URL=value
```

Once this is setup you can run the application with the following command:
```
docker-compose -f udacity-c2-deploy/docker-compose.yml up

// alternatively 
cd udacity-c2-deploy
docker-compose up
```