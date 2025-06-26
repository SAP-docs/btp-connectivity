<!-- loio76db66c32d5445ce9c705ea9774c5354 -->

# POP3S

Configure POP3S destinations for the Transparent Proxy for Kubernetes.



<a name="loio76db66c32d5445ce9c705ea9774c5354__section_olm_cln_sfc"/>

## Preparation

To integrate this functionality, you must create a BTP destination in a first step.

**Example: Internet POP3S Destination with BasicAuthentication** 

> ### Sample Code:  
> ```
> {
>         "Name": "example-dest-pop3s",
>         "Type": "MAIL",
>         "Authentication": "BasicAuthentication",
>         "mail.user": <username>,
>         "mail.password": <password>,
>         "mail.transport.protocol": "pop3s",
>         "mail.pop3s.host": "pop.gmail.com",
>         "mail.pop3s.auth": "true",
>         "mail.pop3s.port": "995",
>         "ProxyType": "Internet"
> }
> ```

**Example: Internet POP3S Mail Destination with OAuth2ClientCredentials**

> ### Sample Code:  
> ```
> {
>         "Name": "example-dest-pop3s",
>         "Type": "MAIL",
>         "Authentication": "OAuth2ClientCredentials",
>         "mail.user": <username>,
>         "mail.password": <password>,
>         "mail.transport.protocol": "pop3s",
>         "mail.pop3s.host": "pop3s",
>         "mail.pop3s.auth": "true",
>         "mail.pop3s.port": "995",
>         "ProxyType": "Internet",
>         "tokenServiceURL": <token-service-url>,
>         "clientId": <client-id>,
>         "clientSecret": <client-secret>,
>         "tokenServiceURLType": "Dedicated"
> }
> ```

To target the destination with the name "example-dest-pop3s" for handling by the Transparent Proxy, you should create a [Destination Custom Resource](destination-custom-resource-fc7951e.md) \(CR\) in a namespace of your choice.

**Example: Destination CR for a POP3S Destination**

> ### Sample Code:  
> ```
> apiVersion: destination.connectivity.api.sap/v1
> kind: Destination
> metadata:
>   name: <destination-cr-name>
> spec:
>   destinationRef:
>     name: "example-dest-pop3s"
>   destinationServiceInstanceName: <dest-service-instance-name> // can be ommited if config.destinationService.defaultInstanceName is provided
> ```

The Transparent Proxy will create a [Kubernetes Service](https://kubernetes.io/docs/concepts/services-networking/service/) for that destination on port 995, the default POP3S port \(unless another port is specified in the destination CR\). The Transparent proxy handles basic authentication with the mail server using the credentials from the respective destination.

**Multitenant Usage**

The Transparent Proxy supports multitenancy for MAIL destinations. To consume a target system in a multitenant manner, describe all tenants in the `transparent-proxy.connectivity.api.sap/tenant-subdomains` annotation:

**Example: Destination CR for a MAIL Destination in Transparent Proxy *Shared* Mode** 

> ### Sample Code:  
> ```
> apiVersion: destination.connectivity.api.sap/v1
> kind: Destination
> metadata:
>   name: <destination-cr-name>
>   annotations:
>     transparent-proxy.connectivity.api.sap/tenant-subdomains: '["tenant-subdomain", "another-tenant-subdomain"]'
>   destinationRef:
>     name: "example-dest-pop3s"
>   destinationServiceInstanceName: <dest-service-instance-name> // can be ommited if config.destinationService.defaultInstanceName is provided
> ```

The Transparent Proxy will create a [Kubernetes Service](https://kubernetes.io/docs/concepts/services-networking/service/) for each tenant described in the `transparent-proxy.connectivity.api.sap/tenant-subdomains` annotation. The names of the Kubernetes services will follow this format: `<destination-cr-name>-<tenant-subdomain>`.



<a name="loio76db66c32d5445ce9c705ea9774c5354__section_ibf_cln_sfc"/>

## Consumption

Once done, the application can start consuming the destination from within the Kubernetes cluster:

> ### Note:  
> `<destination-cr-namespace>` can be omitted if the destination custom resource is created in the same namespace as the application workload.

**POP3S Consumption - Bash Snippet**

> ### Sample Code:  
> ```
> telnet <destination-cr-name>.<destination-cr-namespace> 995
>      
> list
>     
> retr 1
>     
> retr 2
>     
> quit
> ```

**POP3S Consumption in *Shared* \(Multitenant\) Mode - Bash Snippet** 

> ### Sample Code:  
> ```
> telnet <destination-cr-name>-<tenant-subdomain>.<destination-cr-namespace> 995
>      
> list
>     
> retr 1
>     
> retr 2
>     
> quit
> ```

