## How to get started with kubernetes.

**Follow the below steps for the setup:**

* **Install Docker, Hyper-V, VirtualMachine or similar platform** 
* **Install Minikube** [Install instructions](https://minikube.sigs.k8s.io/docs/start/)
* **From elevated shell, run: "minikube start"** [Driver setup(If there are errors)](https://minikube.sigs.k8s.io/docs/drivers/)
* **To check if everything is setup correctly, run: "minikube dashoard"**

**Once the setup is ready, use the below steps as needed:**

* List all deployments, services, pods etc: `kubectl get all`
* To use docker of kubernetes instead of the default docker: `eval $(minikube docker-env)`
* To check if pointing to correct docker: `docker images`
* To run standard image in k8s pod: `kubectl apply -f postgres.yaml`
* To expose the service:
```
minikube service postgres

or

kubectl port-forward service/postgres 5432:5432

or

minikube tunnel
kubectl get services balanced
```

**If a custom image is to be deployed:**

* First build a custom image with help of Dockerfile: `docker build -t microservice:1.0.0 .`
* To run the image built above in k8s pod: `kubectl apply -f microservice.yaml`

**Other important commands:**

* To log into the pod: `kubectl exec --stdin --tty pod/microservice-84984d4c5c-8l6mq -- /bin/sh`
* To get logs from the pod: `kubectl logs -f pod/microservice-84984d4c5c-8l6mq`
* To get minikube IP: `minikube ip`
* Increase the default memory limit (requires a restart): `minikube config set memory 4096`
* To delete deployment: `kubectl delete deployment microservice`
* To delete deployment: `kubectl delete service microservice`
* To delete all minikube clusters: `minikube delete --all`


