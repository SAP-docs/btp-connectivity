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



## Connectivity Proxy in Untrusted Mode

The Connectivity Proxy can be configured to require authentication on every incoming request. To do so, configure the following flags on the Connectivity Proxy CR in Kyma, or in the Connectivity Proxy Helm values when deployed on any other Kubernetes cluster:

-   `config.servers.proxy.http.enableProxyAuthorization`: when `true`, the Transparent Proxy automatically mints a Bearer token for the provider subaccount and injects it on every outbound HTTP request to the Connectivity Proxy.
-   `config.servers.proxy.socks5.enableProxyAuthorization`: when `true`, the Transparent Proxy automatically mints a Bearer token for the provider subaccount and uses it for SOCKS5 authentication on every outbound TCP request to the Connectivity Proxy.

-   `config.servers.proxy.rfcAndLdap.enableProxyAuthorization`: when `true`, the Transparent Proxy automatically mints a Bearer token for the provider subaccount and includes it in the LDAP/RFC handshake to the Connectivity Proxy.


The flags can be changed at runtime without restarting the Transparent Proxy. The new value propagates to all Transparent Proxy pods within a few seconds.

**Prerequisite: `allowedClientIds`**

Before enabling any of these flags, you *must* add the Transparent Proxy's `client_id` to the Connectivity Proxy's allowlist. Otherwise, the Connectivity Proxy rejects every Transparent Proxy request and all on-premise traffic fails. The Transparent Proxy `client_id` is the *provider subaccount `client_id` of the Connectivity Proxy instance* used by the Transparent Proxy.

The allowlist is stored in the `connectivity-proxy-region-configurations` Secret in the Connectivity Proxy namespace, under `allowedClientIds`. The exact path depends on whether the Connectivity Proxy is configured in *multi-region* or *single-region* mode. Each region has its own `allowedClientIds` list, so you must add the provider subaccount `client_id` to every region to which the Transparent Proxy can route:

**Example: Allowed Client IDs in Multi-Region Mode**

> ### Sample Code:  
> ```
>  {
> 
>     "default": {
> 
>       "allowedClientIds": ["<provider-subaccount-client-id>"],
> 
>       "dependencies": { ... }
> 
>     },
> 
>     "eu10": {
> 
>       "allowedClientIds": ["<provider-subaccount-client-id>"],
> 
>       "dependencies": { ... }
> 
>     }
> 
>   } 
> ```

In *single-region* mode, the JSON has a flat top-level structure \(no region keys\). In this case, add the provider subaccount `client_id` to the single top-level `allowedClientIds` list:

**Example: Allowed Client IDs in Single-Region Mode**

> ### Sample Code:  
> ```
>  {
> 
>     "allowedClientIds": ["<provider-subaccount-client-id>"],
> 
>     "dependencies": { ... }
> 
>   } 
> ```

After updating the Secret, restart the Connectivity Proxy *StatefulSet* to make it pick up the new allowlist.

**HTTP: customer-supplied authorization \(optional\)**

If your application already has a Connectivity Proxy-compatible Bearer token, it can supply it explicitly with the header `connectivity-proxy-authorization`: Bearer <jwt\>.

The Transparent Proxy honors this value and forwards it to the Connectivity Proxy. If the header is absent, the Transparent Proxy automatically mints a token as described above. The header name avoids a collision with the application's use of the standard `Proxy-Authorization` header.

**Related Information**  


[Connectivity Proxy for Kubernetes](connectivity-proxy-for-kubernetes-e661713.md "Use the Connectivity Proxy for Kubernetes to connect workloads on a Kubernetes cluster to on-premise systems.")

