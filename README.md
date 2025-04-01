# Simple Minikube project
## Requirements
* [Minikube](https://minikube.sigs.k8s.io/docs/)
	* Run $ minikube start

## Running with Docker
$ docker compose up -d

$ curl localhost:5000 or view http://localhost:5000

## Running in Minikube
### 1. Set environment variables
$ eval $(minikube docker-env)

### 2. Build the container
$ docker build -t hello-foo-image .

### 3. Create deployment
$ kubectl apply -f deployment.yaml

### 4. Create service
$ kubectl expose deployment hello-foo-deployment --type=LoadBalancer --port=80 --target-port=5000

### 5. Check everything is running properly
$ kubectl get pods; kubectl get deployments; kubectl get svc

### 6. Open deployment in browser
$ minikube service hello-foo-deployment

## Troubleshooting
### When running with Docker, site isn't available
Check that you haven't set the environment variables for Minikube. If you have, open a new terminal.

### Cleaning up Kubernetes
kubectl delete deployments --all;
kubectl delete services --all;
kubectl delete pods --all;
