<!-- loio5ab1150a827b47ec8ed4ab1f3f40d9ba -->

# OAuth Refresh Token Authentication

The transparent proxy handles the HTTP communication protocol for both Internet and on-premise destinations protected with the *OAuth Refresh Token* flow.



<a name="loio5ab1150a827b47ec8ed4ab1f3f40d9ba__section_tfr_bwv_hcc"/>

## Prerequisites

To integrate this functionality, you must create an SAP BTP destination. This destination should have `Type` "HTTP" and `Authentication` "OAuth2RefreshToken", for example:

**OAuth 2 Refresh Token Destination**

> ### Sample Code:  
> ```
> {
>     "Name": "example-dest-oauth-2-refresh-token",
>     "Type": "HTTP",
>     "ProxyType": "Internet",
>     "URL": <application-url>,
>     "Authentication": "OAuth2RefreshToken",
>     "tokenServiceURLType": "Dedicated",
>     "clientId": <client-id>,
>     "clientSecret": <client-secret>,
>     "tokenServiceURL": <token-service-url>
> }
> ```

To target the destination with the name "example-dest-oauth-2-refresh-token" for handling by the transparent proxy, you should create a [Destination Custom Resource](destination-custom-resource-fc7951e.md) in a namespace of your choice.

**Destination CR for an OAuth 2 Refresh Token Destination**

> ### Sample Code:  
> ```
> apiVersion: destination.connectivity.api.sap/v1
> kind: Destination
> metadata:
>   name: <destination-cr-name>
> spec:
>   destinationRef:
>     name: "example-dest-oauth-2-refresh-token"
>   destinationServiceInstanceName: <dest-service-instance-name> // can be ommited if config.destinationService.defaultInstanceName is provided
> ```



<a name="loio5ab1150a827b47ec8ed4ab1f3f40d9ba__section_g4k_bwv_hcc"/>

## Consumption

For authentication type `OAuth2RefreshToken`, a refresh token has to be passed to the transparent proxy via `Authorization` header of scheme `Bearer`.

For more information, see [OAuth Refresh Token Authentication](oauth-refresh-token-authentication-bff0136.md).

> ### Note:  
> `<destination-cr-namespace>` can be omitted if the destination custom resource is created in the same namespace as the application workload.

**OAuth 2 Refresh Token Pseudocode Snippet**

> ### Sample Code:  
> ```
> function callOAuth2RefreshTokenHttpDestination() {
>     refreshToken = getPasswordRefreshToken()
>  
>     url = '<destination-cr-name>.<destination-cr-namespace>'
>     headers: {
>             // X-Tenant-Subdomain is required only when transparent proxy is in shared tenant mode
>             'X-Tenant-Subdomain': '<tenant-where-destination-is-located>',
>             'Authorization': 'Bearer ' + refreshToken,
>     }
>  
>     response = performHttpGetRequest(url, headers)
>     print(response)
> }
>  
> function getPasswordRefreshToken() {
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
>         passwordRefreshToken = parseJSON(response.body)['refresh_token']
>         return passwordRefreshToken
>     } catch (err) {
>         return fail('Cannot parse password refresh token: ' + err)
>     }
> }
> ```

**OAuth 2 Refresh Token Bash Snippet** 

> ### Sample Code:  
> ```
> # 1. Get password refresh token  (the 'refresh_token' value from the response body):
> curl -X POST \
>   -H "Content-Type: application/x-www-form-urlencoded" \
>   -H "Authorization: Basic <auth>" \
>   -d "username=<username>&password=<password>" \
>   '<tenant-for-retrieving-password-token>.authentication.ap10.hana.ondemand.com/oauth/token?grant_type=password&response_type=token'
>  
> # 2. Call HTTP destination protected with OAuth 2 Refresh Token using the refresh token retrieved in step 1:
> curl \
>   -H "X-Tenant-Subdomain: <tenant-where-destination-is-located>" \
>   -H "Authorization: Bearer <refresh-token>" \
>   '<destination-cr-name>.<destination-cr-namespace>'
> ```

**Related Information**  


[OAuth Refresh Token Authentication](oauth-refresh-token-authentication-bff0136.md "Create and configure an OAuth refresh token destination for an application.")

