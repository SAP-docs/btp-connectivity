<!-- loioc5257cf110bf4b7b9054eab74ededff4 -->

# Using the Transparent Proxy

Use the transparent proxy for Kubernetes in different SAP BTP communication scenarios.

The transparent proxy lightens the way your Kubernetes workloads connect to remote systems using BTP destinations of type *Internet* and *OnPremise*. It provides authentication, principal propagation, SOCKS5 handshake, and easy access to the destination target systems by exposing them as [Kubernetes Services](https://kubernetes.io/docs/concepts/services-networking/service/).

To target a given destination for handling by the transparent proxy, you should create a custom Kubernetes resource of type *destinations.destination.connectivity.api.sap* that references the given destination. If you do not create a custom Kubernetes resource of type destinations.destination.connectivity.api.sap for a given destination, the destination in question will not be handled by the transparent proxy.

> ### Note:  
> There should be no Kubernetes service in the namespace of the destination custom resource or in the namespace where the transparent proxy is installed, with a name equal to the destination custom resource. The transparent proxy handles the creation of Kubernetes services based on the information stored in these custom resources.



<a name="loioc5257cf110bf4b7b9054eab74ededff4__section_n2h_j3v_hcc"/>

## Internet Connectivity

The transparent proxy handles the HTTP\(s\) communication protocol for Internet destinations. The application developer needs to create a BTP destination of Type “HTTP” and ProxyType “Internet”, for example:

**Internet Destination** 

> ### Sample Code:  
> ```
> {
>     "Name": "example-dest-client-cert",
>     "Type": "HTTP",
>     "ProxyType": "Internet",
>     "URL": <application-url>,
>     "Authentication": "ClientCertificateAuthentication",
>     "KeyStorePassword": <key-store-password>,
>     "KeyStoreLocation": <key-store-location>
> }
> ```

To target the destination with the name “example-dest-client-cert” for handling by the transparent proxy, you should create a [Destination Custom Resource](destination-custom-resource-fc7951e.md) in a namespace of your choice:

> ### Sample Code:  
> ```
> apiVersion: destination.connectivity.api.sap/v1
> kind: Destination 
> metadata:
>   name: example-dest 
> spec:   
>   destinationRef:
>     name: "example-dest-client-cert"
>   destinationServiceInstanceName: <dest-service-instance-name> // can be ommited if config.destinationService.defaultInstanceName is provided
> ```

Once done, the application could start consuming the destination from within the Kubernetes cluster, for example:

> ### Sample Code:  
> ```
> curl example-dest.<destination-cr-namespace>
> ```

> ### Note:  
> `<destination-cr-namespace>` can be omitted if the destination custom resource is created in the same namespace as the application workload.



<a name="loioc5257cf110bf4b7b9054eab74ededff4__section_czp_m3v_hcc"/>

## On-Premise Connectivity

The transparent proxy handles HTTP and TCP communication protocols for on-premise destinations. In order to use the on-premise scenarios, the application developer needs to install a connectivity proxy and integrate it with the transparent proxy. For more information, see [Lifecycle Management](lifecycle-management-60c0a45.md) \(connectivity proxy documentation\).

This happens in the transparent proxy configuration integration section. For example:

> ### Sample Code:  
> ```
> integration:
>   connectivityProxy:
>     serviceName: connectivity-proxy.<connectivity-proxy-namespace>
> ```

> ### Note:  
> To use the Cloud Connector with a specified *Location ID*, you have two options:
> 
> -   Pass the Location ID via the HTTP header "SAP-Connectivity-SCC-Location\_ID"
> -   Use the property "CloudConnectorLocationId" in the referenced SAP BTP destination.
> 
> If both methods are used, the value in the HTTP header will take precedence.
> 
> For non-HTTP SAP BTP destinations, only the "CloudConnectorLocationId" property is supported.

> ### Caution:  
> For installation in Kyma environment using the transparent proxy module, the integration between the transparent proxy and the connectivity proxy is automatic.

Then the application developer needs to create a BTP destination of `ProxyType` “OnPremise”, for example:

> ### Sample Code:  
> ```
> {
>     "Name": "example-dest-on-prem",
>     "Type": "HTTP",
>     "ProxyType": "OnPremise",
>     "URL": <virtual-host>:<port>,
>     "Authentication": "PrincipalPropagation"
> }
> ```

To target the destination with the name “example-dest-onprem” for handling by the transparent proxy, you should create a destination custom resource in a namespace of your choice:

> ### Sample Code:  
> ```
> apiVersion: destination.connectivity.api.sap/v1
> kind: Destination 
> metadata: 
>   name: example-dest
> spec:    
>   destinationRef:
>     name: "example-dest-on-prem"
>   destinationServiceInstanceName: <dest-service-instance-name> // can be ommited if config.destinationService.defaultInstanceName is provided
> ```

Once done, the application could start consuming the destination from within the Kubernetes cluster, for example:

> ### Sample Code:  
> ```
> curl example-dest.<destination-cr-namespace>
> ```

> ### Note:  
> `<destination-cr-namespace>` can be omitted if the destination custom resource is created in the same namespace as the application workload.



<a name="loioc5257cf110bf4b7b9054eab74ededff4__section_ad1_m3v_hcc"/>

## Destination Fragments

Additionally, you can use destination fragments.

For more information, see [Extending Destinations with Fragments](extending-destinations-with-fragments-f56600a.md).

> ### Sample Code:  
> ```
> {
>     "FragmentName": "example-fragment",
>     "URL": <application-url>
> }
> ```

The destination fragment can be referenced in two ways: statically through a [Destination Custom Resource](destination-custom-resource-fc7951e.md), or dynamically by using [Destination Gateway \(Dynamic Lookup of Destinations\)](destination-gateway-dynamic-lookup-of-destinations-6836e00.md).

**Related Information**  


[HTTP Destinations](http-destinations-fd3e2a0.md "Configure HTTP destinations for the transparent proxy for Kubernetes.")

[Mail Destinations](mail-destinations-584bc93.md "Configure Mail destinations for the transparent proxy for Kubernetes.")

[LDAP Destinations](ldap-destinations-47128a8.md "The transparent proxy simplifies access to target systems defined as LDAP destinations. It handles the LDAP protocol for on-premise destinations.")

[TCP Destinations](tcp-destinations-558b39a.md "The transparent proxy simplifies access to target systems defined as TCP destinations. It handles the TCP protocol for on-premise destinations.")

