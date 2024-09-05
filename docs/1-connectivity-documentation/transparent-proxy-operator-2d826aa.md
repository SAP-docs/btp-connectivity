<!-- loio2d826aa388524bb8804223b5e2a31968 -->

# Transparent Proxy Operator

Use the transparent proxy operator for the transparent proxy for Kubernetes.

The transparent proxy operator continuously observes the state of the system and the desired state defined by the transparent proxy custom resource. It then makes necessary adjustments to the system \(like creating, updating, or deleting resources\) to achieve the desired state, and regularly monitors the health of the transparent proxy, ensuring it runs optimally according to the configurations defined in the custom resource.



<a name="loio2d826aa388524bb8804223b5e2a31968__section_cgw_jtc_3cc"/>

## Automatic Tracking and Revival of Mandatory Resources

The transparent proxy operator continuously monitors transparent proxy components within the cluster and makes necessary adjustments in order to achieve the desired state.

If a mandatory resource fails or is accidentally deleted, the operator automatically:

-   Detects the missing resource
-   Attempts to revive or recreate the resource based on its last known configuration
-   Ensures the resource is properly integrated back into the cluster

This feature maintains the stability and reliability of essential cluster components without manual intervention.



<a name="loio2d826aa388524bb8804223b5e2a31968__section_p1c_ktc_3cc"/>

## Dependencies

**Traffic Encryption**

The dependencies below are interchangeable and up to your preference:

-   [Istio Service Mesh Integration](istio-service-mesh-integration-f030e5d.md)
-   [Certificate Manager](certificate-manager-6a73ed0.md)

**Destination Service Integration**

If the BTP operator is available in the cluster, a Destinations service instance is created/loaded depending on the setup, automating the configuration. To manually integrate with the Destination service, see [Integration with SAP BTP Connectivity](integration-with-sap-btp-connectivity-aa9fc26.md).

**Automatic Creation of a Destination Service Instance**

If no resources of api version "services.cloud.sap.com/v1" and kind "ServiceInstance" exist in namespace "sap-transp-proxy-system" and no destination service instances are directly specified in the transparent proxy CR, a default, empty destination service instance with name "sap-transp-proxy-default" will be created in namespace "sap-transp-proxy-system" and loaded as destination service instance in the transparent proxy CR.

**Automatic Loading of a Destination Service Instances**

If the service instance and service bindings for a certain Destination service instance are created in the transparent proxy namespace, they will be automatically loaded by the transparent proxy. The transparent proxy will load all resources of api version "services.cloud.sap.com/v1" and kind "ServiceInstance" having "spec.serviceOfferingName: destination", created in namespace "sap-transp-proxy-system", as destination service instances.

