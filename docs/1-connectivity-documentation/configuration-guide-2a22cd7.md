<!-- loio2a22cd7872964e6a9ceb5af72920cfd0 -->

# Configuration Guide

Use the parameters below to configure the transparent proxy for Kubernetes.

> ### Caution:  
> Changing any of the properties below using *helm upgrade* may result in the restart of some or all transparent proxy components.

> ### Note:  
> \[n\] in the table below means that the described property is part of an array.



<a name="loio2a22cd7872964e6a9ceb5af72920cfd0__config"/>

## Configuration


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Description

</th>
<th valign="top">

Default Value

</th>
<th valign="top">

Example

</th>
<th valign="top">

Required

</th>
</tr>
<tr>
<td valign="top">

`config.tenantMode`

</td>
<td valign="top">

Defines the tenant mode in which the transparent proxy is working.

Default value *"dedicated"* specifies that only destinations defined in the subaccount in a service key can be exposed and accessed via the transparent proxy. The other option *"shared"* specifies that the proxy can work with different tenants subscribed to the provider in the service key. In this mode, on each request the *"X-Tenant-Subdomain"* or *"X-Tenant-Id"* header is required. The tenant mode *"shared"* works only for destinations of type HTTP.

</td>
<td valign="top">

"dedicated"

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

`config.integration.destinationService.connectionTimeoutSeconds`

</td>
<td valign="top">

Connect timeout that would be used when getting access tokens and Destination service clients. \[1, 60\] seconds allowed.

</td>
<td valign="top">

5

</td>
<td valign="top">

20

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`config.integration.destinationService.readTimeoutSeconds`

</td>
<td valign="top">

Read timeout that would be used when getting access tokens and Destination service clients. \[1, 60\] seconds allowed.

</td>
<td valign="top">

10

</td>
<td valign="top">

20

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`config.integration.connectivityProxy.connectionTimeoutSeconds`

</td>
<td valign="top">

The connect timeout must be used when accessing an HTTP system with `ProxyType`=`OnPremise` through the connectivity proxy. \[1, 60\] seconds allowed.

</td>
<td valign="top">

1

</td>
<td valign="top">

20

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`config.integration.connectivityProxy.serviceName`

</td>
<td valign="top">

Kubernetes service name and namespace associated with the connectivity proxy workload.

</td>
<td valign="top">

None

</td>
<td valign="top">

`connectivity-proxy.<namespace>`

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`config.integration.connectivityProxy.http.port` 

</td>
<td valign="top">

Port on which the HTTP interface of the connectivity proxy is started.

</td>
<td valign="top">

20003

</td>
<td valign="top">

 

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`config.integration.connectivityProxy.tcp.port` 

</td>
<td valign="top">

Port on which the TCP interface of the connectivity proxy is started.

</td>
<td valign="top">

20004

</td>
<td valign="top">

 

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`config.integration.serviceMesh.istio.istio-injection`

</td>
<td valign="top">

Integration with Istio service mesh.

The only acceptable value is 'enabled'. If set, the transparent proxy components will be integrated in the mesh, otherwise they will be exclusively removed from the mesh.

If the configuration is changed, it triggers a restart.

</td>
<td valign="top">

"enabled"

</td>
<td valign="top">

 

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`config.logging.level` 

</td>
<td valign="top">

