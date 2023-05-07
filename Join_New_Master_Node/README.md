# Joining a new master node into k8s cluster

Little bit more steps are required for master node.

1. we need to copy the cluster configuration file
   If you can not able to find that configuration file, you can generate that as below.

   kubectl get cm kubeadm-config -n kube-system -o yaml (in this command, copy the content of clusterConfiguration attribute)

2. Copy the control plane certificates to the latest node
3. Trigger join command with the token
   kubeadm join k8s-endpoint:6443 --token xxxxxxxx \
   --discovery-token-ca-cert-hash xxxxxxx \
   --control-plane --certificate-key xxxxxxxxx


if you notice above join command, it is having the options of k8s-endpoint and control-plane.