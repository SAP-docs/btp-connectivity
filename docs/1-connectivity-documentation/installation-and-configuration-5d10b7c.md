<!-- loio5d10b7cc0c6b48639899c3469b9eb959 -->

# Installation and Configuration

Find troubleshooting information for installation and configuration of the transparent proxy for Kubernetes.


<table>
<tr>
<th valign="top">

Installation Issue

</th>
<th valign="top">

Possible Solution

</th>
</tr>
<tr>
<td valign="top">

Applying helm configuration fails with "When .Values.config.security.communication.internal.encryptionEnabled is true, .Values.config.security.communication.internal.certManager.issuerRef.name cannot be empty".

</td>
<td valign="top">

Set value to .Values.config.security.communication.internal.certManager.issuerRef.name when .Values.config.security.communication.internal.encryptionEnabled is true.

</td>
</tr>
<tr>
<td valign="top">

Applying helm configuration fails with ".Values.config.security.communication.internal.certManager.issuerRef.namespace and .Values.config.security.communication.internal.certManager.issuerRef.kind are both passed. Use .Values.config.security.communication.internal.certManager.issuerRef.kind when your issuer is of type cert-manager.io and .Values.config.security.communication.internal.certManager.issuerRef.namespace when your issuer is of type cert.gardener.cloud".

</td>
<td valign="top">

Pass either .Values.config.security.communication.internal.certManager.issuerRef.kind or .Values.config.security.communication.internal.certManager.issuerRef.namespace, not both, when .Values.config.security.communication.internal.encryptionEnabled is true.

</td>
</tr>
<tr>
<td valign="top">

Applying helm configuration fails with "Neither .Values.config.security.communication.internal.certManager.issuerRef.namespace or .Values.config.security.communication.internal.certManager.issuerRef.kind is passed. Use .Values.config.security.communication.internal.certManager.issuerRef.kind when your issuer is of type cert-manager.io and .Values.config.security.communication.internal.certManager.issuerRef.namespace when your issuer is of type cert.gardener.cloud".

</td>
<td valign="top">

One of .Values.config.security.communication.internal.certManager.issuerRef.kind and .Values.config.security.communication.internal.certManager.issuerRef.namespace is required when .Values.config.security.communication.internal.encryptionEnabled is true.

</td>
</tr>
<tr>
<td valign="top">

Applying helm configuration fails with "Issuer of version cert.gardener.cloud/v1alpha1 with name 'test' in namespace 'test' not found".

</td>
<td valign="top">

Make sure that Issuer of version cert.gardener.cloud/v1alpha1 with name 'test' in namespace 'test' exists

</td>
</tr>
<tr>
<td valign="top">

Applying helm configuration fails with "Issuer of version cert-manager.io/v1 with name 'test' in namespace 'test' not found".

</td>
<td valign="top">

Make sure that Issuer of version cert-manager.io/v1 with name 'test' in namespace 'test' exists

</td>
</tr>
<tr>
<td valign="top">

Applying helm configuration fails with "ClusterIssuer of version cert-manager.io/v1 with name 'test' not found".

</td>
<td valign="top">

Make sure that ClusterIssuer of version cert-manager.io/v1 with name 'test' exists

</td>
</tr>
<tr>
<td valign="top">

Applying helm configration fails with "Istio not installed on the cluster. Revise your Istio integration configuration."

</td>
<td valign="top">

The configuration for integration in Istio service mesh is provided but Istio is not installed on the cluster. Either install Istio on the cluster or remove the configuration for integration in Istio service mesh.

</td>
</tr>
<tr>
<td valign="top">

Applying helm configuration fails with "An error occurred because certain necessary configuration settings are missing. Ensure that either 'config.security.communication.internal.encryptionEnabled' or 'config.integration.serviceMesh.istio.istio-integration' is provided.".

</td>
<td valign="top">

It is mandatory to integrate either with Istio or cert-manager. This is done by configuring at least one of the two properties:: config.integration.serviceMesh.istio.istio-integration and config.security.communication.internal.encryptionEnabled. config.integration.serviceMesh.istio.istio-integration makes config.security.communication.internal.encryptionEnabled optional. If "encryptionEnabled" is set to true and config.integration.serviceMesh.istio.istio-integration is missing then config.security.communication.internalCommunication.certManager.issuerRef.name and config.security.communication.internalCommunication.certManager.issuerRef.kind have to be provided.

</td>
</tr>
<tr>
<td valign="top">

Applying helm configuration fails with 'Connectivity Proxy tenant mode "shared" is not compatible with Transparent Proxy tenant mode "dedicated". Both must be in the same mode.'.

</td>
<td valign="top">

Make sure that the transparent proxy and the referenced connectivity proxy are in the same tenant mode.

</td>
</tr>
<tr>
<td valign="top">

Applying helm configuration fails with 'Connectivity Proxy tenant mode "dedicated" is not compatible with Transparent Proxy tenant mode "shared". Both must be in the same mode.'.

</td>
<td valign="top">

Make sure that the transparent proxy and the referenced connectivity proxy are in the same tenant mode.

</td>
</tr>
<tr>
<td valign="top">

Applying helm configuration fails with "Connectivity Proxy multi region ConfigMap with name <connectivityProxyMultiRegionConfigMapName\> in namespace <connectivityProxyMultiRegionConfigMapNamespace\> does not exist!".

</td>
<td valign="top">

The connectivity proxy multi region config map does not exist.

</td>
</tr>
</table>

