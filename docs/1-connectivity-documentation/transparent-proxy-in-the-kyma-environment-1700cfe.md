<!-- loio1700cfe070704d2e80aa76de1033a6c4 -->

# Transparent Proxy in the Kyma Environment

Use the transparent proxy in the Kyma environment.

This documentation serves as a reference for adding the transparent proxy in the Kyma environment and the respective transparent proxy operator, integrated with [Kyma's Lifecycle Manager](https://github.com/kyma-project/lifecycle-manager).

The transparent proxy operator continuously observes the state of the system and the desired state defined by the transparent proxy custom resource. It then makes necessary adjustments to the system \(like creating, updating, or deleting resources\) to achieve the desired state, and regularly monitors the health of the transparent proxy, ensuring it runs optimally according to the configurations defined in the custom resource.



<a name="loio1700cfe070704d2e80aa76de1033a6c4__section_tpm_wxc_zxb"/>

## Add the Module

To add the module, refer to [Add and Delete a Kyma module](https://help.sap.com/docs/btp/sap-business-technology-platform/enable-and-disable-kyma-module#loio1b548e9ad4744b978b8b595288b0cb5c).

With the enablement of the transparent proxy module, a default transparent proxy custom resource is created in the **sap-transp-proxy-system** namespace.

> ### Caution:  
> The **sap-transp-proxy-system** namespace is intended for the monitoring of the transparent proxy resources, do not use it for deploying workloads there.

The default transparent proxy custom resource is defined like this:

```
apiVersion: operator.kyma-project.io/v1alpha1
kind: TransparentProxy
metadata:
  name: transparent-proxy
  namespace: sap-transp-proxy-system
spec:
  config:
    security:
      communication:
        internal:
          encryptionEnabled: true
    integration:
      serviceMesh:
        istio:
          istio-injection: enabled
```

You can update it to meet your requirements. To do this, either use *kubectl edit* or create a YAML file containing the transparent proxy custom resource and edit the spec section with values according to the [Configuration Guide](configuration-guide-2a22cd7.md).

> ### Sample Code:  
> ```
> kubectl apply -f <fileName> -n sap-transp-proxy-system
> 
> ```

If you want to create a second instance of the transparent proxy, you can create a transparent proxy custom resource in another namespace.



<a name="loio1700cfe070704d2e80aa76de1033a6c4__section_zk4_4gm_zyb"/>

## Dependencies

**Service Mesh Configuration**

The transparent proxy supports integration with the Istio service mesh \(for more information, see [Configuration Guide](configuration-guide-2a22cd7.md)\).

If the transparent proxy is configured to integrate in the *Istio mesh* and Istio is present on the cluster, the integration with the *certificate manager* becomes optional, otherwise it is mandatory.

If `encryptionEnabled` is set to "false", but there is integration in the *Istio service mesh*, the transparent proxy custom resource will assume the state "Ready" with message *"installation is ready. Although encryptionEnabled is set to false, the traffic will be encrypted by Istio."*. You can use both, integration with *Istio service mesh* and with the *certificate manager*.

**Encryption between Micro Components**

If you don't integrate the transparent proxy with a service mesh, you must encrypt the traffic between the micro components. To do that, set `encryptionEnabled` to `true`. This property configures encryption between the transparent proxy micro components internally. Additionally, you should provide the necessary *certificate manager* configuration to make sure encryption works as expected.

For more information, see [Configuration Guide](configuration-guide-2a22cd7.md).

**Destination Service Instance**

The transparent proxy will load all resources of api version *services.cloud.sap.com/v1* and kind `ServiceInstance` having `spec.serviceOfferingName: destination`, created in namespace `sap-transp-proxy-system`, as destination service instances. In addition, you can configure more destination service instances directly in the transparent proxy custom resource.

For more information, see the [Configuration Guide](configuration-guide-2a22cd7.md).

If no resources of api version *services.cloud.sap.com/v1* and kind `ServiceInstance` exist in namespace `sap-transp-proxy-system`, and no destination service instances are directly specified in the transparent proxy custom resource, a default, empty destination service instance with name `sap-transp-proxy-default` will be created in namespace `sap-transp-proxy-system` and loaded as destination service instance in the transparent proxy custom resource.



<a name="loio1700cfe070704d2e80aa76de1033a6c4__TransparentProxyinKymaenvironment-Encryptionbetweenmicro-components"/>

## Troubleshooting

In case of issues, please refer to [Troubleshooting in Kyma](troubleshooting-in-kyma-aebcc82.md).