The initial log level across all transparent proxy components. The log levels can be changed dynamically, see [Troubleshooting](https://wiki.one.int.sap/wiki/display/NGP/TP+Troubleshooting).

</td>
<td valign="top">

info

</td>
<td valign="top">

 

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`config.managedNamespacesMode` 

</td>
<td valign="top">

The mode in which transparent proxy operates with the destinations in the cluster. Possible values are "all" or "labelSelector".

If "labelSelector" is set, the transparent proxy operates only in namespaces labeled with *transparent-proxy.connectivity.api.sap/namespace:<namespace where TP is installed in\>*.

</td>
<td valign="top">

all

</td>
<td valign="top">

 

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`config.manager.executionIntervalMinutes`

</td>
<td valign="top">

The execution interval in minutes, on which the destination resource updates are fetched and applied to the cluster.

> ### Tip:  
> We recommend that you do not set this value higher than 5, if there are frequent updates on destinations.



</td>
<td valign="top">

3

</td>
<td valign="top">

 

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`config.security.accessControl.destinations.defaultScope`

</td>
<td valign="top">

Defines the default scope of destination custom resources. Possible values are “namespaced” or “clusterWide”.

See [Restrict Access Using Scoping](restrict-access-using-scoping-bd47cbe.md).

</td>
<td valign="top">

"namespaced"

</td>
<td valign="top">

 

</td>
<td valign="top">

True

</td>
</tr>
<tr>
<td valign="top">

`config.security.communication.internal.encryptionEnabled` 

</td>
<td valign="top">

Enables/disables mTLS communication between the transparent proxy components.

It should be disabled only in test environments or if you implement your own mTLS solution like Istio for example.

> ### Note:  
> Make sure you install the [cert-manager](https://cert-manager.io/) in advance.



</td>
<td valign="top">

true

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

`config.security.communication.internal.certManager.issuerRef.kind` 

</td>
<td valign="top">

The *cert-manager* custom Kubernetes resource type of the CA. Must be one of \(`Issuer` or `ClusterIssuer`\).

Only applicable for cert-manager.io \([https://cert-manager.io/docs/](https://cert-manager.io/docs/)\).

</td>
<td valign="top">

 

</td>
<td valign="top">

Issuer

</td>
<td valign="top">

False when encryption is disabled

</td>
</tr>
<tr>
<td valign="top">

`config.security.communication.internal.certManager.issuerRef.name` 

</td>
<td valign="top">

The name of the installed cert-manager issuer.

</td>
<td valign="top">

 

</td>
<td valign="top">

sap-transp-proxy-issuer

</td>
<td valign="top">

False when encryption is disabled

</td>
</tr>
<tr>
<td valign="top">

`config.security.communication.internal.certManager.issuerRef.namespace`

</td>
<td valign="top">

The namespace of the installed cert-manager issuer. Only applicable for cert.gardener.cloud \([https://github.com/gardener/cert-management](https://github.com/gardener/cert-management)\).

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

`config.security.communication.internal.certManager.certificate.privateKey.algorithm` 

</td>
<td valign="top">

Check cert-manager private key [docs](https://cert-manager.io/docs/reference/api-docs/#cert-manager.io/v1.CertificatePrivateKey).

Only applicable for cert-manager.io \([https://cert-manager.io/docs/](https://cert-manager.io/docs/)\).

</td>
<td valign="top">

 

</td>
<td valign="top">

ECDSA

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`config.security.communication.internal.certManager.certificate.privateKey.encoding` 

</td>
<td valign="top">

Check cert-manager private key [docs](https://cert-manager.io/docs/reference/api-docs/#cert-manager.io/v1.CertificatePrivateKey).

Only applicable for cert-manager.io \([https://cert-manager.io/docs/](https://cert-manager.io/docs/)\).

</td>
<td valign="top">

 

</td>
<td valign="top">

PKCS8

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`config.security.communication.internal.certManager.certificate.privateKey.size` 

</td>
<td valign="top">

Check cert-manager private key [docs](https://cert-manager.io/docs/reference/api-docs/#cert-manager.io/v1.CertificatePrivateKey).

Only applicable for cert-manager.io \([https://cert-manager.io/docs/](https://cert-manager.io/docs/)\).

</td>
<td valign="top">

 

</td>
<td valign="top">

256

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`config.security.communication.internal.certManager.certificate.duration` 

</td>
<td valign="top">

The duration for which the certificates will be valid. Minimum accepted duration is 1 hour. Value must be in units accepted by [Go time.ParseDuration](https://golang.org/pkg/time/#ParseDuration).

Only applicable for cert-manager.io \([https://cert-manager.io/docs/](https://cert-manager.io/docs/)\).

</td>
<td valign="top">

 

</td>
<td valign="top">

720h

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`config.security.communication.internal.certManager.certificate.renewBefore` 

</td>
<td valign="top">

How long before expiry the *cert-manager* should renew the currently issued certificate. Value must be in units accepted by [Go time.ParseDuration](https://golang.org/pkg/time/#ParseDuration).

Only applicable for cert-manager.io \([https://cert-manager.io/docs/](https://cert-manager.io/docs/)\).

</td>
<td valign="top">

 

</td>
<td valign="top">

240h

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`config.integration.destinationService.defaultInstanceName`

</td>
<td valign="top">

Name of the default destination service instance to be used when `destinationServiceInstanceName` is not provided in the destination custom resource specification.

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`config.integration.destinationService.instances[n].name`

</td>
<td valign="top">

Name of the destination service instance that is described. You can use it as `config.integration.destinationService.defaultInstanceName` or reference it in the destination custom resource specification as `destinationServiceInstanceName`.

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`config.integration.destinationService.instances[n].serviceCredentials.secretName` 

</td>
<td valign="top">

The name of the existing secret, which holds the credentials for the Destination service or the name of the secret to be created based on the "secretName", "secretData", "secretKey" fields.

</td>
<td valign="top">

destination-service-key

</td>
<td valign="top">

 

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`config.integration.destinationService.instances[n].serviceCredentials.secretKey` 

</td>
<td valign="top">

The key in the Destination service secret resource, which holds the base64-encoded value of the destination service key.

> ### Note:  
> Make sure you provide the right key for an existing secret. Required when the transparent proxy should create a secret and not required when describing an existing secret.



</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`config.integration.destinationService.instances[n].serviceCredentials.secretData` 

</td>
<td valign="top">

The base64-encoded value of the service key, obtained from the Destination service instance. Required when transparent proxy should create secret and not required when describing an existing secret.

> ### Note:  
> The base64 encoded value of the service key can only be specified during [Installation with Helm](installation-with-helm-d201be0.md).



</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`config.integration.destinationService.instances[n].serviceCredentials.secretNamespace` 

</td>
<td valign="top">

The namespace of the existing secret to be used, which holds the credentials for the Destination service. This field should not be present if there is no existing secret and the transparent proxy would create one based on the "secretName", "secretData", "secretKey" fields.

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`config.integration.destinationService.instances[n].serviceCredentials.privateKey.secretName` 

</td>
<td valign="top">

The name of the Kubenetes secret, which holds the private key to authenticate if using an x.509-based service key to the Destination service.

</td>
<td valign="top">

x509-svc-key-private-key

</td>
<td valign="top">

 

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`config.integration.destinationService.instances[n].serviceCredentials.privateKey.secretInternalKey` 

</td>
<td valign="top">

The name of the internal key inside the Kubenetes secret holding the private key to authenticate if using an x.509-based service key to the Destination service.

</td>
<td valign="top">

pk.pem

</td>
<td valign="top">

 

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`config.integration.destinationService.instances[n].associateWith.connectivityProxy.locallyConfiguredRegionId`

</td>
<td valign="top">

The locally configured region id from the connectivity proxy multi region configurations, that will be used by default when consuming destinations from the given destination service instance. Will be overridden for HTTP scenarios if header`SAP-Connectivity-Region-Configuration-Id` is passed.

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`deployment.image.registry`

</td>
<td valign="top">

Name of the registry from which the transparent proxy will be downloaded.

</td>
<td valign="top">

docker.io

</td>
<td valign="top">

 

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`deployment.image.repository` 

</td>
<td valign="top">

Name of the repository.

</td>
<td valign="top">

sapse

</td>
<td valign="top">

 

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`deployment.image.pullPolicy`

</td>
<td valign="top">

One of `Always`, `Never`, `IfNotPresent`.

For more information, see [Updating Images](https://kubernetes.io/docs/concepts/containers/images/) \(Kubernetes documentation\).

</td>
<td valign="top">

“IfNotPresent”

</td>
<td valign="top">

 

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`deployment.image.pullSecret`

</td>
<td valign="top">

The secret used for authenticating against the repository \(not required when using the Docker registry\).

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`deployment.image.tag`

</td>
<td valign="top">

Version of the transparent proxy images to be deployed.

</td>
<td valign="top">

<Version of the helm chart\>

</td>
<td valign="top">

1.0.0

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`deployment.replicas.http`

</td>
<td valign="top">

Amount of transparent HTTP proxy pods to start.

</td>
<td valign="top">

1

</td>
<td valign="top">

 

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`deployment.replicas.tcp`

</td>
<td valign="top">

Amount of transparent TCP proxy pods for each TCP destination to start from this deployment.

</td>
<td valign="top">

1

</td>
<td valign="top">

 

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`deployment.resources.http.request.cpu`

</td>
<td valign="top">

The Kubernetes scheduler uses this information to decide which node to place the pod on. If there are no nodes with the specified amount of CPU resources, the pod won't be scheduled \(and therefore started\).

</td>
<td valign="top">

0.2

</td>
<td valign="top">

 

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`deployment.resources.http.request.memory`

</td>
<td valign="top">

The Kubernetes scheduler uses this information to decide which node to place the pod on. If there are no nodes with the specified amount of memory, the pod won't be scheduled \(and therefore started\).

</td>
<td valign="top">

256M

</td>
<td valign="top">

 

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`deployment.resources.http.limits.cpu`

</td>
<td valign="top">

The Kubelet enforces the limit so that the running container is not allowed to use more CPU resources than the set limit. If the limit is crossed, the process is throttled.

</td>
<td valign="top">

0.4

</td>
<td valign="top">

 

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`deployment.resources.http.limits.memory`

</td>
<td valign="top">

The Kubelet enforces the limit so that the running container is not allowed to use more memory than the set limit. If the limit is crossed, the process is terminated with an out of memory \(OOM\) error.

</td>
<td valign="top">

512M

</td>
<td valign="top">

 

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`deployment.resources.tcp.request.cpu`

</td>
<td valign="top">

The Kubernetes scheduler uses this information to decide which node to place the pod on. If there are no nodes with the specified amount of CPU resources, the pod won't be scheduled \(and therefore started\).

</td>
<td valign="top">

0.05

</td>
<td valign="top">



</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`deployment.resources.tcp.request.memory` 

</td>
<td valign="top">

The Kubernetes scheduler uses this information to decide which node to place the Pod on. If there are no nodes with the specified amount of memory, the pod won't be scheduled \(and therefore started\).

</td>
<td valign="top">

32M

</td>
<td valign="top">



</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`deployment.resources.tcp.limits.cpu`

</td>
<td valign="top">

The Kubernetes enforces the limit so that the running container is not allowed to use more CPU resources than the set limit. In case the limit is crossed, the process would be throttled.

</td>
<td valign="top">

0.1

</td>
<td valign="top">



</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`deployment.resources.tcp.limits.memory` 

</td>
<td valign="top">

The Kubelet enforces the limit so that the running container is not allowed to use more memory than the set limit. In case the limit is crossed, the process would be terminated with an out-of-memory \(OOM\) error.

</td>
<td valign="top">

64M

</td>
<td valign="top">



</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`deployment.autoscaling.http.horizontal.enabled`

</td>
<td valign="top">

Enables or disables the *Horizontal Pod Autoscaler* mechanism see [Horizontal Pod Autoscaler](https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale/) \(Kubernetes documentation\) for HTTP proxy pods.

> ### Note:  
> You cannot enable both horizontal and vertical autoscaling. If you want to use horizontal autoscaling, `deployment.autoscaling.http.vertical.enabled` must not be set to `true`.



</td>
<td valign="top">

False

</td>
<td valign="top">

 

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`deployment.autoscaling.http.horizontal.maxReplicaCount`

</td>
<td valign="top">

Upper limit for the number of HTTP transparent proxy replicas to which the autoscaler can scale up. It should be higher than `deployment.replicas.http`.

</td>
<td valign="top">

2

</td>
<td valign="top">

 

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`deployment.autoscaling.http.horizontal.metrics.cpuAverageUtilization`

</td>
<td valign="top">

Target value of the average CPU metric across all transparent HTTP proxy pods, represented as a percentage of the requested value of the CPU for the pods.

</td>
<td valign="top">

80

</td>
<td valign="top">

 

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`deployment.autoscaling.http.horizontal.metrics.memoryAverageUtilization`

</td>
<td valign="top">

Target value of the average memory metric across all transparent HTTP proxy pods, represented as a percentage of the requested value of the memory for the pods.

</td>
<td valign="top">

80

</td>
<td valign="top">

 

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`deployment.autoscaling.http.vertical.enabled` 

</td>
<td valign="top">

Enables or disables the *Vertical Pod Autoscaler* mechanism for http proxy pods.

To take effect, the vertical pod autoscaling mechanism for the cluster should be enabled.

See [Vertical Pod Auto-Scaling](https://github.com/gardener/gardener/blob/master/docs/usage/shoot_autoscaling.md#vertical-pod-auto-scaling) for details.

> ### Note:  
> You cannot enable both horizontal and vertical autoscaling. If you want to use vertical autoscaling, `deployment.autoscaling.http.horizontal.enabled` must not be set to `true`.



</td>
<td valign="top">

false

</td>
<td valign="top">

 

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`deployment.autoscaling.http.vertical.updateMode` 

</td>
<td valign="top">

The mode in which the *Vertical Pod Autoscaler* should operate.

See [Vertical Pod Autoscaler Quick start](https://github.com/kubernetes/autoscaler/tree/master/vertical-pod-autoscaler#quick-start) for details.

</td>
<td valign="top">

"Off"

</td>
<td valign="top">

 

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`deployment.autoscaling.http.vertical.minAllowed.cpu` 

</td>
<td valign="top">

Specifies the minimal amount of CPU that will be recommended for each HTTP proxy pod. By default there is no minimum.

> ### Note:  
> There are 2 containers in each HTTP proxy pod.



</td>
<td valign="top">

 

</td>
<td valign="top">

0.2

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`deployment.autoscaling.http.vertical.minAllowed.memory` 

</td>
<td valign="top">

Specifies the minimal amount of memory that will be recommended for each HTTP proxy pod. By default, there is no minimum.

> ### Note:  
> There are 2 containers in each HTTP proxy pod.



</td>
<td valign="top">

 

</td>
<td valign="top">

256M

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`deployment.autoscaling.http.vertical.maxAllowed.cpu`

</td>
<td valign="top">

Specifies the maximum amount of CPU that will be recommended for each HTTP proxy pod. By default, there is no maximum.

> ### Note:  
> There are 2 containers in each HTTP proxy pod.



</td>
<td valign="top">

 

</td>
<td valign="top">

0.4

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`deployment.autoscaling.http.vertical.maxAllowed.memory` 

</td>
<td valign="top">

Specifies the maximum amount of memory that will be recommended for each HTTP proxy pod. By default, there is no maximum.

> ### Note:  
> There are 2 containers in each HTTP proxy pod.



</td>
<td valign="top">

 

</td>
<td valign="top">

512M

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`deployment.autoscaling.tcp.horizontal.enabled`

</td>
<td valign="top">

Enables or disables the *Horizontal Pod Autoscaler* mechanism see [Horizontal Pod Autoscaler](https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale/) \(Kubernetes documentation\) for TCP proxy pods.

> ### Note:  
> You cannot enable both horizontal and vertical autoscaling. If you want to use horizontal autoscaling, `deployment.autoscaling.tcp.vertical.enabled` must not be set to `true`.



</td>
<td valign="top">

False

</td>
<td valign="top">

 

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`deployment.autoscaling.tcp.horizontal.maxReplicaCount`

</td>
<td valign="top">

Upper limit for the number of TCP transparent proxy replicas to which the autoscaler can scale up. It should be higher than `deployment.replicas.tcp`.

</td>
<td valign="top">

2

</td>
<td valign="top">

 

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`deployment.autoscaling.tcp.horizontal.metrics.cpuAverageUtilization`

</td>
<td valign="top">

Target value of the average CPU metric across all transparent TCP proxy pods for a given destination instance, represented as a percentage of the requested value of the CPU for the pods.

</td>
<td valign="top">

80

</td>
<td valign="top">

 

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`deployment.autoscaling.tcp.horizontal.metrics.memoryAverageUtilization` 

</td>
<td valign="top">

Target value of the average memory metric across transparent TCP proxy pods for a given destination instance, represented as a percentage of the requested value of the memory for the pods.

</td>
<td valign="top">

80

</td>
<td valign="top">

 

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`deployment.autoscaling.tcp.vertical.enabled` 

</td>
<td valign="top">

Enables or disables the *Vertical Pod Autoscaler* mechanism for TCP proxy pods.

To take effect, the vertical pod autoscaling mechanism for the cluster should be enabled.

See [Vertical Pod Auto-Scaling](https://github.com/gardener/gardener/blob/master/docs/usage/shoot_autoscaling.md#vertical-pod-auto-scaling) for details.

> ### Note:  
> You cannot enable both horizontal and vertical autoscaling. If you want to use vertical autoscaling, `deployment.autoscaling.tcp.horizontal.enabled` must not be set to `true`.



</td>
<td valign="top">

false

</td>
<td valign="top">

 

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`deployment.autoscaling.tcp.vertical.updateMode`

</td>
<td valign="top">

The mode in which the *Vertical Pod Autoscaler* should operate.

See [Vertical Pod Autoscaler Quick start](https://github.com/kubernetes/autoscaler/tree/master/vertical-pod-autoscaler#quick-start) for details.

</td>
<td valign="top">

"Off"

</td>
<td valign="top">

 

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`deployment.autoscaling.tcp.vertical.minAllowed.cpu` 

</td>
<td valign="top">

Specifies the minimal amount of CPU that will be recommended for each TCP proxy pod.

By default there is no minimum.

</td>
<td valign="top">

 

</td>
<td valign="top">

0.2

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`deployment.autoscaling.tcp.vertical.minAllowed.memory` 

</td>
<td valign="top">

Specifies the minimal amount of memory that will be recommended for each TCP proxy pod.

By default there is no minimum.

</td>
<td valign="top">

 

</td>
<td valign="top">

256M

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`deployment.autoscaling.tcp.vertical.maxAllowed.cpu` 

</td>
<td valign="top">

Specifies the maximum amount of CPU that will be recommended for each TCP proxy pod.

By default there is no maximum.

</td>
<td valign="top">

 

</td>
<td valign="top">

0.4

</td>
<td valign="top">

False

</td>
</tr>
<tr>
<td valign="top">

`deployment.autoscaling.tcp.vertical.maxAllowed.memory` 

</td>
<td valign="top">

Specifies the maximum amount of memory that will be recommended for each TCP proxy pod.

By default there is no maximum.

</td>
<td valign="top">

 

</td>
<td valign="top">

512M

</td>
<td valign="top">

False

</td>
</tr>
</table>

If you want to pull docker images from the *SAP Repository-Based Shipment Channel* \(RBSC\), use the following configuration:

-   `deployment.image.registry` = `73554900100900006891.dockersrv.cdn.repositories.cloud.sap`
-   `deployment.image.repository` = `com.sap.core.connectivity.transparent-proxy`
-   `deployment.image.pullSecret` = See [Lifecycle Management](lifecycle-management-1c18e0c.md).

