<!-- loioceb84cb51ed64008b6aa7782c80c1651 -->

# IMAPS

Configure IMAPS destinations for the Transparent Proxy for Kubernetes.



<a name="loioceb84cb51ed64008b6aa7782c80c1651__section_olm_cln_sfc"/>

## Preparation

To integrate this functionality, you must create a BTP destination in a first step.

**Example: Internet IMAPS Destination with BasicAuthentication**

> ### Sample Code:  
> ```
> {
>         "Name": "example-dest-imaps",
>         "Type": "MAIL",
>         "Authentication": "BasicAuthentication",
>         "mail.user": <username>,
>         "mail.password": <password>,
>         "mail.transport.protocol": "imap4s",
>         "mail.imap4s.host": "imap.gmail.com",
>         "mail.imap4s.auth": "true",
>         "mail.imap4s.port": "993",
>         "ProxyType": "Internet"
> }
> ```

**Example: Internet IMAPS Mail Destination with OAuth2ClientCredentials**

> ### Sample Code:  
> ```
> {
>         "Name": "example-dest-imaps",
>         "Type": "MAIL",
>         "Authentication": "OAuth2ClientCredentials",
>         "mail.user": <username>,
>         "mail.transport.protocol": "imap4s",
>         "mail.imap4s.host": "imap4s",
>         "mail.imap4s.auth": "true",
>         "mail.imap4s.port": "993",
>         "ProxyType": "Internet",
>         "tokenServiceURL": <token-service-url>,
>         "clientId": <client-id>,
>         "clientSecret": <client-secret>,
>         "tokenServiceURLType": "Dedicated"
> }
> ```

To target the destination with the name "example-dest-imaps" for handling by the Transparent Proxy, you should create a [Destination Custom Resource](destination-custom-resource-fc7951e.md) \(CR\) in a namespace of your choice.

**Example: Destination CR for an IMAPS Destination**

> ### Sample Code:  
> ```
> apiVersion: destination.connectivity.api.sap/v1
> kind: Destination
> metadata:
>   name: <destination-cr-name>
> spec:
>   destinationRef:
>     name: "example-dest-imaps"
>   destinationServiceInstanceName: <dest-service-instance-name> // can be ommited if config.destinationService.defaultInstanceName is provided
> ```

The Transparent Proxy will create a [Kubernetes Service](https://kubernetes.io/docs/concepts/services-networking/service/) for that destination on port 993, the default IMAPS port \(unless another port is specified in the destination CR\). The Transparent proxy handles basic authentication with the mail server using the credentials from the respective destination.

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
>     name: "example-dest-imaps"
>   destinationServiceInstanceName: <dest-service-instance-name> // can be ommited if config.destinationService.defaultInstanceName is provided
> ```

The Transparent Proxy will create a [Kubernetes Service](https://kubernetes.io/docs/concepts/services-networking/service/) for each tenant described in the `transparent-proxy.connectivity.api.sap/tenant-subdomains` annotation. The names of the Kubernetes services will follow this format: `<destination-cr-name>-<tenant-subdomain>`.



<a name="loioceb84cb51ed64008b6aa7782c80c1651__section_ibf_cln_sfc"/>

## Consumption

Once done, the application can start consuming the destination from within the Kubernetes cluster:

> ### Note:  
> `<destination-cr-namespace>` can be omitted if the destination custom resource is created in the same namespace as the application workload.

**IMAPS Consumption - Bash Snippet** 

> ### Sample Code:  
> ```
> telnet <destination-cr-name>.<destination-cr-namespace> 993
>    
> 2 LIST "" "*"
>    
> 3 SELECT INBOX
>    
> 5 FETCH 1 BODY[TEXT]
> ```

**IMAPS Consumption in *Shared* \(Multitenant\) Mode - Bash Snippet** 

> ### Sample Code:  
> ```
> telnet <destination-cr-name>-<tenant-subdomain>.<destination-cr-namespace> 993
>    
> 2 LIST "" "*"
>    
> 3 SELECT INBOX
>    
> 5 FETCH 1 BODY[TEXT]
> ```

