<!-- loio897df9757cd842cfb1cb9fb6c0327911 -->

# SMTPS

Configure SMTPS destinations for the Transparent Proxy for Kubernetes.



<a name="loio897df9757cd842cfb1cb9fb6c0327911__section_olm_cln_sfc"/>

## Preparation

To integrate this functionality, you must create a BTP destination in a first step:

**Example: Internet SMTPS Destination with BasicAuthentication**

> ### Sample Code:  
> ```
> {
>         "Name": "example-dest-smtps",
>         "Type": "MAIL",
>         "Authentication": "BasicAuthentication",
>         "mail.user": <username>,
>         "mail.password": <password>,
>         "mail.transport.protocol": "smtps",
>         "mail.smtps.host": "smtp.gmail.com",
>         "mail.smtps.auth": "true",
>         "mail.smtps.port": "465",
>         "ProxyType": "Internet"
> }
> ```

**Example: Internet SMTPS Mail Destination with OAuth2ClientCredentials**

> ### Sample Code:  
> ```
> {
>         "Name": "example-dest-smtps",
>         "Type": "MAIL",
>         "Authentication": "OAuth2ClientCredentials",
>         "mail.user": <username>,
>         "mail.transport.protocol": "smtps",
>         "mail.smtps.host": "smtps",
>         "mail.smtps.auth": "true",
>         "mail.smtps.port": "465",
>         "ProxyType": "Internet", 
>         "tokenServiceURL": <token-service-url>,
>         "clientId": <client-id>,
>         "clientSecret": <client-secret>,
>         "tokenServiceURLType": "Dedicated"
> }
> ```

**Example: Internet SMTPS Mail Destination with OAuth2RefreshToken**

> ### Sample Code:  
> ```
> {
>         "Name": "example-dest-smtps",
>         "Type": "MAIL",
>         "Authentication": "OAuth2RefreshToken",
>         "mail.user": <username>,
>         "mail.transport.protocol": "smtps",
>         "mail.smtps.host": "smtps",
>         "mail.smtps.auth": "true",
>         "mail.smtps.port": "465",
>         "ProxyType": "Internet", 
>         "tokenServiceURL": <token-service-url>,
>         "clientId": <client-id>,
>         "clientSecret": <client-secret>,
>         "tokenServiceURLType": "Dedicated"
> }
> ```

**Example: Internet SMTPS Mail Destination with OAuth2AuthorizationCode**

> ### Sample Code:  
> ```
> {
>         "Name": "example-dest-smtps",
>         "Type": "MAIL",
>         "Authentication": "OAuth2AuthorizationCode",
>         "mail.user": <username>,
>         "mail.transport.protocol": "smtps",
>         "mail.smtps.host": "smtps",
>         "mail.smtps.auth": "true",
>         "mail.smtps.port": "465",
>         "ProxyType": "Internet", 
>         "tokenServiceURL": <token-service-url>,
>         "clientId": <client-id>,
>         "clientSecret": <client-secret>,
>         "tokenServiceURLType": "Dedicated"
> }
> ```

To target the destination with the name "example-dest-smtps" for handling by the Transparent Proxy, you should create a [Destination Custom Resource](destination-custom-resource-fc7951e.md) \(CR\) in a namespace of your choice.

**Example: Destination CR for an SMTPS Destination**

> ### Sample Code:  
> ```
> apiVersion: destination.connectivity.api.sap/v1
> kind: Destination
> metadata:
>   name: <destination-cr-name>
> spec:
>   destinationRef:
>     name: "example-dest-smtps"
>   destinationServiceInstanceName: <dest-service-instance-name> // can be ommited if config.destinationService.defaultInstanceName is provided
> ```

The Transparent Proxy will create a [Kubernetes Service](https://kubernetes.io/docs/concepts/services-networking/service/) for that destination on port 465, the default SMTPS port \(unless another port is specified in the destination CR\). The Transparent proxy handles basic authentication with the mail server using the credentials from the respective destination.

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
>     name: "example-dest-smtps"
>   destinationServiceInstanceName: <dest-service-instance-name> // can be ommited if config.destinationService.defaultInstanceName is provided
> ```

The Transparent Proxy will create a [Kubernetes Service](https://kubernetes.io/docs/concepts/services-networking/service/) for each tenant described in the `transparent-proxy.connectivity.api.sap/tenant-subdomains` annotation. The names of the Kubernetes services will follow this format: `<destination-cr-name>-<tenant-subdomain>`.



<a name="loio897df9757cd842cfb1cb9fb6c0327911__section_ibf_cln_sfc"/>

## Consumption

Once done, the application can start consuming the destination from within the Kubernetes cluster:

> ### Note:  
> `<destination-cr-namespace>` can be omitted if the destination custom resource is created in the same namespace as the application workload.

> ### Note:  
> In the following code snippets, a single dot on a line by itself indicates the end-of-data marker in SMTPS. This notifies the server that the message body is complete.

**SMTPS Consumption - Bash Snippet** 

> ### Sample Code:  
> ```
> telnet <destination-cr-name>.<destination-cr-namespace> 465
>    
> MAIL FROM:sender@transparentproxy.com
>     
> RCPT TO:receiver@transparentproxy.com
>     
> DATA
>     
> Some test data.
>   
> .
> ```

**SMTPS Consumption for Authentication Types OAuth2RefreshToken/OAuth2AuthorizationCode - Bash Snippet** 

> ### Sample Code:  
> ```
> telnet <destination-cr-name>.<destination-cr-namespace> 465
>  
> // Token Format: "user=<username>\x01auth=Bearer <access_token>\x01\x01" where access_token is the refresh token for OAuth2RefreshToken or the authorization code for OAuth2AuthorizationCode and username is your mail user
> AUTH XOAUTH2 <base64-encoded-token>
>  
> MAIL FROM:sender@transparentproxy.com
>     
> RCPT TO:receiver@transparentproxy.com
>     
> DATA
>     
> Some test data.
>   
> .
> ```

**SMTPS Consumption in *Shared* \(Multitenant\) Mode - Bash Snippet**

> ### Sample Code:  
> ```
> telnet <destination-cr-name>-<tenant-subdomain>.<destination-cr-namespace> 465
>    
> MAIL FROM:sender@transparentproxy.com
>     
> RCPT TO:receiver@transparentproxy.com
>     
> DATA
>     
> Some test data.
>   
> .
> ```

**SMTPS Consumption for Authentication Types OAuth2RefreshToken/OAuth2AuthorizationCode - Bash Snippet** 

> ### Sample Code:  
> ```
> telnet <destination-cr-name>-<tenant-subdomain>.<destination-cr-namespace> 465
>    
> // Token Format: "user=<username>\x01auth=Bearer <access_token>\x01\x01" where access_token is the refresh token for OAuth2RefreshToken or the authorization code for OAuth2AuthorizationCode and username is your mail user
> AUTH XOAUTH2 <base64-encoded-token>
>  
> MAIL FROM:sender@transparentproxy.com
>     
> RCPT TO:receiver@transparentproxy.com
>     
> DATA
>     
> Some test data.
>   
> .
> ```

