<!-- loio5ef40e35d1494603b46c49b501a65acb -->

# No Authentication

The Transparent Proxy handles HTTP and TCP communication protocols for both Internet and on-premise destinations without authentication.



<a name="loio5ef40e35d1494603b46c49b501a65acb__section_tfr_bwv_hcc"/>

## Prerequisites

To integrate this functionality, you must create an SAP BTP destination. This destination should have `Type` "HTTP" and `Authentication` "NoAuthentication", for example:

**No Authentication Destination**

> ### Sample Code:  
> ```
> {
>     "Name": "example-dest-no-auth",
>     "Type": "HTTP",
>     "ProxyType": "Internet",
>     "URL": <application-url>,
>     "Authentication": "NoAuthentication"
> }
> ```

To target the destination with the name "example-dest-basic-auth" for handling by the Transparent Proxy, you should create a [Destination Custom Resource](destination-custom-resource-fc7951e.md) in a namespace of your choice.

**Destination CR for No Authentication Destination**

> ### Sample Code:  
> ```
> apiVersion: destination.connectivity.api.sap/v1
> kind: Destination
> metadata:
>   name: <destination-cr-name>
> spec:
>   destinationRef:
>     name: "example-dest-no-auth"
>   destinationServiceInstanceName: <dest-service-instance-name> // can be ommited if config.destinationService.defaultInstanceName is provided
> ```



<a name="loio5ef40e35d1494603b46c49b501a65acb__section_g4k_bwv_hcc"/>

## Consumption

> ### Note:  
> `<destination-cr-namespace>` can be omitted if the destination custom resource is created in the same namespace as the application workload.

**No Authentication Pseudocode Snippet**

> ### Sample Code:  
> ```
> function callHttpDestinationNoAuth() {
>   url = '<destination-cr-name>.<destination-cr-namespace>'
>   headers = {
>             // X-Tenant-Subdomain is required only when Transparent Proxy is in shared tenant mode
>             'X-Tenant-Subdomain': '<tenant-where-destination-is-located>'
>         };
>  
>   response = http.get(url, headers)
>   print(response)
> }
> ```

**No Authentication Bash Snippet** 

> ### Sample Code:  
> ```
> # Call HTTP destination without authentication:
> curl <destination-cr-name>.<destination-cr-namespace> -H 'X-Tenant-Subdomain: <tenant-where-destination-is-located>'
> ```

**Related Information**  


[Client Certificate Authentication](client-certificate-authentication-4e13a04.md "Create and configure a Client Certificate destination for an application.")

