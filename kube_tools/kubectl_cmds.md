# Debugging commands with kubectl

## kubectl commands

```
---> when you are waiting for a buch of pods to start up, it can be annoying to have to keep typing kubectl get pods multiple times.

kubectl get pods --watch

----> Mastering kubectl

shell aliases

alias k=kubectl
alias kg="kubectl get"
alias kgdep="kubectl get deployment"
alias kd="kubectl describe"

-----> Showing more detailed output:
kubectl get pods
kubectl get pods -o wide
kubectl get nodes -o wide

kubectl config get-contexts
kubectl cluster-info
kubectl config use-context gke
kubectl config set-context mypp --cluster=gke --namespace=myapp(context myapp created)
kubectl config current-context

kubectl get all 
kubectl api-versions 
kubectl api-resources 

------> Getting help on kubernetes resources
kubectl explain pods

------> Working with jsondata and jq
```

### kubectl imperative commands
```
----> create a namespace
kubectl create namespace my-new-namespace

----> delete a namespace
kubectl delete ns my-new-namespace

---> Edit deployment
kubectl edit deploy my-deployment

---> Generating resource manifests
kubectl run demo --image=cloudnatived/demo:hello --dry-run -o yaml

The dry-run flag tells kubernetes not to actually create the resource

kubectl run demo --image=cloudnatived/demo:hello --dry-run -o yaml > deploy.yaml(save this output to a file)


----> Imperative vs Declarative model

----> Diffing resources
kubectl diff -f deployment.yaml

----> Working with container's logs

kubectl logs -n kube-system --tail=20 kube-dns-autoscaler-xxxx
kubectl logs -n kube-system --tail=20 kube-dns-autoscaler-xxxx -f

----> Forwarding a kubernetes port
kubectl port-forward demo-12345 9999:9988

----> Executing commands on containers
kubectl run alpine --image alpine --command -- sleep 999

---> Running containers for troubleshooting
kubectl run demo --image cloudnatived/demo:hello --expose --port 8888 (this will create service and deployment)

By using below command, we are verifying the DNS resolution of above pod

kubectl run nslookup --image=busybox:1.28 --rm -it --restart=never --command -- nslookup demo
kubectl run nslookup --image=busybox:1.28 --rm -it --restart=never --command -- wget -qO- http://demo:8888

-----> Using busybox commands

kubectl run busybox --image=busybox:1.28 --rm -it --restart=never /bin/sh

alias bb= kubectl run busybox --image=busybox:1.28 --rm -it --restart=never --command --

bb nslookup demo
bb wget http://demo:8888
bb sh


----> Installing programs on a container then use alpine or ubuntu image
```

