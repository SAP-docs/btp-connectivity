<!-- loiod75e31ed734f48249c601e8fda3d578d -->

# Transparent Proxy Custom Resource Conditions

When installing the Transparent Proxy via the Transparent Proxy Operator or adding the Transparent Proxy module in Kyma environment, a Transparent Proxy custom resource is created in the 'sap-transp-proxy-system' namespace. In this custom resource, one can define the configuration for the Transparent Proxy and also receive information in the status conditions whether the installation is successful or not. If the installation is not successful, use the table below to find a solution for your problem.



Common Issues and Solutions

For custom resources having Warning state refer to this table with issue/solution to the particular misconfiguration.

Check the Configuration guide after identifying your misconfiguration in the transparent proxy custom resource conditions.


<table>
<tr>
<th valign="top">

Custom Resource Condition Messages

</th>
<th valign="top">

Solution

</th>
</tr>
<tr>
<td valign="top">

An error occurred because certain necessary configuration settings are missing. Ensure that either 'config.security.communication.internal.encryptionEnabled' or 'config.integration.serviceMesh.istio.istio-integration' is provided.

</td>
<td valign="top">

It is mandatory to integrate either with Istio or cert-manager. This is done by configuring at least one of the two properties: config.integration.serviceMesh.istio.istio-integration and config.security.communication.internal.encryptionEnabled. config.integration.serviceMesh.istio.istio-integration makes config.security.communication.internal.encryptionEnabled optional. If "encryptionEnabled" is set to true and config.integration.serviceMesh.istio.istio-integration is missing then config.security.communication.internalCommunication.certManager.issuerRef.name and config.security.communication.internalCommunication.certManager.issuerRef.kind have to be provided.

</td>
</tr>
<tr>
<td valign="top">

Custom Resource with name "<name\>" already exists in this namespace.

</td>
<td valign="top">

There could be only 1 Transparent Proxy Custom resource in a single namespace. Delete the unnecessary custom resource or move it to another namespace.

</td>
</tr>
<tr>
<td valign="top">

When config.security.communication.internal.encryptionEnabled is true, config.security.communication.internal.certManager.issuerRef.name cannot be empty

</td>
<td valign="top">

If config.security.communication.internalCommunication.encryptionEnabled is set to true then config.security.communication.internal.certManager.issuerRef.name cannot be empty.

</td>
</tr>
<tr>
<td valign="top">

config.security.communication.internal.certManager.issuerRef.namespace and config.security.communication.internal.certManager.issuerRef.kind are both passed. Use config.security.communication.internal.certManager.issuerRef.kind when your issuer is of type cert-manager.io and config.security.communication.internal.certManager.issuerRef.namespace when your issuer is of type cert.gardener.cloud

</td>
<td valign="top">

If config.security.communication.internalCommunication.encryptionEnabled is set to true, you must pass either config.security.communication.internal.certManager.issuerRef.kind or config.security.communication.internal.certManager.issuerRef.namespace, not both.

</td>
</tr>
<tr>
<td valign="top">

Neither config.security.communication.internal.certManager.issuerRef.namespace or config.security.communication.internal.certManager.issuerRef.kind is passed. Use config.security.communication.internal.certManager.issuerRef.kind when your issuer is of type cert-manager.io and config.security.communication.internal.certManager.issuerRef.namespace when your issuer is of type cert.gardener.cloud.

</td>
<td valign="top">

If config.security.communication.internalCommunication.encryptionEnabled is set to true, you must pass either config.security.communication.internal.certManager.issuerRef.kind or config.security.communication.internal.certManager.issuerRef.namespace, both cannot be empty.

</td>
</tr>
<tr>
<td valign="top">

"certificates.cert-manager.io" custom resource definition not found.

</td>
<td valign="top">

If config.security.communication.internalCommunication.encryptionEnabled is set to true and config.security.communication.internalCommunication.certManager.issuerRef.kind is not empty then cert-manager-io has to be installed in the cluster.

</td>
</tr>
<tr>
<td valign="top">

"certificates.cert.gardener.cloud" custom resource definition not found.

</td>
<td valign="top">

If config.security.communication.internalCommunication.encryptionEnabled is set to true and config.security.communication.internalCommunication.certManager.issuerRef.namespace is not empty then cert-manager-gardener has to be installed in the cluster.

