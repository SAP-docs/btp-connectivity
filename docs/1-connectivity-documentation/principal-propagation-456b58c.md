<!-- loio456b58cd5cd541d897f4bd3edf8ef7d2 -->

# Principal Propagation

Configure *principal propagation* for the transparent proxy for Kubernetes.

Principal propagation, also known as *user propagation*, lets you perform a single sign-on \(SSO\) of the cloud user towards an on-premise system.



<a name="loio456b58cd5cd541d897f4bd3edf8ef7d2__section_tfr_bwv_hcc"/>

## Prerequisites

The transparent proxy handles HTTP communication protocol for on-premise destinations which use *principal propagation*.

To integrate this functionality, you must:

-   Fulfill the on-premise/private cloud connectivity prerequisites
-   Create an SAP BTP Destination

This destination should have `Type` "HTTP" and `Authentication` "PrincipalPropagation", for example:

**Principal Propagation Destination**

> ### Sample Code:  
> ```
> {
>     "Name": "example-dest-principal-propagation",
>     "Type": "HTTP",
>     "ProxyType": "OnPremise",
>     "URL": <virtual-host>:<port>,
>     "Authentication": "PrincipalPropagation"
> }
> ```

To target the destination with the name "example-dest-principal-propagation" for handling by the transparent proxy, you should create a [Destination Custom Resource](destination-custom-resource-fc7951e.md) in a namespace of your choice.

**Destination CR for a Principal Propagation Destination**

> ### Sample Code:  
> ```
> apiVersion: destination.connectivity.api.sap/v1
> kind: Destination
> metadata:
>   name: <destination-cr-name>
> spec:
>   destinationRef:
>     name: "example-dest-principal-propagation"
>   destinationServiceInstanceName: <dest-service-instance-name> // can be ommited if config.destinationService.defaultInstanceName is provided
> ```



<a name="loio456b58cd5cd541d897f4bd3edf8ef7d2__section_g4k_bwv_hcc"/>

## Consumption

For the consumption of a destination with *principal propagation*, the cloud user identity is passed to the transparent proxy as a token represented by a JSON Web token \(JWT\) via an `Authorization` header of scheme `Bearer`. It is forwarded via the transparent proxy to the [Connectivity Proxy for Kubernetes](connectivity-proxy-for-kubernetes-e661713.md) and then to the [Cloud Connector](cloud-connector-e6c7616.md), which validates and further processes it to establish SSO with the on-premise system.

For more information, see [Authenticating Users against On-Premise Systems](authenticating-users-against-on-premise-systems-b643fbe.md)  and [Set Up Trust](set-up-trust-a4ee70f.md).

> ### Note:  
> `<destination-cr-namespace>` can be omitted if the destination custom resource is created in the same namespace as the application workload.

**Principal Propagation Pseudocode Snippet**

> ### Sample Code:  
> ```
> function callHttpDestinationPrincipalPropagation() {
>     passwordAccessToken = getPasswordAccessToken()
>     assertionToken = getAssertionToken(passwordAccessToken);
>  
>     url = '<destination-cr-name>.<destination-cr-namespace>'
>     headers = {
>                 // X-Tenant-Subdomain is required only when transparent proxy is in shared tenant mode
>                 'X-Tenant-Subdomain': '<tenant-where-destination-is-located>',
>                 'Authorization': 'Bearer ' + assertionToken,
>     }
>          
>     response = performHttpGetRequest(url, headers)
>     print(response)
> }
>  
> function getAssertionToken(accessToken) {
>     host = '<tenant-to-retrieve-assertion-token>.authentication.ap10.hana.ondemand.com'
>     path = '/oauth/token?grant_type=urn:ietf:params:oauth:grant-type:jwt-bearer&response_type=token&assertion=' + accessToken
>     url = host + path
>     headers = {
>                 'Authorization': 'Basic <auth>',
>     }
>  
>     response = performHttpGetRequest(url, headers);
>  
>     try {
>         assertionToken = parseJSON(response.body)['access_token']
>         return assertionToken
>     } catch (err) {
>         return fail('Cannot parse assertion token token: ' + err)
>     }
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
>         return fail('Cannot parse password access token: ' + err)
>     }
> }
> ```

**Principal Propagation Bash Snippet** 

> ### Sample Code:  
> ```
> # 1. Get password access token (the 'access_token' value from the response body):
> curl -X POST \
>   -H "Content-Type: application/x-www-form-urlencoded" \
>   -H "Authorization: Basic <auth>" \
>   -d "username=<username>&password=<password>" \
>   '<tenant-for-retrieving-password-token>.authentication.ap10.hana.ondemand.com/oauth/token?grant_type=password&response_type=token'
>   
> # 2. Get assertion token (the 'access_token' value from the response body) using the password access token retrieved in step 1:
> curl \
> -H 'Authorization: Basic <auth>' \
> 'https://<tenant-to-retrieve-assertion-token>.authentication.ap10.hana.ondemand.com/oauth/token?grant_type=urn:ietf:params:oauth:grant-type:jwt-bearer&response_type=token&assertion=<passwordAccessToken>'
>  
> # 3. Call HTTP destination protected with Principal Propagation using the assertion token retrieved in step 2:
> curl \
> -H 'X-Tenant-Subdomain: <tenant-where-destination-is-located>' \
> -H 'Authorization: Bearer <assertionToken>' \
> 'https://<destination-cr-name>.<destination-cr-namespace>'
> ```

**Related Information**  


[Principal Propagation](principal-propagation-e2cbb48.md "Enable single sign-on (SSO) by forwarding the identity of cloud users to a remote system or service.")

