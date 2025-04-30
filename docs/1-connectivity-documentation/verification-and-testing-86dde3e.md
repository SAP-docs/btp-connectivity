<!-- loio86dde3ed292443c3adfb0e19c2a12c8d -->

# Verification and Testing

Check the Transparent Proxy for Kubernetes after installation.

 Once you have installed the Transparent Proxy in your cluster, you can perform the following steps to verify it is running successfully.

> ### Note:  
> You may have to wait for a few seconds before all the components are started and can be consumed.

To check the status of the Transparent Proxy's components, execute the following, replacing the namespace placeholder:

```
kubectl run perform-hc --image=radial/busyboxplus:curl -it --rm --restart=Never -- curl -w "\n" 'sap-transp-proxy-int-healthcheck.{installation-namespace}/status'
```

or the following commands when your transaparent proxy is started within *Istio Service Mesh*:

```
kubectl run perform-hc --image=radial/busyboxplus:curl --labels="sidecar.istio.io/inject=true" -it --rm
curl -w '\n' sap-transp-proxy-int-healthcheck.{installation-namespace}/status
exit
```

and observe the result.

**Example:**

```
{
    "Status": "ok", // possible values: "ok|warning|critical"
    "Components": {
        "sap-transp-proxy-http": {
            "Status": "ok", // possible values: "ok|warning|critical"
            "Message":  "" // optional if status is not ok.
        },
        "sap-transp-proxy-tcp": {
            "Status": "ok", // possible values: "ok|warning|critical"            
            "Message":  "", // optional if status is not ok.
            "AffectedDeployments": []// optional if status is not ok. Lists all sap-transp-proxy-tcp deployments that have unready pods.
        },  
        "sap-transp-proxy-manager": {  "Status": "ok", // possible values: "ok|warning|critical"
            "Message":  "" // optional if status is not ok.
        }
    }
}
```

To check if all destination custom resources are configured properly, execute:

```
kubectl run perform-hc --image=curlimages/curl -it --rm --restart=Never -- curl -w "\n" 'sap-transp-proxy-int-healthcheck.{installation-namespace}/destinationCRs'
```

and observe the result.

**Example:**

```
{
    "Status": "ok",
    "CustomResources": [{
        "Name": "httpexample",
        "DestinationRef":  {
            "name" : "httpdestination"
        },
        "CreationTimestamp": "2022-08-26T11:05:30Z",
        "Available": "True",
        "Message": "Technical connectivity is configured. Kubernetes service with name httpexample is created.",
        "Reason": "ConfigurationSuccessful"
    }, {
        "Name": "tcpexample",  
        "DestinationRef":  {
            "name" : "tcpdestination"
        },  
        "CreationTimestamp": "2022-08-26T11:05:34Z",
        "Available": "True",
        "Message": "Technical connectivity is configured. Kubernetes service with name tcpexample is created.",
        "Reason": "ConfigurationSuccessful"  
    }]
}
```

If you encounter problems with any of the above steps, see [Troubleshooting](troubleshooting-fce292a.md) and [Recommended Actions](recommended-actions-20b1a62.md) for further investigation.

Now you can proceed with consuming the Transparent Proxy from your Kubernetes applications.

 