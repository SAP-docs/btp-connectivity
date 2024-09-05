<!-- loio23db6d9e21ee4698a16ea8ab5ce5ddd5 -->

# SAML Assertion Authentication

The transparent proxy handles the HTTP communication protocol for both Internet and on-premise destinations protected with the *SAML Assertion* flow.



<a name="loio23db6d9e21ee4698a16ea8ab5ce5ddd5__section_tfr_bwv_hcc"/>

## Prerequisites

**SAML Assertion Destination**

> ### Sample Code:  
> ```
> {
>     "Name": "example-dest-saml-assertion",
>     "Type": "HTTP",
>     "ProxyType": "Internet",
>     "URL": <application-url>,
>     "Authentication": "SAMLAssertion",    
>     "audience": <audience-url>,
>     "authnContextClassRef": "urn:oasis:names:tc:SAML:2.0:ac:classes:X509"
> }
> ```

To target the destination with the name "example-dest-saml-assertion" for handling by the transparent proxy, you should create a [Destination Custom Resource](destination-custom-resource-fc7951e.md) in a namespace of your choice.

**Destination CR for a SAML Assertion Destination**

> ### Sample Code:  
> ```
> apiVersion: destination.connectivity.api.sap/v1
> kind: Destination
> metadata:
>   name: <destination-cr-name>
> spec:
>   destinationRef:
>     name: "example-dest-saml-assertion"
>   destinationServiceInstanceName: <dest-service-instance-name> // can be ommited if config.destinationService.defaultInstanceName is provided
> ```



<a name="loio23db6d9e21ee4698a16ea8ab5ce5ddd5__section_g4k_bwv_hcc"/>

## Consumption

For authentication type `SAMLAssertion`, the cloud user identity has to be passed to the transparent proxy as a token represented by a JSON Web token \(JWT\) via `Authorization` header of scheme `Bearer`.

> ### Note:  
> `<destination-cr-namespace>` can be omitted if the destination custom resource is created in the same namespace as the application workload.

**SAML assertion Pseudocode Snippet**

> ### Sample Code:  
> ```
> function callSAMLAssertionHttpDestination() {
>     accessToken = getPasswordAccessToken()
>  
>     url = '<destination-cr-name>.<destination-cr-namespace>'
>     headers: {
>             // X-Tenant-Subdomain is required only when transparent proxy is in shared tenant mode
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
>       return passwordAccessToken
>     } catch (err) {
>         return fail('Cannot parse password access token: ' + err)
>     }
> }
> ```

**SAML Assertion Bash Snippet** 

> ### Sample Code:  
> ```
> # 1. Retrieve the user identity, which is the password access token (the 'access_token' value from the response body):
> curl -X POST \
>   -H "Content-Type: application/x-www-form-urlencoded" \
>   -H "Authorization: Basic <auth>" \
>   -d "username=<username>&password=<password>" \
>   '<tenant-for-retrieving-password-token>.authentication.ap10.hana.ondemand.com/oauth/token?grant_type=password&response_type=token'
>    
> # 2. Call HTTP destination protected with SAML Assertion using the password access token retrieved in step 1:
> curl \
>   -H "X-Tenant-Subdomain: <tenant-where-destination-is-located>" \
>   -H "Authorization: Bearer <password-access-token>" \
>   '<destination-cr-name>.<destination-cr-namespace>'
> ```

**Related Information**  


[SAML Assertion Authentication](saml-assertion-authentication-d81e168.md "Create and configure an SAML Assertion destination for an application.")

