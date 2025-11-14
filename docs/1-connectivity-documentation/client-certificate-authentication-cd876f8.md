<!-- loiocd876f8d496f4be0a0c87bd023e3f17a -->

# Client Certificate Authentication

The Transparent Proxy handles HTTP communication protocol for both Internet and on-premise destinations protected with *Client Certificate Authentication*.

For this authentication type, the Transparent Proxy manages the client certificate addition \(client certificates and CA certificates\) by getting them from the destination and adding them to the HTTP client used to establish the communication between the client and server.



<a name="loiocd876f8d496f4be0a0c87bd023e3f17a__section_tfr_bwv_hcc"/>

## Prerequisites

To integrate this functionality, you must create an SAP BTP destination. This destination should have `Type` "HTTP" and `Authentication` "ClientCertificateAuthentication", for example:

**Client Certificate Destination**

> ### Sample Code:  
> ```
> {
>     "Name": "example-dest-client-certificate",
>     "Type": "HTTP",
>     "ProxyType": "Internet",
>     "URL": <application-url>,
>     "Authentication": "ClientCertificateAuthentication"
>     "KeyStorePassword": <key-store-password>,
>     "TrustStoreLocation": <trust-store-location>,
>     "KeyStoreLocation": <key-store-location>
> }
> ```

> ### Restriction:  
> Limitations for usage:
> 
> -   Supported cert store types are p12, pfx, pem, der, cer, crt.
> -   Only RSA pkcs1\(starting with header RSA PRIVATE KEY and having headers with encryption information\) keys are currently supported for decryption from PEM format. The following encryption algorithms are supported DES-CBC, DES-EDE3-CBC, AES-128-CBC, AES-192-CBC, and AES-256-CBC. All key types should be supported if no encryption is present.
> -   KeyStore.Source=ClientProvided is not supported as the Transparent Proxy can manage only certificates stored in the Destination Service.

For more information, see [Client Certificate Authentication](client-certificate-authentication-4e13a04.md#loio4e13a04147314e8e9e54321f25d93fdc__clientCert).

To target the destination with the name "example-dest-client-certificate" for handling by the Transparent Proxy, you should create a [Destination Custom Resource](destination-custom-resource-fc7951e.md) in a namespace of your choice.

**Destination CR for a Client Certificate Destination**

> ### Sample Code:  
> ```
> apiVersion: destination.connectivity.api.sap/v1
> kind: Destination
> metadata:
>   name: <destination-cr-name>
> spec:
>   destinationRef:
>     name: "example-dest-client-certificate"
>   destinationServiceInstanceName: <dest-service-instance-name> // can be ommited if config.destinationService.defaultInstanceName is provided
> ```



<a name="loiocd876f8d496f4be0a0c87bd023e3f17a__section_g4k_bwv_hcc"/>

## Consumption

For consumption of destination with authentication type *ClientCertificateAuthentication*, no additional `Authorization` headers need to be provided to the Transparent Proxy as all necessary data for authorization is in the destination.

> ### Note:  
> `<destination-cr-namespace>` can be omitted if the destination custom resource is created in the same namespace as the application workload.

**Client Certificate Authentication Pseudocode Snippet**

> ### Sample Code:  
> ```
> function callHttpsDestinationClientCertificateAuthentication() {
>   url = '<destination-cr-name>.<destination-cr-namespace>'
>   headers = {
>             // X-Tenant-Subdomain is required only when Transparent Proxy is in shared tenant mode
>             'X-Tenant-Subdomain': '<tenant-where-destination-is-located>'
>         }
>      
>   response = http.get(url, headers)
>   print(response)
> }
> ```

**Client Certificate Authentication Bash Snippet** 

> ### Sample Code:  
> ```
> # Call HTTP destination protected with Client Certificate authentication:
> curl <destination-cr-name>.<destination-cr-namespace> -H 'X-Tenant-Subdomain': '<tenant-where-destination-is-located>'
> ```

**Related Information**  


[Client Certificate Authentication](client-certificate-authentication-4e13a04.md "Create and configure a Client Certificate destination for an application.")

