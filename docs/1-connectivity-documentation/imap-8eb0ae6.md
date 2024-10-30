<!-- loio8eb0ae6c8258441181fbae1d73d7a9fa -->

# IMAP

Configure IMAP destinations for the transparent proxy for Kubernetes.



<a name="loio8eb0ae6c8258441181fbae1d73d7a9fa__section_tfr_bwv_hcc"/>

## Prerequisites

To integrate this functionality, you must:

-   Fulfill the on-premise/private cloud connectivity prerequisites
-   Create an SAP BTP Destination

This destination should have `Type` "MAIL" and `ProxyType` "OnPremise", for example:

**IMAP Destination**

> ### Sample Code:  
> ```
> {
>         "Name": "example-dest-imap",
>         "Type": "MAIL",
>         "mail.user": <username>,
>         "mail.password": <password>,
>         "mail.transport.protocol": "imap4",
>         "mail.imap4.host": "imap4",
>         "mail.imap4.auth": "true",
>         "mail.imap4.port": "464",
>         "ProxyType": "OnPremise"
> }
> ```

To target the destination with the name "example-dest-imap" for handling by the transparent proxy, you should create a [Destination Custom Resource](destination-custom-resource-fc7951e.md) in a namespace of your choice.

**Destination CR for an IMAP Destination**

> ### Sample Code:  
> ```
> apiVersion: destination.connectivity.api.sap/v1
> kind: Destination
> metadata:
>   name: <destination-cr-name>
> spec: 
>   destinationRef:
>     name: "example-dest-imap"
>   destinationServiceInstanceName: <dest-service-instance-name> // can be ommited if config.destinationService.defaultInstanceName is provided
> ```

The transparent proxy will create a [Kubernetes Service](https://kubernetes.io/docs/concepts/services-networking/service/) for that destination on port 143, the default IMAP port \(unless another port is specified in the destination CR\). The transparent proxy handles the basic authentication with the mail server using the credentials from the respective destination.

**Multitenant Usage** 

The transparent proxy supports multitenancy for `MAIL` destinations. To consume a target system in a multitenant manner, describe all tenants in the *transparent-proxy.connectivity.api.sap/tenant-subdomains* annotation:

**Destination CR for a MAIL destination in transparent proxy *shared* mode** 

> ### Sample Code:  
> ```
> apiVersion: destination.connectivity.api.sap/v1
> kind: Destination
> metadata:
>   name: <destination-cr-name>
>   annotations:
>     transparent-proxy.connectivity.api.sap/tenant-subdomains: '["tenant-subdomain", "another-tenant-subdomain"]'
>   destinationRef:
>     name: "example-dest-imap"
>   destinationServiceInstanceName: <dest-service-instance-name> // can be ommited if config.destinationService.defaultInstanceName is provided
> ```

The transparent proxy will create a Kubernetes service for each tenant described in the *transparent-proxy.connectivity.api.sap/tenant-subdomains* annotation. The names of the Kubernetes services will follow this format: <destination-cr-name\>-<tenant-subdomain\>.



<a name="loio8eb0ae6c8258441181fbae1d73d7a9fa__section_g4k_bwv_hcc"/>

## Consumption

Once done, the application can start consuming the destination from within the Kubernetes cluster.

> ### Note:  
> `<destination-cr-namespace>` can be omitted if the destination custom resource is created in the same namespace as the application workload.

**IMAP Consumption Bash Snippet**

> ### Sample Code:  
> ```
> telnet <destination-cr-name>.<destination-cr-namespace> 143
>   
> 2 LIST "" "*"
>   
> 3 SELECT INBOX
>   
> 5 FETCH 1 BODY[TEXT]
> ```

**IMAP Consumption in *Shared* \(Multitenant\) Mode Bash Snippet**

> ### Sample Code:  
> ```
> telnet <destination-cr-name>-<tenant-subdomain>.<destination-cr-namespace> 143
>   
> 2 LIST "" "*"
>   
> 3 SELECT INBOX
>   
> 5 FETCH 1 BODY[TEXT]
> ```

