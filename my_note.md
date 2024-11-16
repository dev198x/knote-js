# step 2: https://learnk8s.io/developing-and-packaging-nodejs-docker
 - Knote — a note taking app
 - Standard Express.js stack
 - Connecting a database
 - Saving and retrieving notes
 - Rendering Markdown to HTML
 - Uploading pictures
 - Deploying apps with containers
 - Linux containers
 - Containerising the app
 - Running the container
 - Uploading the container image to a container registry
 - Recap and next steps

```bash
# login to docker server
docker login

# add tag
docker tag knote datdaodev/knote-js:1.0.0

# push to remote repository
docker push datdaodev/knote-js:1.0.0

# run command
docker run \
  --name=knote \
  --rm \
  --network=knote \
  -p 3000:3000 \
  -e MONGO_URL=mongodb://mongo:27017/dev \
  datdaodev/knote-js:1.0.0

```
# step 3: https://learnk8s.io/deploying-nodejs-kubernetes
 - Deploying containerised applications
 - Container orchestrators
 - Creating a local Kubernetes cluster
 - Kubernetes resources
 - The application
 - Defining a Deployment
 - Defining a Service
 - Defining the database tier
 - Deploying the application
 - Recap and next steps
 ```bash
cd /home/c2c/developers/my_repo/k8s_learnk8s/knote-js/03
minikube status
kubectl apply -f kube	
kubectl get pods --watch	
minikube service knote --url	
	kubectl autoscale deploy/knote --min=3 --max=5 --cpu-percent=50
	minikube dashboard
kubectl delete -f kube

# access pod
kubectl exec -it pod/mongo-869db887b5-chspj -- bash

# Truy cập Pod từ bên ngoài Cluster (Kiểm tra - Debug)
# run proxy
kubectl proxy
http://127.0.0.1:8001/api/v1/namespaces/default/pods/knote-d58c7bcb6-m8cm8/proxy/

# run minikube dashboard
minikube dashboard
 ```
