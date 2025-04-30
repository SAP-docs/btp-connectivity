<!-- loio05d70a1fde804ff88dcf8a2f6f4bcfae -->

# OAuth User Token Exchange Authentication

The Transparent Proxy handles the HTTP communication protocol for both Internet and on-premise destinations protected with the *OAuth User Token Exchange* flow.



<a name="loio05d70a1fde804ff88dcf8a2f6f4bcfae__section_tfr_bwv_hcc"/>

## Prerequisites

To integrate this functionality, you must create an SAP BTP destination. This destination should have `Type` "HTTP" and `Authentication` "OAuth2UserTokenExchange", for example:

**OAuth 2 User Token Exchange Destination**

> ### Sample Code:  
> ```
> {
>     "Name": "example-dest-oauth-2-user-token-exchange",
>     "Type": "HTTP",
>     "ProxyType": "Internet",
>     "URL": <application-url>,
>     "Authentication": "OAuth2UserTokenExchange",
>     "tokenServiceURLType": "Common",
>     "clientId": <client-id>,
>     "clientSecret": <client-secret>,
>     "tokenServiceURL": <token-service-URL>
> }
> ```

To target the destination with the name "example-dest-user-oauth-2-token-exchange" for handling by the Transparent Proxy, you should create a [Destination Custom Resource](destination-custom-resource-fc7951e.md) in a namespace of your choice.

**Destination CR for an OAuth 2 User Token Exchange Destination**

> ### Sample Code:  
> ```
> apiVersion: destination.connectivity.api.sap/v1
> kind: Destination
> metadata:
>   name: <destination-cr-name>
> spec:
>   destinationRef:
>     name: "example-dest-oauth-2-user-token-exchange"
>   destinationServiceInstanceName: <dest-service-instance-name> // can be ommited if config.destinationService.defaultInstanceName is provided
> ```



<a name="loio05d70a1fde804ff88dcf8a2f6f4bcfae__section_g4k_bwv_hcc"/>

## Consumption

For authentication type `OAuth2UserTokenExchange`, the cloud user identity has to be passed to the Transparent Proxy as a token represented by a JSON Web token \(JWT\) via `Authorization` header of scheme `Bearer`.

> ### Note:  
> `<destination-cr-namespace>` can be omitted if the destination custom resource is created in the same namespace as the application workload.

**OAuth 2 User Token Exchange Pseudocode Snippet**

> ### Sample Code:  
> ```
> function callOAuth2TokenExchangeHttpsDestination() {
>     accessToken = getPasswordAccessToken()
>     url = '<destination-cr-name>.<destination-cr-namespace>'
>     headers: {
>             // X-Tenant-Subdomain is required only when Transparent Proxy is in shared tenant mode
>             'X-Tenant-Subdomain': '<tenant-where-destination-is-located>',
>             'Authorization': 'Bearer ' + accessToken,
>     }
>  
>     response = performHttpGetRequest(url, headers)
>     print(response)
> }
>  
> function getPasswordAccessToken() {
>     url = '<tenant-for-retrieving-password-token>.authentication.ap10.hana.ondemand.com/oauth/token?grant_type=password&response_type=token'
>     headers = {
>                 'Content-Type': 'application/x-www-form-urlencoded',
>                 'Authorization': 'Basic <auth>',
>     }
>  
>     postData = {
>             'username': '<username>',
>             'password': '<password>',
>     }
>      
>     response = performHttpPostRequest(url, headers, postData)
>      
>     try {
>         passwordAccessToken = parseJSON(response.body)['access_token']
>         return passwordAccessToken
>     } catch (err) {
>         return fail('Cannot parse password access token: ' + err)
>     }
> }
> ```

**OAuth 2 User Token Exchange Bash Snippet** 

> ### Sample Code:  
> ```
> # 1. Get password access token (the 'access_token' value from the response body):
> curl -X POST \
>   -H "Content-Type: application/x-www-form-urlencoded" \
>   -H "Authorization: Basic <auth>" \
>   -d "username=<username>&password=<password>" \
>   '<tenant-for-retrieving-password-token>.authentication.ap10.hana.ondemand.com/oauth/token?grant_type=password&response_type=token'
>   
> # 2. Call HTTP destination protected with OAuth 2 User Token Exchange:
> curl \
>   -H "X-Tenant-Subdomain: <tenant-where-destination-is-located>" \
>   -H "Authorization: Bearer <password-access-token>" \
>   '<destination-cr-name>.<destination-cr-namespace>'
> ```

**Related Information**  


[OAuth User Token Exchange Authentication](oauth-user-token-exchange-authentication-e3c333f.md "Learn about the OAuth2UserTokenExchange authentication type for HTTP destinations: use cases, supported properties and ways to retrieve an access token in an automated way.")

