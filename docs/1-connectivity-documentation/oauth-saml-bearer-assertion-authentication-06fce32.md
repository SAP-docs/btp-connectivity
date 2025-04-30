<!-- loio06fce328e65c4e0db94d88daacddca3d -->

# OAuth SAML Bearer Assertion Authentication

The Transparent Proxy handles the HTTP communication protocol for both Internet and on-premise destinations protected with the *OAuth SAML Bearer Assertion* flow.



<a name="loio06fce328e65c4e0db94d88daacddca3d__section_tfr_bwv_hcc"/>

## Prerequisites

**OAuth 2 SAML Bearer Assertion Destination**

> ### Sample Code:  
> ```
> {
>     "Name": "example-dest-oauth-2-saml-bearer-assertion",
>     "Type": "HTTP",
>     "ProxyType": "Internet",
>     "URL": <application-url>,
>     "Authentication": "OAuth2SAMLBearerAssertion",
>     "tokenServiceURLType": "Dedicated",
>     "tokenServiceURL": <token-service-url>,
>     "clientKey": <client-key>,
>     "apiKey": <api-key>,
>     "audience": <audience-url>,
>     "authnContextClassRef": "urn:oasis:names:tc:SAML:2.0:ac:classes:PreviousSession"  
> }
> ```

To target the destination with the name "example-dest-oauth-2-saml-bearer-assertion" for handling by the Transparent Proxy, you should create a [Destination Custom Resource](destination-custom-resource-fc7951e.md) in a namespace of your choice.

**Destination CR for an OAuth 2 SAML Bearer Assertion Destination**

> ### Sample Code:  
> ```
> apiVersion: destination.connectivity.api.sap/v1
> kind: Destination
> metadata:
>   name: <destination-cr-name>
> spec:
>   destinationRef:
>     name: "example-dest-oauth-2-saml-bearer-assertion"
>   destinationServiceInstanceName: <dest-service-instance-name> // can be ommited if config.destinationService.defaultInstanceName is provided
> ```



<a name="loio06fce328e65c4e0db94d88daacddca3d__section_g4k_bwv_hcc"/>

## Consumption

For authentication type `OAuth2SAMLBearerAssertion`, the cloud user identity has to be passed to the Transparent Proxy as a token represented by a JSON Web token \(JWT\) via `Authorization` header of scheme `Bearer`.

> ### Note:  
> `<destination-cr-namespace>` can be omitted if the destination custom resource is created in the same namespace as the application workload.

**OAuth 2 SAML Bearer Assertion Pseudocode Snippet**

> ### Sample Code:  
> ```
> function callOAuth2SAMLBearerAssertionHttpDestination() {
>     accessToken = getPasswordAccessToken()
>   
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

**OAuth 2 SAML Bearer Assertion Bash Snippet** 

> ### Sample Code:  
> ```
> # 1. Retrieve the user identity, which is the password access token (the 'access_token' value from the response body):
> curl -X POST \
>   -H "Content-Type: application/x-www-form-urlencoded" \
>   -H "Authorization: Basic <auth>" \
>   -d "username=<username>&password=<password>" \
>   '<tenant-for-retrieving-password-token>.authentication.ap10.hana.ondemand.com/oauth/token?grant_type=password&response_type=token'
>     
> # 2. Call HTTP destination protected with OAuth 2 SAML Bearer Assertion using the password access token retrieved in step 1:
> curl \
>   -H "X-Tenant-Subdomain: <tenant-where-destination-is-located>" \
>   -H "Authorization: Bearer <password-access-token>" \
>   '<destination-cr-name>.<destination-cr-namespace>'
> ```

**Related Information**  


[OAuth SAML Bearer Assertion Authentication](oauth-saml-bearer-assertion-authentication-c69ea6a.md "Create and configure an OAuth SAML Bearer Assertion destination for an application.")

