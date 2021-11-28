# Project Git URLS

[Udagram Frontend](https://github.com/ntickoo/udagram-frontend)  
[Udagram ReverseProxy](https://github.com/ntickoo/udagram-reverseproxy)  
[Udagram User Microservice](https://github.com/ntickoo/udagram-api-user)  
[Udagram Feed Microservice](https://github.com/ntickoo/udagram-api-feed)  
[Environment Config and Project submission Details]()  
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

[comment]: NAME           READY   UP-TO-DATE   AVAILABLE   AGE
[comment]: backend-feed   2/2     2            2           32m
[comment]: backend-user   2/2     2            2           32m
[comment]: frontend       2/2     2            2           32m
[comment]: reverseproxy   2/2     2            2           32m

kubectl expose deployment frontend --type=LoadBalancer --name=publicfrontend
kubectl expose deployment reverseproxy --type=LoadBalancer --name=publicreverseproxy



kubectl set image deployment frontend frontend=tickoon/udagram-frontend:v2


http://ad45713d3b8654e85875ffada715bc0e-1209343989.ca-central-1.elb.amazonaws.com:8080/api/v0/feed


http://a0f91204ff0604b7f822d63d32385554-689742264.ca-central-1.elb.amazonaws.com:8100


kubectl exec --stdin --tty    -- /bin/bash









