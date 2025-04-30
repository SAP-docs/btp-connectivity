<!-- loio8813df7e39e5472ca5bdcdd34598592d -->

# OAuth Token Exchange Authentication

The Transparent Proxy handles the HTTP communication protocol for both Internet and on-premise destinations protected with the *OAuth Token Exchange* flow.



<a name="loio8813df7e39e5472ca5bdcdd34598592d__section_tfr_bwv_hcc"/>

## Prerequisites

To integrate this functionality, you must create an SAP BTP destination. This destination should have `Type` "HTTP" and `Authentication` "OAuth2TokenExchange", for example:

> ### Note:  
> All examples below assume usage of an IAS token service URL, but any authorization server that supports [RFC-8963](https://datatracker.ietf.org/doc/html/rfc8693) can be used.

**OAuth 2 Token Exchange Destination**

> ### Sample Code:  
> ```
> {
>     "Name": "example-dest-oauth-2-token-exchange",
>     "Type": "HTTP",
>     "ProxyType": "Internet",
>     "URL": <application-url>,
>     "Authentication": "OAuth2TokenExchange",
>     "tokenServiceURLType": "Dedicated",
>     "clientId": <client-id>,
>     "clientSecret": <client-secret>,
>     "tokenServiceURL": <ias-token-service-URL>
> }
> ```

To target the destination with the name "example-dest-oauth-2-token-exchange" for handling by the Transparent Proxy, you should create a [Destination Custom Resource](destination-custom-resource-fc7951e.md) in a namespace of your choice.

**Destination CR for an OAuth 2 Token Exchange Destination**

> ### Sample Code:  
> ```
> apiVersion: destination.connectivity.api.sap/v1
> kind: Destination
> metadata:
>   name: <destination-cr-name>
> spec:
>   destinationRef:
>     name: "example-dest-oauth-2-token-exchange"
>   destinationServiceInstanceName: <dest-service-instance-name> // can be ommited if config.destinationService.defaultInstanceName is provided
> ```



<a name="loio8813df7e39e5472ca5bdcdd34598592d__section_g4k_bwv_hcc"/>

## Consumption

For authentication type `OAuth2TokenExchange`, the cloud user identity has to be passed to the Transparent Proxy as a token represented by a JSON Web token \(JWT\) via an `Authorization` header of scheme `Bearer`.

> ### Note:  
> `<destination-cr-namespace>` can be omitted if the destination custom resource is created in the same namespace as the application workload.

**OAuth 2 Token Exchange Pseudocode Snippet**

> ### Sample Code:  
> ```
> function callOAuth2TokenExchangeHttpsDestination() {
>     accessToken = getPasswordAccessToken()
>     url = '<destination-cr-name>.<destination-cr-namespace>'
>     headers: {
>             // X-Tenant-Subdomain is required only when Transparent Proxy is in shared tenant mode
>             'X-Tenant-Subdomain': '<tenant-where-destination-is-located>',
>             'Authorization': 'Bearer ' + accessToken,
>             'X-Subject-Token-Type': 'urn:ietf:params:oauth:token-type:jwt',
>             'X-Actor-Token: <actor-token>',        # Optional: Include if an actor token is available
>             'X-Actor-Token-Type: urn:ietf:params:oauth:token-type:jwt',  # Optional: Specify the token type if using 'X-Actor-Token' 
>     }
>  
>     response = performHttpGetRequest(url, headers)
>     print(response)
> }
>  
> function getPasswordAccessToken() {
>     url = 'https://<tenant-domain>/oauth2/token'
>      
>     headers = {
>                 'Content-Type': 'application/x-www-form-urlencoded',
>                 'Authorization': 'Basic <auth>',
>     }
>  
>     postData = {
>             'username': '<username>',
>             'password': '<password>',
>             'grant_type' : 'password',
>             'client_id' : '<client_id>',
>             'token_format' : 'jwt',
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
> function getActorAccessToken() {
>     const url = 'https://<tenant-domain>/oauth2/token';
>  
>     const headers = {
>         'Content-Type': 'application/x-www-form-urlencoded',
>         'Authorization': 'Basic <actor-basic-auth>',
>     };
>  
>     const postData = {
>         'grant_type': 'client_credentials',
>         'client_id': '<actor_client_id>',
>         'token_format': 'jwt',
>     };
>  
>     const response = performHttpPostRequest(url, headers, postData);
>  
>     try {
>         const actorAccessToken = parseJSON(response.body)['access_token'];
>         return actorAccessToken;
>     } catch (err) {
>         return fail('Cannot parse actor access token: ' + err);
>     }
> }
> ```

**OAuth 2 Token Exchange Bash Snippet** 

> ### Sample Code:  
> ```
> # Get password access token (the 'access_token' value from the response body):
> curl --request POST \
>   --url https://<tenant-domain>/oauth2/token \
>   --header 'Authorization: Basic <basic-auth>' \
>   --header 'Content-Type: application/x-www-form-urlencoded' \
>   --data username=<username> \
>   --data password=<password> \
>   --data grant_type=password \
>   --data client_id=<subject_client_id> \
>   --data token_format=jwt
>  
> # Optional - Get token representing the identity of the acting party on behalf of the subject.
> curl --request POST \
>   --url https://<tenant-domain>/oauth2/token \
>   --header 'Authorization: Basic <actor-basic-auth>' \
>   --header 'Content-Type: application/x-www-form-urlencoded' \
>   --data grant_type=client_credentials \
>   --data client_id=<actor_client_id> \
>   --data token_format=jwt
>  
> # Call HTTP destination protected with OAuth 2 Token Exchange:
> curl \
>   -H "X-Tenant-Subdomain: <tenant-where-destination-is-located>" \
>   -H "Authorization: Bearer <password-access-token>" \
>   -H "X-Subject-Token-Type: urn:ietf:params:oauth:token-type:jwt" \
>   -H "X-Actor-Token: <actor-token>" \        # Optional: Include if an actor token is available
>   -H "X-Actor-Token-Type: urn:ietf:params:oauth:token-type:jwt" \  # Optional: Specify the token type if using 'X-Actor-Token'
>   '<destination-cr-name>.<destination-cr-namespace>'
> ```

