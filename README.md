# Udagram microservices assignment

This assignment consisted of breaking down a monolith app into microservices. After breaking up the services, I 
configured docker images for each of the services, which are hosted publicly at my docker hub account. 

The CI process works in the following manner: 
- The .travis.yml file defines the steps to go through
- First we set up the tools we need
- We build the docker images and push them to docker hub
- We decrypt the kubeconfig and set the KUBECONFIG environment variable
- We use kubectl to deploy the new images