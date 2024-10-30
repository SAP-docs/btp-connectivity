<!-- loio8b6e0195318f490f85c4f19f138acdf3 -->

# Technical User Propagation

Configure *technical user propagation* for the transparent proxy for Kubernetes.

*Technical user propagation* is similar to *principal propagation*, but in this case, a technical user is propagated instead of a business user. The retrieval of the access token performs the OAuth 2.0 client credentials flow, according to the token service configurations in the destination.



<a name="loio8b6e0195318f490f85c4f19f138acdf3__section_tfr_bwv_hcc"/>

## Prerequisites

The transparent proxy handles HTTP communication protocol for on-premise destinations which use *technical user propagation*.

To integrate this functionality, you must:

-   Fulfill the on-premise/private cloud connectivity prerequisites
-   Create an SAP BTP Destination

This destination should have `Type` "HTTP" and `Authentication` "OAuth2TechnicalUserPropagation", for example:

**Technical User Propagation Destination**

> ### Sample Code:  
> ```
> {
>     "Name": "example-dest-technical-user-propagation",
>     "Type": "HTTP",
>     "ProxyType": "OnPremise",
>     "URL": <virtual-host>:<port>,
>     "Authentication": "OAuth2TechnicalUserPropagation"
>     "tokenServiceURLType": <token-service-url-type>,
>     "clientId": <client-id>,
>     "clientSecret": <client-secret>,
>     "tokenServiceURL": <token-service-url>
> }
> ```

To target the destination with the name "example-dest-technical-user-propagation" for handling by the transparent proxy, you should create a [Destination Custom Resource](destination-custom-resource-fc7951e.md) in a namespace of your choice.

**Destination CR for a Technical User Propagation Destination**

> ### Sample Code:  
> ```
> apiVersion: destination.connectivity.api.sap/v1
> kind: Destination
> metadata:
>   name: <destination-cr-name>
> spec:
>   destinationRef:
>     name: "example-dest-technical-user-propagation"
>   destinationServiceInstanceName: <dest-service-instance-name> // can be ommited if config.destinationService.defaultInstanceName is provided
> ```



<a name="loio8b6e0195318f490f85c4f19f138acdf3__section_g4k_bwv_hcc"/>

## Consumption

For the consumption of a destination with *technical user propagation*, the technical user is obtained from the destination by the transparent proxy, forwarded to the [Connectivity Proxy for Kubernetes](connectivity-proxy-for-kubernetes-e661713.md), and then to the [Cloud Connector](cloud-connector-e6c7616.md), which validates and further processes it to establish SSO with the on-premise system.

For more information, see  [Authenticating Users against On-Premise Systems](authenticating-users-against-on-premise-systems-b643fbe.md) and [Configuring Technical User Propagation](configuring-technical-user-propagation-b62e588.md).

> ### Note:  
> `<destination-cr-namespace>` can be omitted if the destination custom resource is created in the same namespace as the application workload.

**Technical User Propagation Pseudocode Snippet**

> ### Sample Code:  
> ```
> function callHttpDestinationTechnicalUserPropagation() {
>   url = '<destination-cr-name>.<destination-cr-namespace>'
>   headers = {
>             // X-Tenant-Subdomain is required only when transparent proxy is in shared tenant mode
>             'X-Tenant-Subdomain': '<tenant-where-destination-is-located>',
>         }
>      
>   response = performHttpGetRequest(url, headers)
>   print(response)
> }
> ```

**Technical User Propagation Bash Snippet** 

> ### Sample Code:  
> ```
> # Call HTTP destination protected with Technical User Propagation:
> curl <destination-cr-name>.<destination-cr-namespace> -H 'X-Tenant-Subdomain: <tenant-where-destination-is-located>' -H 'X-Token-Service-Tenant: <tenant-to-retrieve-oauth-token>'
> ```

