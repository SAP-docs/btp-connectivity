<!-- loiofc7951e80cb0423ebc0d35e3443c32dc -->

# Destination Custom Resource

A destination custom resource represents an SAP BTP destination from the Destination service that can be used by the transparent proxy.

For each destination custom resource, the transparent proxy creates two [Kubernetes Services](https://kubernetes.io/docs/concepts/services-networking/service/): one in the transparent proxy's installation namespace and the other in the destination custom resource's namespace. Both services can be used to access the destination.

> ### Note:  
> We recommend that you create the destination custom resource in the same namespace as the application workload. By doing so, you can access the destination without specifying the namespace in the URL.



<a name="loiofc7951e80cb0423ebc0d35e3443c32dc__section_mky_zmc_3cc"/>

## Prerequisites

To target the destination with the name “example-dest” for handling by the transparent proxy, you should create the following Kubernetes resource in a namespace of your choice:

> ### Sample Code:  
> ```
> apiVersion: destination.connectivity.api.sap/v1
> kind: Destination
> metadata:
>   name: <destination-cr-name>
> spec:  
>   destinationRef:
>     name: <destination-name>
>   destinationServiceInstanceName: dest-service-instance-example // can be ommited if config.destinationService.defaultInstanceName is provided
> ```

**Destination Fragments**

You can reference a fragment as follows:

-   Directly in the destination custom resource:

    **Destination CR with Static Reference to a Destination Fragment** 

    > ### Sample Code:  
    > ```
    > apiVersion: destination.connectivity.api.sap/v1
    > kind: Destination
    > metadata:
    >   name: <destination-cr-name>
    > spec:  
    >   destinationRef:
    >     name: <destination-name>
    >   fragmentRef:
    >     name: <fragment-name>
    >   destinationServiceInstanceName: <dest-service-instance-name> // can be ommited if config.destinationService.defaultInstanceName is provided
    > ```

    > ### Caution:  
    > Static reference of a fragment is only applicable for a destination custom resource that references a particular destination. The [Dynamic Lookup of Destinations](destination-gateway-dynamic-lookup-of-destinations-6836e00.md) feature is not compatible with this approach.

-   Dynamically passing a fragment as an HTTP header is only compatible with the [Dynamic Lookup of Destinations](destination-gateway-dynamic-lookup-of-destinations-6836e00.md) approach. You can check the examples given there.

The transparent proxy monitors the available *destinations.destination.connectivity.api.sap* Kubernetes resources. Once a new SAP BTP destination is created for which *destinations.destination.connectivity.api.sap* resource exists, the transparent proxy changes its configuration.

After the transparent proxy executes successfully all necessary operations, the status of the *destinations.destination.connectivity.api.sap* Kubernetes resource will be updated as follows and the DNS record <destination-cr-name\> will route to the configured URL in the destination:

> ### Sample Code:  
> ```
> apiVersion: destination.connectivity.api.sap/v1
> kind: Destination
> metadata:
>   name: <destination-cr-name>
> spec: 
>   destinationRef:
>     name: <destination-name>
>   fragmentRef:
>     name: <fragment-name>  
> destinationServiceInstanceName: <dest-service-instance-name> // can be ommited if config.destinationService.defaultInstanceName is provided
> status:
>   conditions:
>   - lastUpdateTime: "2022-09-28T07:26:46Z"
>     message: Transparent Proxy is configured and Kubernetes service with name "example-dest" is created.
>     reason: ConfigurationSuccessful
>     status: "True"
>     type: Available
> ```

**Configure a Custom Service Port**

In the destination custom resource spec you can describe on which port you would like to consume your destination:

> ### Sample Code:  
> ```
> apiVersion: destination.connectivity.api.sap/v1
> kind: Destination
> metadata:
>   name: <destination-cr-name>
> spec:  
>   destinationRef:
>     name: <destination-name>
>   destinationServiceInstanceName: <dest-service-instance-name> // can be ommited if config.destinationService.defaultInstanceName is provided
>   service:
>     port: <service-port>
> ```



<a name="loiofc7951e80cb0423ebc0d35e3443c32dc__section_sss_zmc_3cc"/>

## Consumption

Once done, the application can start consuming the destination from within the Kubernetes cluster.

> ### Note:  
> `<destination-cr-namespace>` can be omitted if the destination custom resource is created in the same namespace as the application workload.

**Example without Additional Parameters**

> ### Sample Code:  
> ```
> curl <destination-cr-name>.<destination-cr-namespace>
> ```

**Example with Path Parameters**

> ### Sample Code:  
> ```
> curl <destination-cr-name>.<destination-cr-namespace>/<param-1>/<param-2>/<param-3>
> ```

**Example with Path and Query Parameters**

> ### Sample Code:  
> ```
> curl <destination-cr-name>.<destination-cr-namespace>/<param-1>/<param-2>/<param-3>?<key-1>=<value-1>&<key-2>=<value-2>
> ```

**Example with Custom Service Port**

> ### Sample Code:  
> ```
> curl <destination-cr-name>.<destination-cr-namespace>:<custom-service-port>
> ```

**Related Information**  


[Restrict Access Using Scoping](restrict-access-using-scoping-bd47cbe.md "Define the access control scope of the destination custom resources for the transparent proxy for Kubernetes.")

