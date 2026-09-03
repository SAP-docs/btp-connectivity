<!-- loiobcbcd9f682bf4ff58c8cc4e5412abf23 -->

# Local Development

Find a local development guide for the Transparent Proxy for Kubernetes.



<a name="loiobcbcd9f682bf4ff58c8cc4e5412abf23__section_mky_zmc_3cc"/>

## Prerequisites

Before you begin, ensure the following prerequisites are set up:

1.  *kubectl* \(or an equivalent client\) installed on your machine to communicate with the Kubernetes cluster's control plane.
2.  One or more Destination service instances that the Transparent Proxy can work with.
3.  An SAP BTP destination created within one of the above Destination service instances, which references the end system.
4.  A destination custom resource created for that destination.

> ### Note:  
> Transparent proxy will create a [Kubernetes Service](https://kubernetes.io/docs/concepts/services-networking/service/) for every destination custom resource which it processes. Each service is an entry point to its corresponding destination.



<a name="loiobcbcd9f682bf4ff58c8cc4e5412abf23__section_sss_zmc_3cc"/>

## Guide

This guide outlines the steps to set up port forwarding and use a Transparent Proxy service from your local environment. Follow the steps below to list the services, forward ports, and consume services.

1.  Find the Kubernetes Service that match your destination custom resource name and namespace.

    Search by labels containing destination custom resource attributes\(e.g. name=example-dest, namespace=client-namespace, tp-namespace=sap-transp-proxy-system\):

    > ### Sample Code:  
    > ```
    > kubectl get svc -n <tp-namespace> -l transparent-proxy.connectivity.api.sap/parent-destination-cr-name=<name>,transparent-proxy.connectivity.api.sap/parent-destination-cr-namespace=<namespace> -o yaml
    > ```

    > ### Sample Code:  
    > ```
    > apiVersion: v1
    > kind: Service
    > metadata:
    >   creationTimestamp: "2025-11-22T21:44:48Z"
    >   labels:
    >     transparent-proxy.connectivity.api.sap/parent-destination-cr-name: example-dest
    >     transparent-proxy.connectivity.api.sap/parent-destination-cr-namespace: client-namespace
    >   name: example-dest-d3q12
    >   namespace: sap-transp-proxy-system
    > ...
    > 
    > ```

2.  [Port forward](https://kubernetes.io/docs/reference/kubectl/generated/kubectl_port-forward/) the selected service to your local machine. Replace \`<local-port\>\` with any available port number on your local machine \(for example, \`8042\`\), and \`<k8s-svc-port\>\` with the port number used by the Kubernetes service \(for example, \`80\`\).

    > ### Sample Code:  
    > ```
    > kubectl port-forward svc/<cluster-ip-service-name> <local-port>:<k8s-svc-port> -n <transparent-proxy-namespace>
    > ```

    For example, to port forward \`example-dest-no-auth-d3q12\` service to local port \`8042\`, execute:

    > ### Sample Code:  
    > ```
    > kubectl port-forward svc/example-dest-d3q12 8042:80 -n <transparent-proxy-namespace>
    > ```

3.  When making requests from your local environment, **include the `Host` header** with the `ClusterIP` service name.

    **Consumption Using curl**

    > ### Sample Code:  
    > ```
    > curl localhost:<local-port> -H "Host: <cluster-ip-service-name>"
    > ```

    **Consumption of `example-dest-no-auth` on Port 8042 Using curl** 

    > ### Sample Code:  
    > ```
    > curl localhost:8042 -H "Host: example-dest-d3q12"
    > ```

    > ### Caution:  
    > If you encounter an error response from the Transparent Proxy, refer to the [Error Response Headers](error-response-headers-2b3a572.md) page for detailed information and troubleshooting guidance.


