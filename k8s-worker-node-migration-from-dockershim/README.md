# How to perform migration of container runtime from dockershim to CRI in worker nodes of kubeadm cluster?

````
step 1:
Cordon and drain the worker node

kubectl cordon <workernode>
kubectl drain <workernode>

step 2:
once the node is drained, stop the kubelet service

systemctl stop kubelet

step 3:
Uninstall docker with commands

step 4:
Install containerd runtime

step 5:
Enable and start containerd service

step 6:
kubernetes communicated with container runtime through the CRI plugin. Be sure that this plugin is not disabled in your containerd installation.

step 7:
Edit kubelet configuration file /var/lib/kubelet/kubeadm-flags.env to add the following flags to KUBELET_KUBEADM_ARGS variable
--container-runtime=remote --container-runtime-endpoint=/run/containerd/containerd.sock

step 8:
sudo systemctl start kubelet

step 9:
kubectl describe node <node_name>

you should see container runtime version

step 10:
Uncordon the node
kubectl uncordon <node_name>
````
=======

# Q&A

About k8s 1.24 docker runtime changes:

````
Query - Where exactly we are using Docker inside of k8s cluster?

Answer: Kubernetes support for Docker via dockershim is now removed.Docker 
as an underlying runtime is being deprecated in favor of runtimes 
that use the Container Runtime Interface (CRI) created for Kubernetes.


Query - Do we need to change the creation of docker images with dockerfile?

Answer: Docker-produced images will continue to work in your 
cluster with all runtimes, as they always have.

Query - when the docker runtime was deprecated?

Answer: Kubernetes is deprecating Docker as a container runtime after v1.20.

Query - How docker build images work on different runtime?

Answer: The image that Docker produces isn’t really a Docker-specific 
image—it’s an OCI (Open Container Initiative) image. 
Any OCI-compliant image, regardless of the tool you use to build it, 
will look the same to Kubernetes.
Both containerd and CRI-O know how to pull those images and run them. 
This is why we have a standard for what containers should look like.
````
