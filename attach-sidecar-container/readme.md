# INFO
kubectl debug now gives the ability to load an ephemeral container into your pod.

This is an enormous win for developer experience as many of us will have had to include tools for diagnosing pod issues ( conntrack, netstat, vi and dig all spring to mind) into the container image.

## References
https://alexsimonjones.medium.com/kubectl-debug-time-to-say-goodbye-to-baking-diagnostic-tools-into-your-containers-47f6802d982b

https://pradiptabanerjee.medium.com/different-ways-to-debug-your-kubernetes-apps-57732e3ea534

### Rise of the ephemeral container:

An ephemeral container is a type of container that
you can run from inside an existing pod. It is the
feature underpinning the new capabilities released
with kubectl debug.

```
$ kubectl debug --image=quay.io/bpradipt/perf-amd64 -it --share-processes=true <PODName> -- /bin/bash
Defaulting debug container name to debugger-mxtpf.
If you don't see a command prompt, try pressing enter.
bash-5.1# 
```



