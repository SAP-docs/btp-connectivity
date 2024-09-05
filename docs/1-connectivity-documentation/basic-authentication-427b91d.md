<!-- loio427b91d181d647bbb9ae9d26c0f0e7d3 -->

# Basic Authentication

The transparent proxy handles the HTTP communication protocol for both Internet and on-premise destinations protected with *Basic Authentication*.



<a name="loio427b91d181d647bbb9ae9d26c0f0e7d3__section_tfr_bwv_hcc"/>

## Prerequisites

To integrate this functionality, you must create an SAP BTP destination. This destination should have `Type` "HTTP" and `Authentication` "BasicAuthentication", for example:

**Basic Authentication Destination**

> ### Sample Code:  
> ```
> {
>     "Name": "example-dest-basic",
>     "Type": "HTTP",
>     "ProxyType": "Internet",
>     "URL": <application-url>,
>     "Authentication": "BasicAuthentication"
>     "User": <username>,
>     "Password": <password>
> }
> ```

To target the destination with the name "example-dest-basic-auth" for handling by the transparent proxy, you should create a [Destination Custom Resource](destination-custom-resource-fc7951e.md) in a namespace of your choice.

**Destination CR for Basic Authentication**

> ### Sample Code:  
> ```
> apiVersion: destination.connectivity.api.sap/v1
> kind: Destination
> metadata:
>   name: <destination-cr-name>
> spec:
>   destinationRef:
>     name: "example-dest-basic"
>   destinationServiceInstanceName: <dest-service-instance-name> // can be ommited if config.destinationService.defaultInstanceName is provided
> ```



<a name="loio427b91d181d647bbb9ae9d26c0f0e7d3__section_g4k_bwv_hcc"/>

## Consumption

For consumption of destination with authentication type BasicAuthentication no additional Authorization headers have to be provided to the transparent proxy as all necessary data for authorization is in the destination.

> ### Note:  
> `<destination-cr-namespace>` can be omitted if the destination custom resource is created in the same namespace as the application workload.

**Basic Authentication Pseudocode Snippet**

> ### Sample Code:  
> ```
> function callHttpDestinationBasic() {
>   url = '<destination-cr-name>.<destination-cr-namespace>'
>   headers = {
>             // X-Tenant-Subdomain is required only when transparent proxy is in shared tenant mode
>             'X-Tenant-Subdomain': '<tenant-where-destination-is-located>'
>         };
>      
>   response = http.get(url, headers)
>   print(response)
> }
> ```

**Basic Authentication Bash Snippet** 

> ### Sample Code:  
> ```
> # Call HTTP destination protected with Basic authentication:
> curl <destination-cr-name>.<destination-cr-namespace> -H 'X-Tenant-Subdomain: <tenant-where-destination-is-located>'
> ```

**Related Information**  


[Client Authentication Types for HTTP Destinations](client-authentication-types-for-http-destinations-4e13a04.md "Find details about client authentication types for HTTP destinations.")

