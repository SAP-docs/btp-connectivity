<!-- loiobcbcd9f682bf4ff58c8cc4e5412abf23 -->

# Local Development

Find a local development guide for the transparent proxy for Kubernetes.



<a name="loiobcbcd9f682bf4ff58c8cc4e5412abf23__section_mky_zmc_3cc"/>

## Prerequisites

Before you begin, ensure the following prerequisites are set up:

1.  *kubectl* \(or an equivalent client\) installed on your machine to communicate with the Kubernetes cluster's control plane.
2.  One or more Destination service instances that the transparent proxy can work with.
3.  An SAP BTP destination created within one of the above Destination service instances, which references the end system.
4.  A destination custom resource created for that destination.

> ### Note:  
> Transparent proxy will create a [Kubernetes Service](https://kubernetes.io/docs/concepts/services-networking/service/) for every destination custom resource which it processes. Each service is an entry point to its corresponding destination.



<a name="loiobcbcd9f682bf4ff58c8cc4e5412abf23__section_sss_zmc_3cc"/>

## Guide

This guide outlines the steps to set up port forwarding and use a transparent proxy service from your local environment. Follow the steps below to list the services, forward ports, and consume services.

1.  List the Kubernetes services in the *sap-transp-proxy-system* namespace:

    > ### Sample Code:  
    > ```
    > kubectl get svc -n <transparent-proxy-namespace>
    > ```

2.  Get the name of the desired service from the result of the execution of the previous command:

    > ### Sample Code:  
    > ```
    > NAME                                        TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)    AGE
    > example-dest-no-auth                        ClusterIP   10.108.120.25    <none>        80/TCP     16h
    > sap-transp-proxy-healthcheck                ClusterIP   10.109.111.169   <none>        80/TCP     20h
    > sap-transp-proxy-int-healthcheck            ClusterIP   10.107.172.32    <none>        80/TCP     20h
    > sap-transp-proxy-manager                    ClusterIP   10.110.144.77    <none>        80/TCP     20h
    > ```

3.  Port forward the selected service to your local machine. Replace \`<local-port\>\` with any available port number on your local machine \(for example, \`8042\`\), and \`<k8s-svc-port\>\` with the port number used by the Kubernetes service \(for example, \`80\`\).

    > ### Sample Code:  
    > ```
    > kubectl port-forward svc/<destiation-cr-name> <local-port>:<k8s-svc-port> -n <transparent-proxy-namespace>
    > ```

    For example, to port forward \`example-dest-no-auth\` service to local port \`8042\`, execute:

    > ### Sample Code:  
    > ```
    > kubectl port-forward svc/example-dest-no-auth 8042:80 -n <transparent-proxy-namespace>
    > ```

4.  When consuming the service from your local environment, ensure that you rewrite the \`Host\` header with the destination custom resource name.

    **Consumption Using curl**

    > ### Sample Code:  
    > ```
    > curl localhost:<local-port> -H "Host: <destination-cr-name>"
    > ```

    **Consumption of `example-dest-no-auth` on Port 8042 Using curl** 

    > ### Sample Code:  
    > ```
    > curl localhost:8042  -H "Host: example-dest-no-auth"
    > ```

    > ### Caution:  
    > If you encounter an error response from the transparent proxy, refer to the [Error Response Headers](error-response-headers-2b3a572.md) page for detailed information and troubleshooting guidance.


