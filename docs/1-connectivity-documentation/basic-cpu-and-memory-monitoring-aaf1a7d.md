<!-- loioaaf1a7db5d694436b978d5e71b52f1ac -->

# Basic CPU and Memory Monitoring

Perform CPU and memory monitoring for the transparent proxy for Kubernetes.

You can monitor the CPU and memory of the transparent proxy pods in the following way:

```
kubectl top pods -n <installation-namespace> -l 'transparent-proxy.connectivity.api.sap/component in (http,manager,tcp)'
```

> ### Note:  
> For more info about interacting with pods using kubectl, see [Interacting with running Pods](https://kubernetes.io/docs/reference/kubectl/quick-reference/#interacting-with-running-pods).

> ### Caution:  
> In case of error, always look for detailed error messages and hints in 'x-error-message', 'x-error-origin', 'x-proxy-server' and 'x-internal-error-code'. Also you could use 'x-request-id' as correlation id to find more about the error in the transparent proxy HTTP pods. See common issues and solutions.

