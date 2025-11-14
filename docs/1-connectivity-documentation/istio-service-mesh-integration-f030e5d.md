<!-- loiof030e5df081c4c7e8299d2d2ae6a7524 -->

# Istio Service Mesh Integration

Transparent Proxy supports integration with the Istio service mesh for mTLS communication between the Transparent Proxy components.



<a name="loiof030e5df081c4c7e8299d2d2ae6a7524__section_g3p_4sw_hcc"/>

## Prerequisites

Before proceeding with the integration, it is crucial to ensure that Istio is installed on your cluster, as it is a mandatory requirement. If you are operating within a Kyma environment, Istio can be automatically installed by adding the Istio module.

> ### Caution:  
> Transparent proxy will not check whether Istio is working properly.



<a name="loiof030e5df081c4c7e8299d2d2ae6a7524__section_p5h_4sw_hcc"/>

## Integration

To integrate the Transparent Proxy with the Istio mesh, you need to enable the 'istio-injection' setting in the Transparent Proxy configuration.

**Example Istio Integration** 

> ### Sample Code:  
> ```
> config:
>     integration:
>         ## Integration with service mesh. Currently, only Istio service mesh is supported. The only acceptable value is 'enabled'. If it is set, the Transparent Proxy components will be   integrated in the mesh, otherwise they will be exclusively removed from the mesh.
>         serviceMesh:
>         istio:
>             istio-injection: enabled
> ```

If `.Values.config.security.communication.internal.encryptionEnabled` is set to `true`, the Transparent Proxy is configured to integrate in the Istio service mesh and Istio is present on the cluster, integration with the certificate manager becomes optional, otherwise it is mandatory. It is possible to have both integration with Istio service mesh as well as with the certificate manager.

> ### Note:  
> If Transparent Proxy operator is available and `.Values.config.security.communication.internal.encryptionEnabled` is set to `false` but there is integration in the Istio service mesh, the Transparent Proxy CR will become in "Ready" state with message "installation is ready. Although encryptionEnabled is set to false, the traffic will be encrypted by Istio.".

> ### Note:  
> If you have set `config.metrics.prometheus.enabled` to `true`, depending on how Istio is configured it might be required to include Prometheus pods also in the Istio service mesh.

> ### Note:  
> For more details about configuring the Transparent Proxy, check the [Configuration Guide](configuration-guide-2a22cd7.md).

