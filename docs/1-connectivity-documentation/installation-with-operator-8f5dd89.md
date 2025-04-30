<!-- loio8f5dd89fb3d349ab81282d0ee33f4f8e -->

# Installation with Operator

Use the operator to install the Transparent Proxy for Kubernetes.



<a name="loio8f5dd89fb3d349ab81282d0ee33f4f8e__section_rcj_qmn_jdc"/>

## Prerequisites

**Integration with Destination Service**

You need an existing Destination service instance so the Transparent Proxy can link to it. If the [SAP BTP Service Operator](https://github.com/SAP/sap-btp-service-operator) is installed in your Kubernetes cluster, the Transparent Proxy will automatically create a Destination service instance in your Kubernetes cluster and link to it.

**Encryption**

Istio injection is enabled by default. If Istio is present in the cluster, traffic between the workloads will be encrypted, making your installation more secure. The communication with the Transparent Proxy will be secure, as well as the communication from the Transparent Proxy to the Connectivity Proxy, if a Connectivity Proxy is present.

If Istio is not present, you should configure encryption with the [cert-manager](https://cert-manager.io/). Check the [Configuration Guide](configuration-guide-2a22cd7.md) to modify the configuration settings according to your setup, for example, referencing your cert-manager `Issuer` or `ClusterIssuer`.



<a name="loio8f5dd89fb3d349ab81282d0ee33f4f8e__section_dxy_ypw_hcc"/>

## Deploy/Upgrade

The Transparent Proxy with [operator](transparent-proxy-operator-2d826aa.md) can be installed/upgraded in any Kubernetes cluster as follows:

Prerequisites:

-   A Kubernetes cluster
-   *kubectl* installed on your machine

The installation will result in Transparent Proxy operator and Transparent Proxy installed with predefined configurations in your Kubernetes cluster. The Transparent Proxy configuration is located in the Transparent Proxy custom resource and can be found in the *sap-transp-proxy-system* namespace after installation. The default configuration is the following:

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
      destinationService:
        defaultInstanceName: ${SERVICE_INSTANCE_NAME}
        instances:
          - name: ${SERVICE_INSTANCE_NAME}
            serviceCredentials:
              secretKey: ${SECRET_KEY}
              secretName: ${SECRET_NAME}
              secretNamespace: ${SECRET_NAMESPACE}
      serviceMesh:
        istio:
          istio-injection: enabled
```

**Deploy/Upgrade Using the SAP BTP Service Operator**

This operation creates *service instance* and *service binding* custom resources in the *sap-transp-proxy-system* namespace, resulting in a destination service instance created in SAP BTP. This destination service instance is loaded in the Transparent Proxy configuration with name *sap-transp-proxy-default*.

> ### Note:  
> To upgrade to a newer version, run the same command in a Kubernetes cluster where you have already used this script to install the Transparent Proxy.

> ### Note:  
> The upgrade operation will only upgrade to the newer version of the Transparent Proxy deployments without creating an additional destination service instance or changing configurations.

Prerequisites:

-   [SAP BTP Service Operator](https://github.com/SAP/sap-btp-service-operator) set up in your Kubernetes cluster

```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/sap-software/btp-transparent-proxy/refs/heads/main/deploy.sh)"
```

**Deploy/Upgrade Using a Destination Service Instance Key in Plain JSON Format**

The automation script creates a Kubernetes secret containing the service instance and loads it into the Transparent Proxy configuration.

> ### Note:  
> To upgrade, run the same command in a Kubernetes cluster where you have already used this script to install the Transparent Proxy.

> ### Note:  
> The upgrade operation will update the Transparent Proxy to the latest version. If you select the name of an existing destination service instance configuration during this process, that configuration will be updated. All other configurations will remain unchanged.

Prerequisites:

-   Destination service instance created

```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/sap-software/btp-transparent-proxy/refs/heads/main/deploy.sh)" -- --destination-service-instance-name <value> --destination-service-key '{...}'
```

Before executing the script, ensure you have the necessary values ready to replace the placeholders in the command. The following table explains each argument you'll need to provide:


<table>
<tr>
<th valign="top">

Argument

</th>
<th valign="top">

Description

</th>
<th valign="top">

Required

</th>
</tr>
<tr>
<td valign="top">

\--destination-service-instance-name \(-dsin\)

</td>
<td valign="top">

The local name of the Destination service instance present in the Transparent Proxy configuration. It can be later used to reference it in destination custom resources.

</td>
<td valign="top">

True

</td>
</tr>
<tr>
<td valign="top">

\--destination-service-key \(-dsk\)

</td>
<td valign="top">

The service instance key obtained from the destination service instance.

</td>
<td valign="top">

True

</td>
</tr>
</table>

**Deploy/Upgrade Using a Kubernetes Secret Holding a Destination Service Instance Key**

The automation script loads the Kubernetes secret into the Transparent Proxy configuration.

> ### Note:  
> To upgrade, run the same command in a Kubernetes cluster where you have already used this script to install the Transparent Proxy.

> ### Note:  
> The upgrade operation will update the Transparent Proxy to the latest version. If you select the name of an existing destination service instance configuration during this process, that configuration will be updated. All other configurations will remain unchanged.

Prerequisites:

-   A Kubernetes secret in your cluster that holds a destination service instance key

```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/sap-software/btp-transparent-proxy/refs/heads/main/deploy.sh)" -- --destination-service-instance-name <value> --destination-service-secret-name <secret-name> --destination-service-secret-key <secret-key> --destination-service-secret-namespace <namespace>
```

Before executing the script, ensure you have the necessary values ready to replace the placeholders in the command. The following table explains each argument you'll need to provide:


<table>
<tr>
<th valign="top">

Argument

</th>
<th valign="top">

Description

</th>
<th valign="top">

Required

</th>
</tr>
<tr>
<td valign="top">

\--destination-service-instance-name \(-dsin\)

</td>
<td valign="top">

The local name of the Destination service instance present in the Transparent Proxy configuration. It can be later used to reference it in destination custom resources.

> ### Note:  
> If not specified, the script uses the name of the Kubernetes secret.



</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

\--destination-service-secret-name \(-dssn\)

</td>
<td valign="top">

The name of the existing secret, which holds the credentials for the Destination service.

</td>
<td valign="top">

True

</td>
</tr>
<tr>
<td valign="top">

\--destination-service-secret-key \(-dssk\)

</td>
<td valign="top">

The key in the Destination service secret resource, which holds the base64-encoded value of the destination service key.

</td>
<td valign="top">

True

</td>
</tr>
<tr>
<td valign="top">

\--destination-service-secret-namespace \(-dssn\)

</td>
<td valign="top">

The namespace of the existing secret to be used, which holds the credentials for the Destination service.

</td>
<td valign="top">

True

</td>
</tr>
</table>



<a name="loio8f5dd89fb3d349ab81282d0ee33f4f8e__section_sy1_zpw_hcc"/>

## Undeploy

To undeploy the Transparent Proxy and its operator, run:

```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/sap-software/btp-transparent-proxy/refs/heads/main/undeploy.sh)"
```

> ### Caution:  
> This action will delete all Transparent Proxy resources and instances that were previously created by the script or the operator.



<a name="loio8f5dd89fb3d349ab81282d0ee33f4f8e__section_jfs_ypw_hcc"/>

## Troubleshooting

In case of issues, refer to [Transparent Proxy Custom Resource Conditions](transparent-proxy-custom-resource-conditions-d75e31e.md).

