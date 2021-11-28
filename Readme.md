# Project Git URLS

[Udagram Frontend](https://github.com/ntickoo/udagram-frontend)  
[Udagram ReverseProxy](https://github.com/ntickoo/udagram-reverseproxy)  
[Udagram User Microservice](https://github.com/ntickoo/udagram-api-user)  
[Udagram Feed Microservice](https://github.com/ntickoo/udagram-api-feed)  
[Environment Config and Project submission Details](https://github.com/ntickoo/kubernetes-config)

Docker build files and kubernetes deployment and service files are in the deploy project of each module e.g. frontend, reverseproxy, user, feed microservice. This was done to speed up and simplify docker build.

[UDAGRAM URL](http://a0f91204ff0604b7f822d63d32385554-689742264.ca-central-1.elb.amazonaws.com:8100)  
The above url will be removed as keeping the cluster alive is accruing lot of charges.

screenshot directory contains all the project submission requirements.

# Docker Deployment
----------
# Apply env variables and secrets
kubectl apply -f aws-secret.yaml  
kubectl apply -f env-secret.yaml  
kubectl apply -f env-configmap.yaml


# Deployments - Double check the Dockerhub image name and version in the deployment files

kubectl apply -f ../udagram-api-user/deploy/deployment.yaml  
kubectl apply -f ../udagram-api-feed/deploy/deployment.yaml  
kubectl apply -f ../udagram-reverseproxy/deploy/deployment.yaml  
kubectl apply -f ../udagram-frontend/deploy/deployment.yaml


# Service
kubectl apply -f ../udagram-api-user/deploy/service.yaml  
kubectl apply -f ../udagram-api-feed/deploy/service.yaml  
kubectl apply -f ../udagram-reverseproxy/deploy/service.yaml  
kubectl apply -f ../udagram-frontend/deploy/service.yaml  


# To Assign a public IP to the frontend service

kubectl get deployments

kubectl expose deployment frontend --type=LoadBalancer --name=publicfrontend
kubectl expose deployment reverseproxy --type=LoadBalancer --name=publicreverseproxy



kubectl set image deployment frontend frontend=tickoon/udagram-frontend:v2


http://ad45713d3b8654e85875ffada715bc0e-1209343989.ca-central-1.elb.amazonaws.com:8080/api/v0/feed


http://a0f91204ff0604b7f822d63d32385554-689742264.ca-central-1.elb.amazonaws.com:8100










