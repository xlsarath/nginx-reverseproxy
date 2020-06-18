# Overview
This is a very simple, bare-bones NodeJS and ExpressJS project created for you to use with Docker.

# Local Setup
* Install dependencies: `npm install`
* Run server: `node server.js`

# Usage
By default, the application should be loaded on `localhost:8080`. It should provide an HTTP 200 response when loaded at `localhost:8080/health`.

# Container Setup
* Build image: `docker build -t simple-express .`
* Tag with Hub: `docker tag simple-express xlsarathchandra/simple-express`
* Push : `docker push xlsarathchandra/simple-express`
* Docker images `docker images`
* Run container with image: `docker run {image_id}` where `image_id` can be retrieved by running `docker images` and found under the column `IMAGE ID`

# Kubectl
* deployment yaml : `kubectl apply -f deployment.yaml`
* service yaml : `kubectl apply -f service.yaml`
* opening container : `kubectl exec -it my-app-2-svc bash`
* access app on 8080: `root@my-app-2-6c47c56c9-dqn9k:/usr/src/app# curl http://my-app-2-svc:8080/health`
* to access logs : `kubectl logs my-app-2-6c47c56c9-twn8l`
* to delete serivce : `kubectl delete service my-app-2-6c47c56c9-twn8l`
* to delete pod : `kubectl delete pod my-app-2-6c47c56c`
* to delete deployment : `kubectl delete deployment.apps/my-app-2`


# Container teardown
* Remove container: `docker kill {container_id}` where `container_id` can be retrieved by running `docker ps` and found under the column `CONTAINER ID`

# reverse proxy test
### root@my-app-2-6c47c56c9-dqn9k:/usr/src/app# curl http://my-app-2-svc:8080/health
### Hello!root@my-app-2-6c47c56c9-dqn9k:/usr/src/app# curl http://reverseproxy-svc:8080/api/health

# Extra commands
* `kubectl get all`
* `kubectl get pods`
* `kubectl get service`
* `kubectl describe services`
* `kubectl describe pods pod-name`