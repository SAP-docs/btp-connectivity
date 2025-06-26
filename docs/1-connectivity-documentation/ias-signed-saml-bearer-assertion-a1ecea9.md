<!-- loioa1ecea9cec924b7bbc7ad6ebc13f784c -->

# IAS-Signed SAML Bearer Assertion

The Transparent Proxy supports [Token Retrieval Using IAS-Signed SAML2.0 Assertions](token-retrieval-using-ias-signed-saml2-0-assertions-a943bb7.md) for the HTTP communication protocol for both *Internet* and *On-Premise* destinations.



<a name="loioa1ecea9cec924b7bbc7ad6ebc13f784c__section_lcv_jym_sfc"/>

## Preparation

**Provider Destination**

> ### Sample Code:  
> ```
> {
>     "Name": "samlAssertionProviderDest",
>     "Type": "HTTP",
>     "ProxyType": "Internet",
>     "URL": "<application-url>",
>     "Authentication": "OAuth2TokenExchange",
>     "tokenServiceURLType": "Dedicated",
>     "tokenServiceURL": "<ias-token-service-url>",
>     "clientId": "<ias-client-id>",
>     "clientSecret": "<ias-client-secret>",
>     "tokenServiceURL.queries.requested_token_type": "urn:ietf:params:oauth:token-type:saml2",
>     "tokenServiceURL.queries.resource": "urn:sap:identity:application:provider:name:<ias-saml-dependency-name>"
> }
> ```

The example below uses XSUAA on region cf-ap10 as a token service:

**Consumer Destination** 

> ### Sample Code:  
> ```
> {
>     "Name": "samlAssertionConsumerDest",
>     "Type": "HTTP",
>     "ProxyType": "Internet",
>     "URL": "<application-url>",
>     "Authentication": "OAuth2SAMLBearerAssertion",
>     "tokenServiceURLType": "Dedicated",
>     "tokenServiceURL": "https://<tenant-subdomain>.authentication.ap10.hana.ondemand.com/oauth/token/alias/<tenant-subdomain>.cf-ap10",
>     "clientKey": "<token-service-user>",
>     "tokenServiceUser": "<token-service-user>",
>     "tokenServicePassword": "<token-service-password>",
>     "SAMLAssertionProvider": "ClientProvided"
> }
> ```

To target the destination with the name "samlAssertionConsumerDest" for handling by the Transparent Proxy, you should create a destination custom resource in a namespace of your choice.

> ### Sample Code:  
> ```
> apiVersion: destination.connectivity.api.sap/v1
> kind: Destination
> metadata:
>   name: <destination-cr-name>
> spec:
>   destinationRef:
>     name: "samlAssertionConsumerDest"
>   destinationServiceInstanceName: <dest-service-instance-name> // can be ommited if config.destinationService.defaultInstanceName is provided
>   chainRef:
>     name: com.sap.iasGeneratedOAuth2SamlBearerAssertion // can be omitted or overridden if 'X-Chain-Name' header is passed
>     variables:
>     - name: samlProviderDestinationName // can be omitted or overridden if 'X-Chain-var-samlProviderDestinationName' header is passed
>       value: samlAssertionProviderDest
>     - name: subjectTokenType // can be omitted or overridden if 'X-Chain-var-subjectTokenType' header is passed
>       value: urn:ietf:params:oauth:token-type:access_token
> ```



<a name="loioa1ecea9cec924b7bbc7ad6ebc13f784c__section_zpb_jym_sfc"/>

## Consumption

For authentication type *OAuth2SAMLBearerAssertion*, the cloud user identity must passed to the Transparent Proxy as a token represented by a JSON Web token \(JWT\) via an *Authorization Header* of scheme *Bearer*.

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
>             // X-Tenant-Subdomain is required only when transparent proxy is in shared tenant mode
>             'X-Tenant-Subdomain': '<tenant-where-destination-is-located>',
>             'Authorization': 'Bearer ' + accessToken,
>             // 'X-Chain' headers are required only if the are not present as configuration in the Destination CR. If passed they will override the configuration from the CR
>             'X-Chain-Name': 'com.sap.iasGeneratedOAuth2SamlBearerAssertion' \
>             'X-Chain-Var-samlProviderDestinationName': '<provider-destination-name>'   \
>             'X-Chain-Var-subjectTokenType': 'urn:ietf:params:oauth:token-type:access_token' \
>     }  
>   
>     response = performHttpGetRequest(url, headers)
>     print(response)
> }
>   
> function getPasswordAccessToken() {
>     url = 'https://<ias-tenant>.accounts400.ondemand.com/oauth2/token'
>     headers = {
>                 'Content-Type': 'application/x-www-form-urlencoded',
>                 'Authorization': 'Basic <auth>',
>     }
>   
>     postData = {
>             'username': '<username>',
>             'password': '<password>',
>             'grant_type': 'password',
>             'client_id': '<client-id>',
>             'token_format': 'access_token'
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
> curl --request POST \
>   --url https://<ias-tenant>.accounts400.ondemand.com/oauth2/token \
>   --header 'Authorization: Basic <basic-auth>' \
>   --header 'Content-Type: application/x-www-form-urlencoded' \
>   --data username=<username> \
>   --data password=<password> \
>   --data grant_type=password \
>   --data client_id=<oidc-app-client-id> \
>   --data token_format=access_token
>     
> # 2.1 Call HTTP destination protected with OAuth 2 SAML Bearer Assertion using the password access token retrieved in step 1:
> curl \
>   -H "X-Tenant-Subdomain: <tenant-where-destination-is-located>" \
>   -H "Authorization: Bearer <password-access-token>" \
>   '<destination-cr-name>.<destination-cr-namespace>'
> # 2.2 If chainRef.name and variables are not specified in the Destination CR they have to be provided as headers. Call the HTTP destination protected with OAuth 2 SAML Bearer Assertion using the password access token retrieved in step 1:
> curl \
>   -H "X-Tenant-Subdomain: <tenant-where-destination-is-located>" \
>   -H "Authorization: Bearer <password-access-token>" \
>   -H "X-Chain-Name: com.sap.iasGeneratedOAuth2SamlBearerAssertion" \
>   -H "X-Chain-Var-samlProviderDestinationName: <provider-destination-name>"   \
>   -H "X-Chain-Var-subjectTokenType: urn:ietf:params:oauth:token-type:access_token" \
>   '<destination-cr-name>.<destination-cr-namespace>'
> ```

