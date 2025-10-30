<!-- loio6836e007ebb24954b727f1524837f741 -->

# Destination Gateway \(Dynamic Lookup of Destinations\)

Create a single custom resource to look up one ore more destinations dynamically with the Transparent Proxy for Kubernetes.

The Transparent Proxy lets you perform a dynamic lookup of one or multiple destinations from a destination service instance and its tenants. To consume a destination in that way, you only have to create a single custom resource.

**Example: Destination Custom Resource**

```
apiVersion: destination.connectivity.api.sap/v1
kind: Destination
metadata:
  name: destination-gateway
spec:
  destinationRef:
    name: "*"
  destinationServiceInstanceName: <destination-service-instance-local-name> //not mandatory
```

In the example above, a destination custom resource has `spec.destinationRef.name = "*"`, which indicates that this destination would accept dynamic lookup and only a single Kubernetes service will be created with name `dynamic-destination` which works as an entry point for all destinations from `destinationServiceInstanceName` with `name: dest-service-instance`.

The Transparent Proxy identifies the destination for which a request should be configured and dispatched by obtaining the destination name \(destination identifier\) from a custom header called `X-Destination-Name`.

> ### Note:  
> This header is specifically intended to identify a destination within a Destination service instance and its tenants.

The destination can be combined with a fragment by optionally providing a custom header called `X-Fragment-Name`. You can choose whether the fragment is optional or mandatory by passing the `X-Fragment-Optional` header, which accepts values `true` or `false`.

If `X-Fragment-Optional=true` and the referenced fragment exists, the destination and fragment are combined. If the referenced fragment does not exist, the base destination is used. Conversely, if `X-Fragment-Optional=false` and the referenced fragment exists, the destination and fragment are combined. If the referenced fragment does not exist, an error is returned.

**Example Destination:**

```
{
    "Name": "example-dest",
    "Type": "HTTP",
    "ProxyType": "Internet",
    "URL": "<application-url>",
    "Authentication": "ClientCertificateAuthentication",
    "KeyStorePassword": "<key-store-password>",
    "KeyStoreLocation": "<key-store-location>"
}
```

**Example Fragment:**

```
{
    "FragmentName": "example-fragment",
    "URL": "<another-application-url>"
}
```

If you want to call the `example-dest` destination through the Kubernetes service named `destination-gateway`, you can execute the command below:

**Dynamic Lookup of Destinations - Bash Snippet** 

```
curl destination-gateway.<destination-cr-namespace> -H "X-Destination-Name: example-dest"

```

If you want to consume `example-dest` destination with path and query parameters through the Kubernetes service named `destination-gateway`, you can execute the command below:

**Dynamic Lookup of Destinations with Path and Query Parameters - Bash Snippet**

```
curl destination-gateway.<destination-cr-namespace>/<param-1>/<param-2>/<param-3>?<key-1>=<value-1>&<key-2>=<value-2> -H "X-Destination-Name: example-dest"
```

If you want to call `example-dest` destination, enriching it with the properties from fragment `example-fragment` through the Kubernetes service named `dynamic-destination`, you can execute the command below:

**Dynamic Lookup of Destinations with Fragment - Bash Snippet**

```
curl destination-gateway.<destination-cr-namespace> -H "X-Destination-Name: example-dest" -H "X-Fragment-Name: example-fragment"
```

If you want to call `example-dest` destination, enriching it with the properties from fragment `example-fragment` through the Kubernetes service named `destination-gateway` and specify that the fragment is optional, you can execute the command below:

**Dynamic Lookup of Destinations with Fragment \(Optional\) - Bash Snippet** 

```
curl destination-gateway.<destination-cr-namespace> -H "X-Destination-Name: example-dest" -H "X-Fragment-Name: example-fragment" -H "X-Fragment-Optional: true"

```













If you want to call `example-dest` destination, enriching it with destination chaining properties through the Kubernetes service named `destination-gateway`, you can execute the command below:

**Dynamic Lookup of Destinations Using Destination Chaining- Bash Snippet**

```
curl destination-gateway.<destination-cr-namespace> -H "X-Destination-Name: example-dest" -H "X-Chain-Name: <chain-name>" -H "X-Chain-Var-key1: <val1>" -H "X-Chain-Var-key2: <val2>" // and etc for each x-chan-var header
```

If you want to call `example-dest` destination, enriching it with the properties from fragment `example-fragment` through the Kubernetes service named `destination-gateway` and specify that the fragment is not optional, you can execute the command below:

**Dynamic Lookup of Destinations with Fragment \(Not Optional\) - Bash Snippet**

```
curl destination-gateway.<destination-cr-namespace> -H "X-Destination-Name: example-dest" -H "X-Fragment-Name: example-fragment" -H "X-Fragment-Optional: false"
```

