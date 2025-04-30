<!-- loioaaf1a7db5d694436b978d5e71b52f1ac -->

# Basic CPU and Memory Monitoring

Perform CPU and memory monitoring for the Transparent Proxy for Kubernetes.

You can monitor the CPU and memory of the Transparent Proxy pods in the following way:

```
kubectl top pods -l 'transparent-proxy.connectivity.api.sap/component in (http-proxy,tcp-proxy,manager)' -n <installation-namespace>
```

> ### Note:  
> For more info about interacting with pods using kubectl, see [Interacting with running Pods](https://kubernetes.io/docs/reference/kubectl/quick-reference/#interacting-with-running-pods).

