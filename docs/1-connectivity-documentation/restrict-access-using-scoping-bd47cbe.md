<!-- loiobd47cbece15b4dd6aefbd5c53ff27371 -->

# Restrict Access Using Scoping

Define the access control scope of the destination custom resources for the transparent proxy for Kubernetes.

The scoping of access to destinations exposed via *destination custom resources* \(destination CRs\) is based on the *network policies* concept in Kubernetes.



<a name="loiobd47cbece15b4dd6aefbd5c53ff27371__section_qcc_vm2_vwb"/>

## Prerequisites

Network policies are implemented by a CNI Plugin. To apply network policies, you must use a networking solution that supports the *NetworkPolicy* Kubernetes resource.

> ### Note:  
> Creating a *NetworkPolicy* resource without having a corresponding controller running in the cluster, will have **no effect**. In this case, access scoping will not work.
> 
> For more information, see [Network Policies](https://kubernetes.io/docs/concepts/services-networking/network-policies/).



<a name="loiobd47cbece15b4dd6aefbd5c53ff27371__section_uss_5m2_vwb"/>

## Procedure

**Global Configuration**

You can set a default scope on all destination custom resources by setting `.Values.config.security.accessControl.destinations.defaultScope` in the `values.yaml` file.

-   If .`Values.config.security.accessControl.destinations.defaultScope` is set to `namespaced`, the destinations exposed via destination custom resources that were created in a namespace, are accessible only by the applications running in this namespace of the destination custom resource.
-   If `.Values.config.security.accessControl.destinations.defaultScope` is set to `clusterWide`, the destinations exposed via destination custom resources are accessible from any namespace in the cluster.
-   The default value is `namespaced`.

**Destination CR Configuration**

You can also optionally set scope for the destination CR directly, which will override the global setting from the values.yaml. for that particular CR only.

```
apiVersion: destination.connectivity.api.sap/v1
kind: Destination
metadata:
  name: <destination-cr-name>
spec: 
  destinationRef:
    name: <destination-name>
  accessControl:
    scope: "namespaced|clusterWide"
```

