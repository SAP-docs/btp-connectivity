<!-- loio8eb0ae6c8258441181fbae1d73d7a9fa -->

# IMAP

Consume an IMAP system through the Transparent Proxy for Kubernetes and the Destination service.



<a name="loio8eb0ae6c8258441181fbae1d73d7a9fa__section_tfr_bwv_hcc"/>

## Prerequisites

To integrate this functionality, you must:

-   For On-Premise/Private Cloud connectivity, fulfill the [prerequisites](using-the-transparent-proxy-c5257cf.md).
-   Create an SAP BTP Destination.

**Example: OnPremise IMAP Mail Destination with BasicAuthentication**

> ### Sample Code:  
> ```
> {
>         "Name": "example-dest-imap",
>         "Type": "MAIL",
>         "Authentication": "BasicAuthentication",
>         "mail.user": <username>,
>         "mail.password": <password>,
>         "mail.transport.protocol": "imap4",
>         "mail.imap4.host": "imap4",
>         "mail.imap4.auth": "true",
>         "mail.imap4.port": "143",
>         "ProxyType": "OnPremise"
> }
> ```

**Example: OnPremise IMAP Mail Destination with OAuth2ClientCredentials**

> ### Sample Code:  
> ```
> {
>         "Name": "example-dest-imap",
>         "Type": "MAIL",
>         "Authentication": "OAuth2ClientCredentials",
>         "mail.user": <username>,
>         "mail.transport.protocol": "imap4",
>         "mail.imap4.host": "imap4",
>         "mail.imap4.auth": "true",
>         "mail.imap4.port": "143",
>         "ProxyType": "OnPremise",
>         "tokenServiceURL": <token-service-url>,
>         "clientId": <client-id>,
>         "clientSecret": <client-secret>,
>         "tokenServiceURLType": "Dedicated"
> }
> ```

**Example: OnPremise IMAP Mail Destination with OAuth2RefreshToken**

> ### Sample Code:  
> ```
> {
>         "Name": "example-dest-imap",
>         "Type": "MAIL",
>         "Authentication": "OAuth2RefreshToken",
>         "mail.user": <username>,
>         "mail.transport.protocol": "imap4",
>         "mail.imap4.host": "imap4",
>         "mail.imap4.auth": "true",
>         "mail.imap4.port": "143",
>         "ProxyType": "OnPremise",
>         "tokenServiceURL": <token-service-url>,
>         "clientId": <client-id>,
>         "clientSecret": <client-secret>,
>         "tokenServiceURLType": "Dedicated"
> }
> ```

**Example: OnPremise IMAP Mail Destination with OAuth2AuthorizationCode**

> ### Sample Code:  
> ```
> {
>         "Name": "example-dest-imap",
>         "Type": "MAIL",
>         "Authentication": "OAuth2AuthorizationCode",
>         "mail.user": <username>,
>         "mail.transport.protocol": "imap4",
>         "mail.imap4.host": "imap4",
>         "mail.imap4.auth": "true",
>         "mail.imap4.port": "143",
>         "ProxyType": "OnPremise",
>         "tokenServiceURL": <token-service-url>,
>         "clientId": <client-id>,
>         "clientSecret": <client-secret>,
>         "tokenServiceURLType": "Dedicated"
> }
> ```

**Example: Internet IMAP Mail Destination with BasicAuthentication**

> ### Sample Code:  
> ```
> {
>         "Name": "example-dest-imap",
>         "Type": "MAIL",
>         "Authentication": "BasicAuthentication",
>         "mail.user": <username>,
>         "mail.password": <password>,
>         "mail.transport.protocol": "imap4",
>         "mail.imap4.host": "imap4",
>         "mail.imap4.auth": "true",
>         "mail.imap4.port": "143",
>         "ProxyType": "Internet"
> }
> ```

**Example: Internet IMAP Mail Destination with OAuth2ClientCredentials**

> ### Sample Code:  
> ```
> {
>         "Name": "example-dest-imap",
>         "Type": "MAIL",
>         "Authentication": "OAuth2ClientCredentials",
>         "mail.user": <username>,
>         "mail.transport.protocol": "imap4",
>         "mail.imap4.host": "imap4",
>         "mail.imap4.auth": "true",
>         "mail.imap4.port": "143",
>         "ProxyType": "Internet",
>         "tokenServiceURL": <token-service-url>,
>         "clientId": <client-id>,
>         "clientSecret": <client-secret>,
>         "tokenServiceURLType": "Dedicated"
> }
> ```

