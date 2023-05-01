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
