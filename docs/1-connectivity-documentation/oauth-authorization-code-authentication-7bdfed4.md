<!-- loio7bdfed49c6d0451b8aafe1c94da8c770 -->

# OAuth Authorization Code Authentication

The transparent proxy handles the HTTP communication protocol for both Internet and on-premise destinations protected with the *OAuth Authorization Code* flow.



<a name="loio7bdfed49c6d0451b8aafe1c94da8c770__section_tfr_bwv_hcc"/>

## Prerequisites

To integrate this functionality, you must create an SAP BTP destination. This destination should have `Type` "HTTP" and `Authentication` "OAuth2AuthorizationCode", for example:

**OAuth 2 Authorization Code Destination**

> ### Sample Code:  
> ```
> {
>     "Name": "example-dest-oauth-2-auth-code",
>     "Type": "HTTP",
>     "ProxyType": "Internet",
>     "URL": <application-url>,
>     "Authentication": "OAuth2AuthorizationCode",
>     "tokenServiceURLType": "Dedicated",
>     "clientId": <client-id>,
>     "clientSecret": <client-secret>,
>     "tokenServiceURL": <token-service-URL>
> }
> ```

To target the destination with the name "example-dest-oauth-2-auth-code" for handling by the transparent proxy, you should create a [Destination Custom Resource](destination-custom-resource-fc7951e.md) in a namespace of your choice.

**Destination CR for an OAuth 2 Authhroziation Code Destination**

> ### Sample Code:  
> ```
> apiVersion: destination.connectivity.api.sap/v1
> kind: Destination
> metadata:
>   name: <destination-cr-name>
> spec:
>   destinationRef:
>     name: "example-dest-oauth-2-auth-code"
>   destinationServiceInstanceName: <dest-service-instance-name> // can be ommited if config.destinationService.defaultInstanceName is provided
> ```



<a name="loio7bdfed49c6d0451b8aafe1c94da8c770__section_g4k_bwv_hcc"/>

## Consumption

For consumption of a destination with authentication type `OAuth2AuthorizationCode`, the code of the business user from the authorization server has to be passed to the transparent proxy via `Authorization` header of scheme `Bearer`. You can also pass the optional headers 'X-redirect-uri' and 'X-code-verifier' to the request. They can also be configured in the destination configuration. If any or both of the headers are present in the request as well as in the destination configuration, the transparent proxy attaches the request headers to the request to the Destination service.

For more information, see [OAuth Authorization Code Authentication](oauth-authorization-code-authentication-9f634f6.md).

> ### Note:  
> `<destination-cr-namespace>` can be omitted if the destination custom resource is created in the same namespace as the application workload.

**OAuth 2 Authorization Code Pseudocode Snippet**

> ### Sample Code:  
> ```
> function callHttpDestinationWithOAuth2AuthorizationCode() {
>     passwordAccessToken = getPasswordAccessToken()
>     authorizationCode = getAuthorizationCode(accessToken);
>  
>     url = '<destination-cr-name>.<destination-cr-namespace>'
>     headers: {
>             // X-Tenant-Subdomain is required only when transparent proxy is in shared tenant mode
>             'X-Tenant-Subdomain': '<tenant-where-destination-is-located>',
>             'Authorization': 'Bearer ' + authorizationCode,
>     }
>  
>     response = performHttpGetRequest(url, headers)
>  
>     print(response)
> }
>  
> function getAuthorizationCode(accessToken) {
>     url = '<tenant-for-retrieving-auth-code>.authentication.ap10.hana.ondemand.com/oauth/authorize?client_id=<client-id>&response_type=code'
>     headers = {
>                 'Authorization': 'Bearer ' + accessToken,
>     }
>  
>     response = performHttpGetRequest(url, headers);
>  
>     try {
>         locationHeaderValue = response.headers['location'];
>         code = locationHeaderValue.split('code=')[1];
>         return code;
>     } catch (err) {
>         return fail('Cannot retrieve authorization code: ' + err);
>     }
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

**OAuth 2 Authorization Code Bash Snippet** 

> ### Sample Code:  
> ```
> # 1. Retrieve the user identity, which is the password access token (the 'access_token' value from the response body):
> curl -X POST \
>   -H "Content-Type: application/x-www-form-urlencoded" \
>   -H "Authorization: Basic <auth>" \
>   -d "username=<username>&password=<password>" \
>   '<tenant-for-retrieving-password-token>.authentication.ap10.hana.ondemand.com/oauth/token?grant_type=password&response_type=token'
>  
> # 2. Get authorization code (the 'location' header value from the response) using the password access token retrieved in step 1:
> curl \
>   -H "Authorization: Bearer <password-access-token>" \
>   '<tenant-for-retrieving-auth-code>.authentication.ap10.hana.ondemand.com/oauth/authorize?client_id=<client-id>&response_type=code'
>  
> # 3. Call HTTP destination protected with OAuth 2 Authorization Code using the authorisation code retrieved in step 2:
> curl \
>   -H "X-Tenant-Subdomain: <tenant-where-destination-is-located>" \
>   -H "Authorization: Bearer <authorization-code>" \
>   '<destination-cr-name>.<destination-cr-namespace>'
> ```

**Related Information**  


[OAuth Authorization Code Authentication](oauth-authorization-code-authentication-9f634f6.md "Create and configure an OAuth Authorization Code destination for an application.")

