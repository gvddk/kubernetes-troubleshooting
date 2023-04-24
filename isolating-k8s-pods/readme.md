# How to isolate k8s pods from service?

## Reference Link
https://medium.com/@danielepolencic/isolating-kubernetes-pods-for-debugging-5fe41e630e9

## Info
By changing the labels, you can detach pods from the service(no traffic) and you troubleshoot them live.

A Service routes the traffic to your Pods using the selector app=hello.

First, the Service stops routing traffic to the Pod because the Service’s selector doesn’t match the label.


### Troubleshooting steps

```
kubectl label pod <pod-name> app=debug --overwrite
```




