# Udagram microservices assignment

This assignment consisted of breaking down a monolith app into microservices. After breaking up the services, I 
configured docker images for each of the services, which are hosted publicly at my docker hub account.

https://hub.docker.com/r/khare123/udacity-restapi-user
https://hub.docker.com/r/khare123/udacity-restapi-feed
https://hub.docker.com/r/khare123/reverse-proxy
https://hub.docker.com/r/khare123/udacity-frontend


The CI process works in the following manner: 
- The .travis.yml file defines the steps to go through
- First we set up the tools we need
- We build the docker images and push them to docker hub
- We decrypt the kubeconfig and set the KUBECONFIG environment variable
- We use kubectl to deploy the new images

## Architecture 

The app is divided into 4 services. One frontend client, one nginx reverse-proxy, and two backend services. The nginx proxy
proxies the frontends requests to either of the backend services based on the path of the request.

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

## CI Setup

In order to push a new version to production, make the required changes and build the javascript. Then push 
the updated code to the master branch. This will trigger a process that builds new images and deploys them
on kubernetes.