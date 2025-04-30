<!-- loiof6cb5bc1fac14a899b8457b4bf71bb56 -->

# Connectivity Proxy Integration

Integrate the Transparent Proxy with the Connectivity Proxy for Kubernetes.

The Connectivity Proxy is a Kubernetes component that connects workloads running on a Kubernetes cluster to on-premise systems exposed via the [Cloud Connector](cloud-connector-e6c7616.md). The Transparent Proxy itself doesn’t provide direct connections to on-premise systems, that is, the Connectivity Proxy integration is mandatory for the Transparent Proxy to route to on-premise destinations. To integrate the Transparent Proxy with the Connectivity Proxy, you must:

1.  Install a Connectivity Proxy instance or reuse an existing one. It must be installed in the same Kubernetes cluster where the Transparent Proxy is installed.

    For more information, see [Lifecycle Management](lifecycle-management-60c0a45.md).

2.  Follow the instructions under [Lifecycle Management](lifecycle-management-1c18e0c.md) and set up the `values.yaml` for integrating with the Connectivity Proxy, providing the `config.integration.connectivityProxy.serviceName`.

    For more information, see [Configuration Guide](configuration-guide-2a22cd7.md).

3.  If the Connectivity Proxy runs in multi-region mode, you can link a Transparent Proxy configuration for a Destination service instance with a Connectivity Proxy local region configuration. This can be done at design time by adding an association. Doing this, you won't need to provide the HTTP header `SAP-Connectivity-Region-Configuration-Id` on each request - the Transparent Proxy will automatically pass it to the Connectivity Proxy:

> ### Note:  
> To use the Cloud Connector with a specified *Location ID*, you have two options:
> 
> -   Pass the Location ID via the HTTP header "SAP-Connectivity-SCC-Location\_ID"
> -   Use the property "CloudConnectorLocationId" in the referenced SAP BTP destination.
> 
> If both methods are used, the value in the HTTP header will take precedence.
> 
> For non-HTTP SAP BTP destinations, only the "CloudConnectorLocationId" property is supported.

**Connectivity Proxy Integration**

> ### Sample Code:  
> ```
> config:
>   integration:
>     connectivityProxy:
>       serviceName: <conn-proxy-service-name>.<conn-proxy-service-namespace>
>       connectionTimeoutSeconds: 1
> ```

**Association of a local region of Connectivity Proxy with a Destination service instance in Transparent Proxy** 

> ### Sample Code:  
> ```
> config:
>   integration:
>     destinationService:
>       instances:
>       - name: <local-instance-name>
>         serviceCredentials:
>           secretKey: <secret-key>
>           secretName: <secret-name>
>           secretNamespace: <secret-namespace>
>         associateWith:
>           connectivityProxy:
>             locallyConfiguredRegionId: <locally-configured-conn-proxy-region-id>
> ```

**Related Information**  


[Connectivity Proxy for Kubernetes](connectivity-proxy-for-kubernetes-e661713.md "Use the Connectivity Proxy for Kubernetes to connect workloads on a Kubernetes cluster to on-premise systems.")