**Example: Internet IMAP Mail Destination with OAuth2RefreshToken**

> ### Sample Code:  
> ```
> {
>         "Name": "example-dest-imap",
>         "Type": "MAIL",
>         "Authentication": "OAuth2RefreshToken",
>         "mail.user": <username>,
>         "mail.transport.protocol": "imap4",
>         "mail.imap4.host": "imap4",
>         "mail.imap4.auth": "true",
>         "mail.imap4.port": "143",
>         "ProxyType": "Internet",
>         "tokenServiceURL": <token-service-url>,
>         "clientId": <client-id>,
>         "clientSecret": <client-secret>,
>         "tokenServiceURLType": "Dedicated"
> }
> ```

**Example: Internet IMAP Mail Destination with OAuth2AuthorizationCode**

> ### Sample Code:  
> ```
> {
>         "Name": "example-dest-imap",
>         "Type": "MAIL",
>         "Authentication": "OAuth2AuthorizationCode",
>         "mail.user": <username>,
>         "mail.transport.protocol": "imap4",
>         "mail.imap4.host": "imap4",
>         "mail.imap4.auth": "true",
>         "mail.imap4.port": "143",
>         "ProxyType": "Internet",
>         "tokenServiceURL": <token-service-url>,
>         "clientId": <client-id>,
>         "clientSecret": <client-secret>,
>         "tokenServiceURLType": "Dedicated"
> }
> ```

To target the destination with the name "example-dest-imap" for handling by the Transparent Proxy, you should create a [Destination Custom Resource](destination-custom-resource-fc7951e.md) in a namespace of your choice.

**Example: Destination CR for an IMAP Destination**

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

The Transparent Proxy will create a [Kubernetes Service](https://kubernetes.io/docs/concepts/services-networking/service/) for that destination on port 143, the default IMAP port \(unless another port is specified in the destination CR\). The Transparent Proxy handles the basic authentication with the mail server using the credentials from the respective destination.

**Multitenant Usage** 

The Transparent Proxy supports multitenancy for `MAIL` destinations. To consume a target system in a multitenant manner, describe all tenants in the *transparent-proxy.connectivity.api.sap/tenant-subdomains* annotation:

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
>     name: "example-dest-imap"
>   destinationServiceInstanceName: <dest-service-instance-name> // can be ommited if config.destinationService.defaultInstanceName is provided
> ```

The Transparent Proxy will create a Kubernetes service for each tenant described in the *transparent-proxy.connectivity.api.sap/tenant-subdomains* annotation. The names of the Kubernetes services will follow this format: <destination-cr-name\>-<tenant-subdomain\>.



<a name="loio8eb0ae6c8258441181fbae1d73d7a9fa__section_g4k_bwv_hcc"/>

## Consumption

Once done, the application can start consuming the destination from within the Kubernetes cluster.

> ### Note:  
> `<destination-cr-namespace>` can be omitted if the destination custom resource is created in the same namespace as the application workload.

**IMAP Consumption - Bash Snippet**

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

**IMAP Consumption for Authentication Types OAuth2RefreshToken/OAuth2AuthorizationCode - Bash Snippet**

> ### Sample Code:  
> ```
> telnet <destination-cr-name>.<destination-cr-namespace> 143
>  
> // Token Format: "user=<username>\x01auth=Bearer <access_token>\x01\x01" where access_token is the refresh token for OAuth2RefreshToken or the authorization code for OAuth2AuthorizationCode and username is your mail user
> 1 AUTHENTICATE XOAUTH2 <base64-encoded-token>
>   
> 2 LIST "" "*"
>   
> 3 SELECT INBOX
>   
> 5 FETCH 1 BODY[TEXT]
> ```

**IMAP Consumption in *Shared* \(Multitenant\) Mode - Bash Snippet**

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

**IMAP Consumption for Authentication Types OAuth2RefreshToken/OAuth2AuthorizationCode - Bash Snippet**

> ### Sample Code:  
> ```
> telnet <destination-cr-name>-<tenant-subdomain>.<destination-cr-namespace> 143
>  
> // Token Format: "user=<username>\x01auth=Bearer <access_token>\x01\x01" where access_token is the refresh token for OAuth2RefreshToken or the authorization code for OAuth2AuthorizationCode and username is your mail user
> 1 AUTHENTICATE XOAUTH2 <base64-encoded-token>
>  
> 2 LIST "" "*"
>   
> 3 SELECT INBOX
>   
> 5 FETCH 1 BODY[TEXT]
> ```