</td>
</tr>
<tr>
<td valign="top">

Resource with apiVersion cert-manager.io/v1 and kind "<Issuer|ClusterIssuer\>" with name "<name\>" not found.

</td>
<td valign="top">

The referenced Issuer or ClusterIssuer with apiVersion cert-manager.io/v1 is not found in the cluster. In case it is of type Issuer check the transparent proxy namespace and name. For ClusterIssuer check the name.

</td>
</tr>
<tr>
<td valign="top">

Resource with apiVersion cert.gardener.cloud/v1alpha1 and kind Issuer in namespace "<namespace\>" with name "<name\>" not found.

</td>
<td valign="top">

The referenced Issuer with apiVersion cert.gardener.cloud/v1alpha1 is not found. Check the specified namespace to see if the resource exists.

</td>
</tr>
<tr>
<td valign="top">

Provide at least one Destination service instance in config.integration.destinationServiceIntegration.instances, or create and bind an instance in the sap-transp-proxy-system namespace using the SAP BTP Service Operator.

</td>
<td valign="top">

The Transparent Proxy should have at least one destination service instance configured in config.integration.destinationServiceIntegration.instances or resources of api version "services.cloud.sap.com/v1" and kind "ServiceInstance" should exist in "sap-transp-proxy-system" namespace.

</td>
</tr>
<tr>
<td valign="top">

Destination service instance name should be provided.

</td>
<td valign="top">

Some of the entries in config.integration.destinationService.instances does not have name specified.

</td>
</tr>
<tr>
<td valign="top">

secretName should be provided for destination service instance: "<name\>".

</td>
<td valign="top">

The given destination service instance should have valid reference to a secret holding the service credentials for consuming the Destination Service.

</td>
</tr>
<tr>
<td valign="top">

Secret with name "<name\>" not found in namespace: "<namespace\>".

</td>
<td valign="top">

The provided secret cannot be found in the referenced namespace.

Examples:

-   The referenced secret holding the service credentials for the Destination Service is not found for the referenced destination service instance. Check the secretName and secretNamespace properties provided in the serviceCredentials section for the given instance in config.integration.destinationService.instances.

-   The referenced secret holding the service credentials for the Connectivity Proxy is not found. Check the secretName and secretNamespace properties provided in the serviceCredentials section for the given instance in config.integration.connectivityProxy.serviceCredentials.



</td>
</tr>
<tr>
<td valign="top">

secretName should be provided for connectivity proxy service instance in shared mode.

</td>
<td valign="top">

config.integration.connectivityProxy.serviceCredentials.secretName should be provided when config.integration.connectivityProxy.serviceName is not blank and connectivity proxy referenced by config.integration.connectivityProxy.serviceName is in shared mode.

</td>
</tr>
<tr>
<td valign="top">

configMap "connectivity-proxy" not found in namespace "<namespace\>".

</td>
<td valign="top">

The given config map is not present in the same namespace as the service defined in config.integration.connectivityProxy.serviceName. If the service name contains a namespace the config map should be in that namespace otherwise it should be in the same namespace as the Transparent Proxy CR.

</td>
</tr>
<tr>
<td valign="top">

Key "connectivity-proxy-config.yml" not found in configMap\`s Data from configMap: "connectivity-proxy" in namespace "<namespace\>".

</td>
<td valign="top">

The referenced config map does not contain the expected "connectivity-proxy-config.yml" Data key.

</td>
</tr>
<tr>
<td valign="top">

Connectivity Proxy tenant mode "<tenant\_mode\>" is not compatible with Transparent Proxy tenant mode "<tenant\_mode\>".

</td>
<td valign="top">

The tenant mode defined in the Connectivity Proxy\`s configmap is different from the one defined in config.tenantMode of the Transparent Proxy CR. The tenant modes of the Connectivity Proxy and Transparent Proxy must be equal \(shared & shared or dedicated & dedicated\).

</td>
</tr>
<tr>
<td valign="top">

Istio not installed on the cluster. Revise your Istio integration configuration.

</td>
<td valign="top">

The configuration for integration in Istio service mesh is provided but Istio is not installed on the cluster. Either install Istio on the cluster or remove the configuration for integration in Istio service mesh.

</td>
</tr>
</table>

