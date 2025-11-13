<!-- loioa728ae0850594b0d828cb4e426ac518e -->

# OAuth JWT Bearer Authentication

The Transparent Proxy handles the HTTP communication protocol for both Internet and on-premise destinations protected with the *OAuth JWT Bearer* flow.



<a name="loioa728ae0850594b0d828cb4e426ac518e__section_tfr_bwv_hcc"/>

## Prerequisites

To integrate this functionality, you must create an SAP BTP destination. This destination should have `Type` "HTTP" and `Authentication` "OAuth2JWTBearer", for example:

**OAuth 2 JWT Bearer Destination**

> ### Sample Code:  
> ```
> {
>     "Name": "example-dest-oauth-2-jwt-bearer",
>     "Type": "HTTP",
>     "ProxyType": "Internet",
>     "URL": <application-url>,
>     "Authentication": "OAuth2JWTBearer",
>     "tokenServiceURLType": "Common",
>     "clientId": <client-id>,
>     "clientSecret": <client-secret>,
>     "tokenServiceURL": <token-service-URL>
> }
> ```

To target the destination with the name "example-dest-oauth-2-jwt-bearer" for handling by the Transparent Proxy, you should create a [Destination Custom Resource](destination-custom-resource-fc7951e.md) in a namespace of your choice.

**Destination CR for an OAuth 2 JWT Bearer Destination**

> ### Sample Code:  
> ```
> apiVersion: destination.connectivity.api.sap/v1
> kind: Destination
> metadata:
>   name: <destination-cr-name>
> spec:
>   destinationRef:
>     name: "example-dest-oauth-2-jwt-bearer"
>   destinationServiceInstanceName: <dest-service-instance-name> // can be ommited if config.destinationService.defaultInstanceName is provided
> ```



<a name="loioa728ae0850594b0d828cb4e426ac518e__section_g4k_bwv_hcc"/>

## Consumption

For authentication type `OAuth2JWTBearer`, the cloud user identity has to be passed to the Transparent Proxy as a token represented by a JSON Web token \(JWT\) via `Authorization` header of scheme `Bearer`. Then, the token will be passed as an ‘X-User-Token’ to the Destination service, which then will return `authTokens`, processed by the Transparent Proxy and attached to the HTTP request as an `Authorization` header.

> ### Note:  
> `<destination-cr-namespace>` can be omitted if the destination custom resource is created in the same namespace as the application workload.

> ### Caution:  
> The `X-Token-Service-Tenant` header represents the subdomain of the tenant on behalf of which to fetch an access token using the configured credentials. When `tokenServiceURLType` in the BTP Destination is `Common`, this header can be used to specify the tenant if the `X-User-Token` does not contain tenant information. The header value will be used to replace the tenant placeholder in the URL or added as a subdomain if no placeholder exists. When `tokenServiceURLType` is `Dedicated`, this header is forbidden and an error will be returned if provided.
> 
> -   If `X-Token-Service-Tenant` is not provided but `X-User-Token` contains tenant information, the tenant information will be automatically extracted from the JWT \(JSON web token\).
> -   If neither the header nor tenant information in the JWT is available, an error will be returned.

**OAuth 2 JWT Bearer Pseudocode Snippet**

> ### Sample Code:  
> ```
> function callHttpsDestinationOAuth2JWTBearer() {
>     accessToken = getPasswordAccessToken()
>  
>     url = '<destination-cr-name>.<destination-cr-namespace>'
>     headers: {
>             // X-Tenant-Subdomain is required only when transparent proxy is in shared tenant mode
>             'X-Tenant-Subdomain': '<tenant-where-destination-is-located>',
>             // Only when the tokenServiceURLType in the BTP destination is 'Common'
>             'X-Token-Service-Tenant': '<tenant-to-retrieve-oauth-token>',
>             'Authorization': 'Bearer ' + accessToken,
>         }
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
>             }
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
>         return fail('Cannot parse password refresh token: ' + err)
>     }
> }
> ```

**OAuth 2 JWT Bearer Bash Snippet** 

> ### Sample Code:  
> ```
> # 1. Retrieve the user identity, which is the password access token (the 'access_token' value from the response body):
> curl -X POST \
>   -H "Content-Type: application/x-www-form-urlencoded" \
>   -H "Authorization: Basic <auth>" \
>   -d "username=<username>&password=<password>" \
>   '<tenant-for-retrieving-password-token>.authentication.ap10.hana.ondemand.com/oauth/token?grant_type=password&response_type=token'
>    
> # 2. Call HTTP destination protected with OAuth 2 JWT Bearer using the password access token retrieved in step 1:
> curl \
>   -H "X-Tenant-Subdomain: <tenant-where-destination-is-located>" \
>   -H "Authorization: Bearer <password-access-token>" \
>   '<destination-cr-name>.<destination-cr-namespace>'
> ```

**Related Information**  


[OAuth JWT Bearer Authentication](oauth-jwt-bearer-authentication-283cd2d.md "Learn about the OAuth JWT bearer authentication type for HTTP destinations: use cases, supported properties and examples.")

