<!-- loiocf15900ca39242fb87a1fb081a54b9ca -->

# OAuth Client Credentials Authentication

The Transparent Proxy handles the HTTP communication protocol for both Internet and on-premise destinations protected with the *OAuth Client Credentials* flow.



<a name="loiocf15900ca39242fb87a1fb081a54b9ca__section_tfr_bwv_hcc"/>

## Prerequisites

To integrate this functionality, you must create an SAP BTP destination. This destination should have `Type` "HTTP" and `Authentication` "OAuth2ClientCredentials", for example:

**OAuth 2 Client Credentials Destination**

> ### Sample Code:  
> ```
> {
>     "Name": "example-dest-oauth-2-client-credentials",
>     "Type": "HTTP",
>     "ProxyType": "Internet",
>     "URL": <application-url>,
>     "Authentication": "OAuth2ClientCredentials"
>     "tokenServiceURLType": "Common",
>     "clientId": <client-id>,
>     "clientSecret": <client-secret>,
>     "tokenServiceURL": <token-service-url>
> }
> ```

To target the destination with the name "example-dest-oauth-2-client-credentials" for handling by the Transparent Proxy, you should create a [Destination Custom Resource](destination-custom-resource-fc7951e.md) in a namespace of your choice.

**Destination CR for an OAuth 2 Client Credentials Destination**

> ### Sample Code:  
> ```
> apiVersion: destination.connectivity.api.sap/v1
> kind: Destination
> metadata:
>   name: <destination-cr-name>
> spec:
>   destinationRef:
>     name: "example-dest-oauth-2-client-credentials"
>   destinationServiceInstanceName: <dest-service-instance-name> // can be ommited if config.destinationService.defaultInstanceName is provided
> ```



<a name="loiocf15900ca39242fb87a1fb081a54b9ca__section_g4k_bwv_hcc"/>

## Consumption

For authentication type `OAuth2ClientCredentials`, no additional `Authorization` headers have to be provided to the Transparent Proxy as all necessary data for authorization is in the destination.

> ### Note:  
> `<destination-cr-namespace>` can be omitted if the destination custom resource is created in the same namespace as the application workload.

**OAuth 2 Client Credentials Pseudocode Snippet**

> ### Sample Code:  
> ```
> function callHttpsDestinationOAuth2ClientCredentials() {
>   url = '<destination-cr-name>.<destination-cr-namespace>'
>   headers = {
>             // X-Tenant-Subdomain is required only when Transparent Proxy is in shared tenant mode
>             'X-Tenant-Subdomain': '<tenant-where-destination-is-located>'
>             // Only when the tokenServiceURLType is 'Common'
>             'X-Token-Service-Tenant': '<tenant-to-retrieve-oauth-token>'
>   };
>      
>   response = performHttpGetRequest(url, headers)
>   print(response)
> }
> ```

**OAuth 2 Client Credentials Bash Snippet** 

> ### Sample Code:  
> ```
> # Call HTTP destination protected with OAuth 2 Client Credentials:
> curl <destination-cr-name>.<destination-cr-namespace> -H 'X-Tenant-Subdomain': '<tenant-where-destination-is-located>'
> ```

**Related Information**  


[OAuth Client Credentials Authentication](oauth-client-credentials-authentication-4e1d742.md "Create and configure an OAuth2ClientCredentials destination to consume OAuth-protected resources from an application.")

