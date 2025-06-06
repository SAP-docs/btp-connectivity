<!-- loio89f18d6a23ca4e42a72228726a9c96e3 -->

# OAuth Password Authentication

The Transparent Proxy handles the HTTP communication protocol for both Internet and on-premise destinations protected with the *OAuth Password* flow.



<a name="loio89f18d6a23ca4e42a72228726a9c96e3__section_tfr_bwv_hcc"/>

## Prerequisites

To integrate this functionality, you must create an SAP BTP destination. This destination should have Type "HTTP" and Authentication "OAuth2Password", for example:

**OAuth 2 Password Destination**

> ### Sample Code:  
> ```
> {
>     "Name": "example-dest-oauth2-password",
>     "Type": "HTTP",
>     "ProxyType": "Internet",
>     "URL": <application-url>,
>     "Authentication": "OAuth2Password",
>     "clientId": <client-id>,
>     "clientSecret": <client-secret>,
>     "tokenServiceURL": <token-service-URL>,
>     "User": <user>,
>     "Password": <password>
> }
> ```

To target the destination with the name "example-dest-oauth-2-password" for handling by the Transparent Proxy, you should create a [Destination Custom Resource](destination-custom-resource-fc7951e.md) in a namespace of your choice

**Destination CR for an OAuth 2 Password Destination**

> ### Sample Code:  
> ```
> apiVersion: destination.connectivity.api.sap/v1
> kind: Destination
> metadata:
>   name: <destination-cr-name>
> spec:
>   destinationRef:
>     name: "example-dest-oauth-2-password"
>   destinationServiceInstanceName: <dest-service-instance-name> // can be ommited if config.destinationService.defaultInstanceName is provided
> ```



<a name="loio89f18d6a23ca4e42a72228726a9c96e3__section_g4k_bwv_hcc"/>

## Consumption

For authentication type `OAuth2Password`, no additional `Authorization` headers have to be provided to the Transparent Proxy as all necessary data for authorization is in the destination.

> ### Note:  
> `<destination-cr-namespace>` can be omitted if the destination custom resource is created in the same namespace as the application workload.

**OAuth 2 Password Pseudocode Snippet**

> ### Sample Code:  
> ```
> function callHttpsDestinationOAuth2Password() {
>   url = '<destination-cr-name>.<destination-cr-namespace>'
>   headers = {
>             // X-Tenant-Subdomain is required only when Transparent Proxy is in shared tenant mode
>             'X-Tenant-Subdomain': '<tenant-where-destination-is-located>'
>         }
>      
>   response = performHttpGetRequest(url, headers)
>   print(response)
> }
> ```

**OAuth 2 Password Bash Snippet** 

> ### Sample Code:  
> ```
> # Call HTTP destination protected with OAuth 2 Password:
> curl <destination-cr-name>.<destination-cr-namespace> -H 'X-Tenant-Subdomain': '<tenant-where-destination-is-located>'
> ```

**Related Information**  


[OAuth Password Authentication](oauth-password-authentication-452357c.md "Learn about the OAuth password authentication type for HTTP destinations: use cases, supported properties and examples.")

