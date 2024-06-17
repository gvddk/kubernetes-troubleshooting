### Installation approaches for kubernetes 

minikube

k3s


kind
```
brew install kind
To create cluster: kind create cluster
This will take few minuts
kubectl get pods -A

kind version

Creating multiple kubernetes clusters:
kind create cluster --name <your cluster name>
Deleting kind cluster:
kind delete cluster --name <your cluster name>
```

docker-desktop

Microk8s



| Utility Name   |          Installation instructions          |                          Comments |
|----------------|:-------------------------------------------:|----------------------------------:|
| minikube       |            brew install minikube            |                                 - |
| k3s            |              brew install k3s               | Light weight k8s Operating system |
| kind           |              brew install kind              |                                $1 |
| Docker Desktop | Click on settings, enable docker kubernetes |                                $1 |




References:

- kind : https://medium.com/@martin.hodges/using-kind-to-develop-and-test-your-kubernetes-deployments-54093692c9fa
- 
