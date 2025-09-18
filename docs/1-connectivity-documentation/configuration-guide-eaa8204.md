<!-- loioeaa8204fc7484df984b3c321624827ff -->

# Configuration Guide

Find an overview of configuration parameters for the Connectivity Proxy for Kubernetes.

Refer to the table below for the configurations available in the `values.yaml` file of the Connectivity Proxy.

> ### Note:  
> Make sure you become familiar with the semantics, restrictions and interoperability aspects of each property before using it.

[Parameter Overview](configuration-guide-eaa8204.md#loioeaa8204fc7484df984b3c321624827ff__overview)

[Example](configuration-guide-eaa8204.md#loioeaa8204fc7484df984b3c321624827ff__example)



<a name="loioeaa8204fc7484df984b3c321624827ff__overview"/>

## Parameter Overview


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Desccription

</th>
<th valign="top">

Default

</th>
</tr>
<tr>
<td valign="top">

additionalCAs.secretName

</td>
<td valign="top">

This property allows to specify a list of CA certificates which are to be trusted, in addition to the default ones for the outbound communication of the Connectivity Proxy components. The value is the name of a secret in the same namespace in which the proxy is installed. It must contain a field with key "ca-certificates.crt" and with the value being all CAs to be trusted, concatenated together one after the other.

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

chart.nameSuffix

</td>
<td valign="top">

Custom string used to suffix your resources.

</td>
<td valign="top">

"" \(empty string\)

</td>
</tr>
<tr>
<td valign="top">

compliance.fipsModeEnabled

</td>
<td valign="top">

Configures the Connectivity Proxy and its helper components to run in a mode that is compliant with FIPS \(*Federal Information Processing Standard*\). It will use *Bouncy Castle FIPS* as its Java security provider.

</td>
<td valign="top">

false

</td>
</tr>
<tr>
<td valign="top">

config.displayName

</td>
<td valign="top">

Display name for the Connectivity Proxy installation. It is displayed in the Cloud Connector UI in Cloud Connections section.

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

config.integration.connectivityService.serviceCredentialsKey

</td>
<td valign="top">

Key in the Connectivity service secret resource that holds the base64-encoded value of the Connectivity Proxy service key.

</td>
<td valign="top">

"service\_key"

</td>
</tr>
<tr>
<td valign="top">

config.logging.format

</td>
<td valign="top">

Specifies the logging format for the Connectivity Proxy and it's components. The possible values are "console" and "json".

</td>
<td valign="top">

"console"

</td>
</tr>
<tr>
<td valign="top">

config.servers.businessDataTunnel.enableTls

</td>
<td valign="top">

Enables end-to-end mutual TLS. See [Mutual TLS](mutual-tls-7ce7883.md) for details.

</td>
<td valign="top">

false

</td>
</tr>
<tr>
<td valign="top">

config.servers.businessDataTunnel.externalHost

</td>
<td valign="top">

External ingress host of the business data tunnel server.

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

config.servers.businessDataTunnel.externalPort

</td>
<td valign="top">

External ingress port of the business data tunnel server.

</td>
<td valign="top">

443

</td>
</tr>
<tr>
<td valign="top">

config.servers.businessDataTunnel.strictSniEnabled

</td>
<td valign="top">

Flag for enabling and disabling strict SNI verification in the business data tunnel server.

</td>
<td valign="top">

true

</td>
</tr>
<tr>
<td valign="top">

config.servers.businessDataTunnel.port

</td>
<td valign="top">

Port on which to start the business data tunnel server.

</td>
<td valign="top">

8042

</td>
</tr>
<tr>
<td valign="top">

config.servers.businessDataTunnel.threadPoolSize

</td>
<td valign="top">

Number of worker threads for the tunnel server. If not set, the value will be calculated, based on the available resources. The value has a lower limit of 20.

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

config.servers.proxy.authorization.oauth.allowedClientId

</td>
<td valign="top">

OAuth client ID that is authorized to pass through the Connectivity Proxy when authorization is enabled.

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

config.servers.proxy.clientConnection.writeTimeoutSeconds

</td>
<td valign="top">

Write timeout for the client connections to the proxy \(from the proxy's point of view\).

</td>
<td valign="top">

10

</td>
</tr>
<tr>
<td valign="top">

config.servers.proxy.http.allowRemoteConnections

</td>
<td valign="top">

Flag for enabling and disabling calls from outside the pod to the HTTP proxy server.

</td>
<td valign="top">

true

</td>
</tr>
<tr>
<td valign="top">

config.servers.proxy.http.enabled

</td>
<td valign="top">

Flag for enabling and disabling the HTTP proxy server.

</td>
<td valign="top">

false

</td>
</tr>
<tr>
<td valign="top">

config.servers.proxy.http.enableProxyAuthorization

</td>
<td valign="top">

Flag for enabling and disabling the HTTP proxy authorization. See [Operational Modes](operational-modes-148bbad.md) for details.

</td>
<td valign="top">

true

</td>
</tr>
<tr>
<td valign="top">

config.servers.proxy.http.port

</td>
<td valign="top">

Port on which to start the HTTP proxy server.

</td>
<td valign="top">

20003

</td>
</tr>
<tr>
<td valign="top">

config.servers.proxy.socks5.allowRemoteConnections

</td>
<td valign="top">

Flag for enabling and disabling calls from outside the pod to the SOCKS5 proxy server.

</td>
<td valign="top">

true

</td>
</tr>
<tr>
<td valign="top">

config.servers.proxy.socks5.enabled

</td>
<td valign="top">

Flag for enabling and disabling the SOCKS5 proxy server.

</td>
<td valign="top">

true

</td>
</tr>
<tr>
<td valign="top">

config.servers.proxy.socks5.enableProxyAuthorization

</td>
<td valign="top">

Flag for enabling and disabling the SOCKS5 proxy authorization. See [Operational Modes](operational-modes-148bbad.md) for details.

</td>
<td valign="top">

true

</td>
</tr>
<tr>
<td valign="top">

config.servers.proxy.socks5.port

</td>
<td valign="top">

Port on which to start the SOCKS5 proxy server.

</td>
<td valign="top">

20004

</td>
</tr>
<tr>
<td valign="top">

config.servers.proxy.threadPoolSize

</td>
<td valign="top">

Number of worker threads for the proxy server. If not set, the value will be calculated, based on the available resources. The value has a lower limit of 20.

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

config.jvm.errorFilePath

</td>
<td valign="top">

Directory for JVM error logs.

</td>
<td valign="top">

"/var/log/connectivity"

</td>
</tr>
<tr>
<td valign="top">

config.jvm.heapDumpPath

</td>
<td valign="top">

Directory for JVM heap dumps.

</td>
<td valign="top">

"/var/log/connectivity"

</td>
</tr>
<tr>
<td valign="top">

config.jvm.memory.maxDirectSize

</td>
<td valign="top">

Maximum direct memory size to be set to the java process of the Connectivity Proxy. If not set, the value will be calculated, based on the available resources. If the available resources do not set a limit, a default value is used.

</td>
<td valign="top">

512m

</td>
</tr>
<tr>
<td valign="top">

config.jvm.memory.maxHeapSize

</td>
<td valign="top">

Maximum heap size to be set to the java process of the Connectivity Proxy. If not set, the value will be calculated, based on the available resources. If the available resources do not set a limit, a default value is used.

</td>
<td valign="top">

512m

</td>
</tr>
<tr>
<td valign="top">

config.jvm.memory.minHeapSize

</td>
<td valign="top">

Minimum heap size to be set to the java process of the Connectivity Proxy. If not set, the value will be calculated, based on the available resources. If the available resources do not set a limit, a default value is used.

</td>
<td valign="top">

128m

</td>
</tr>
<tr>
<td valign="top">

config.highAvailabilityMode

</td>
<td valign="top">

High availability mode in which the Connectivity Proxy works. The possible values are `off`, `subdomain`, and `path`. See [High Availability](high-availability-3c7f10d.md) for details.

</td>
<td valign="top">

"off"

</td>
</tr>
<tr>
<td valign="top">

config.subaccountId

</td>
<td valign="top">

ID of the subaccount, on whose behalf the Connectivity Proxy is running. This is mandatory only for the *dedicated* tenant mode. It is ignored when running in *shared* tenant mode.

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

config.subaccountSubdomain

</td>
<td valign="top">

Subdomain of the subaccount, on whose behalf the Connectivity Proxy is running. This is mandatory only for the *dedicated* tenant mode when there is at least one proxy with disabled authorization. It is ignored when running in *shared* tenant mode or if authorization is enabled for all proxies.

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

config.tenantMode

</td>
<td valign="top">

Mode in which the Connectivity Proxy works. The possible values are *dedicated* \(single-tenant mode\) and *shared* \(multi-tenant mode\).

See [Operational Modes](operational-modes-148bbad.md) for details.

</td>
<td valign="top">

"dedicated"

</td>
</tr>
<tr>
<td valign="top">

config.serviceChannels.enabled

</td>
<td valign="top">

Enables or disables the service channels which allow *on-premise to cloud* connectivity to services running in a Kubernetes cluster.

> ### Caution:  
> Only one Connectivity Proxy per Kubernetes cluster can have service channels enabled.

For more information, see [Service Channels: On-Premise-to-Cloud Connectivity](service-channels-on-premise-to-cloud-connectivity-bbd3040.md).

</td>
<td valign="top">

true

</td>
</tr>
<tr>
<td valign="top">

config.multiRegionMode.enabled

</td>
<td valign="top">

Enables or disables the multi-region mode.

</td>
<td valign="top">

false

</td>
</tr>
<tr>
<td valign="top">

config.multiRegionMode.configMapName

</td>
<td valign="top">

The name of the config map holding all region configurations which will be used by the Connectivity Proxy if multi-region mode is enabled.

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

config.metrics.prometheus.enabled

</td>
<td valign="top">

Enables the collection and exposure of metrics in the Prometheus format through an HTTP endpoint.

</td>
<td valign="top">

false

</td>
</tr>
<tr>
<td valign="top">

config.metrics.prometheus.port

</td>
<td valign="top">

Specifies the port on which the Prometheus metrics will be exposed.

</td>
<td valign="top">

9494

</td>
</tr>
<tr>
<td valign="top">

config.metrics.prometheus.jvmMetrics.enabled

</td>
<td valign="top">

Enables the collection of JVM-related metrics \(e.g., memory usage, garbage collection, thread count, etc.\).

</td>
<td valign="top">

false

</td>
</tr>
<tr>
<td valign="top">

config.metrics.prometheus.jmxMetrics.enabled

</td>
<td valign="top">

Enables the collection of metrics from JMX that are exposed by the Connectivity Proxy.

</td>
<td valign="top">

false

</td>
</tr>
<tr>
<td valign="top">

secretConfig.integration.connectivityService.secretName

</td>
<td valign="top">

Name of the secret, which will hold the credentials for the Connectivity service.

</td>
<td valign="top">

"connectivity-proxy-service-key"

</td>
</tr>
<tr>
<td valign="top">

secretConfig.integration.connectivityService.secretData

</td>
<td valign="top">

base64-encoded value of the service key, obtained from the Connectivity Proxy service instance.

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

secretConfig.servers.businessDataTunnel.secretName

</td>
<td valign="top">

Name of the secret that is used for TLS handshake with The Ingress proxy or Cloud Connector. See [Mutual TLS](mutual-tls-7ce7883.md) for details.

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

secretConfig.servers.businessDataTunnel.secretData.caCertificate

</td>
<td valign="top">

CA certificate part of the secret that is used for TLS handshake with the Ingress proxy or Cloud Connector. See [Mutual TLS](mutual-tls-7ce7883.md) for details.

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

secretConfig.servers.businessDataTunnel.secretData.certificate

</td>
<td valign="top">

Certificate part of the secret that is used for TLS handshake with the Ingress proxy or Cloud Connector. See[Mutual TLS](mutual-tls-7ce7883.md) for details.

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

secretConfig.servers.businessDataTunnel.secretData.key

</td>
<td valign="top">

Key part of the secret that is used for TLS handshake with the Ingress proxy or Cloud Connector. See [Mutual TLS](mutual-tls-7ce7883.md) for details.

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

deployment.affinity.podAntiAffinity.topologyKey

</td>
<td valign="top">

Configuration of the topology key for the built-in pod anti-affinity setting of the Connectivity Proxy. More info: [Assigning Pods to Nodes | Kubernetes](https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node/#inter-pod-affinity-and-anti-affinity).

</td>
<td valign="top">

"topology.kubernetes.io/zone"

</td>
</tr>
<tr>
<td valign="top">

deployment.nodeSelector

</td>
<td valign="top">

Label\(s\) which are configured for the `nodeSelector` property for all Connectivity Proxy-associated pods. More info: [https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node/\#nodeselector](https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node/#nodeselector)

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

deployment.podDisruptionBudget.minAvailable

</td>
<td valign="top">

Configuration for the minimum required available Pods during voluntary disruptions in the Connectivity Proxy *Pod Disruption Budget*. Can be specified as percentage \(e.g. "50%"\) or as an absolute number \(e.g. "3"\).

</td>
<td valign="top">

"50%"

</td>
</tr>
<tr>
<td valign="top">

deployment.podDisruptionBudget.unhealthyPodEvictionPolicy

</td>
<td valign="top">

Configuration for eviction policy of unhealthy pods in the Connectivity Proxy *Pod Disruption Budget*. One of "IfHealthyBudget", "AlwaysAllow". For more information, see: [Kubernetes Pod Disruption Budget](https://kubernetes.io/docs/tasks/run-application/configure-pdb/#unhealthy-pod-eviction-policy).

</td>
<td valign="top">

"IfHealthyBudget"

</td>
</tr>
<tr>
<td valign="top">

deployment.image.pullPolicy

</td>
<td valign="top">

One of `Always`, `Never`, `IfNotPresent`. For more information, see: [Updating images](https://kubernetes.io/docs/concepts/containers/images#updating-images) \(Kubernetes documentation\).

</td>
<td valign="top">

"IfNotPresent"

</td>
</tr>
<tr>
<td valign="top">

deployment.image.pullSecret

</td>
<td valign="top">

Secret used for authentication against the repository.

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

deployment.image.registry

</td>
<td valign="top">

Name of the registry from which the Connectivity deployment is downloaded.

</td>
<td valign="top">

<the image repository\>

</td>
</tr>
<tr>
<td valign="top">

deployment.image.repository

</td>
<td valign="top">

Name of the repository.

</td>
<td valign="top">

"com.sap.cloud.connectivity/connectivity-proxy"

</td>
</tr>
<tr>
<td valign="top">

deployment.image.tag

</td>
<td valign="top">

Version of the Connectivity Proxy to be deployed.

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

deployment.image.digest

</td>
<td valign="top">

Digest the Connectivity Proxy's image to be deployed. If both digest and tag are provided, the value of the digest has precedence.

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

deployment.utilityImage.pullPolicy

</td>
<td valign="top">

One of *Always*, *Never*, *IfNotPresent*. More info: [https://kubernetes.io/docs/concepts/containers/images\#updating-images](https://kubernetes.io/docs/concepts/containers/images#updating-images)

</td>
<td valign="top">

"IfNotPresent"

</td>
</tr>
<tr>
<td valign="top">

deployment.utilityImage.pullSecret

</td>
<td valign="top">

Pull secret for the utility image, used for authenticating against the repository.

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

deployment.utilityImage.registry

</td>
<td valign="top">

Name of the registry from which the utility image will be downloaded.

</td>
<td valign="top">

"docker.io"

</td>
</tr>
<tr>
<td valign="top">

deployment.utilityImage.repository

</td>
<td valign="top">

Name of the repository of the utility image.

> ### Caution:  
> The repository must point to an image, which is a version of the Docker official Alpine image \(see [Alpine Docker Image](https://hub.docker.com/_/alpine)\). Usage of any other type of container image is not recommended and can result in broken or dysfunctional Connectivity Proxy deployment.



</td>
<td valign="top">

"alpine"

</td>
</tr>
<tr>
<td valign="top">

deployment.utilityImage.tag

</td>
<td valign="top">

Version of the utility image to be deployed.

</td>
<td valign="top">

"3.18.0"

</td>
</tr>
<tr>
<td valign="top">

deployment.utilityImage.digest

</td>
<td valign="top">

Digest of the utility image to be deployed. If both digest and tag are provided, the value of the digest has precedence.

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

deployment.replicaCount

</td>
<td valign="top">

Amount of connectivity proxies to start from this deployment.

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

deployment.resources.maxFileDescriptorCount

</td>
<td valign="top">

Maximum number of file descriptors that will be used. This value should be based on the overall scenario in which the Connectivity Proxy is used and on the load of the proxy \(user requests to the proxy\).

</td>
<td valign="top">

64000

</td>
</tr>
<tr>
<td valign="top">

deployment.resources.limits.cpu

</td>
<td valign="top">

The *kubelet* enforces the limit so that the running container is not allowed to use more CPU resource than set as limit. If the limit is crossed, the process is throttled.

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

deployment.resources.limits.memory

</td>
<td valign="top">

The *kubelet* enforces the limit so that the running container is not allowed to use more memory than set as limit. If the limit is crossed, the process is terminated with an out-of-memory \(OOM\) error.

</td>
<td valign="top">

1024M

</td>
</tr>
<tr>
<td valign="top">

deployment.resources.requests.cpu

</td>
<td valign="top">

The Kubernetes scheduler uses this information to decide which node to place the pod on. If there are no nodes with the specified amount of CPU resources, the pod won't be scheduled \(and therefore not started\).

</td>
<td valign="top">

0.1

</td>
</tr>
<tr>
<td valign="top">

deployment.resources.requests.memory

</td>
<td valign="top">

The Kubernetes scheduler uses this information to decide which node to place the pod on. If there are no nodes with the specified amount of memory, the pod won't be scheduled \(and therefore not started\).

</td>
<td valign="top">

256M

</td>
</tr>
<tr>
<td valign="top">

deployment.regionConfigurationsController.resources.limits.cpu

</td>
<td valign="top">

The kubelet enforces the limit so that the running container of the Region Configurations Controller utility microservice is not allowed to use more CPU resource than the set limit. In case the limit is crossed, the process would be throttled. If omitted, nothing is enforced.

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

deployment.regionConfigurationsController.resources.limits.memory

</td>
<td valign="top">

The kubelet enforces the limit so that the running container of the Region Configurations Controller utility microservice is not allowed to use more memory than the set limit. In case the limit is crossed, the process would be terminated with an out of memory \(OOM\) error. If omitted, nothing is enforced.

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

deployment.regionConfigurationsController.resources.requests.cpu

</td>
<td valign="top">

The Kubernetes scheduler uses this information to decide which node to place the Region Configurations Controller utility microservice Pod on. If there are no nodes with the specified amount of CPU resources, the pod won't be scheduled \(and therefore started\). If omitted, nothing is enforced.

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

deployment.regionConfigurationsController.resources.requests.memory

</td>
<td valign="top">

The Kubernetes scheduler uses this information to decide which node to place the Region Configurations Controller utility microservice Pod on. If there are no nodes with the specified amount of memory, the pod won't be scheduled \(and therefore started\). If omitted, nothing is enforced.

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

deployment.autoscaling.horizontal.enabled

</td>
<td valign="top">

Enables or disables the *Horizontal Pod Autoscaler* mechanism, see [Horizontal Pod Autoscaler](https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale/) \(Kubernetes documentation\).

</td>
<td valign="top">

256M

</td>
</tr>
<tr>
<td valign="top">

deployment.autoscaling.horizontal.maxReplicaCount

</td>
<td valign="top">

Upper limit for the number of Connectivity Proxy replicas to which the autoscaler can scale up. It should be higher than `deployment.replicaCount`.

</td>
<td valign="top">

2

</td>
</tr>
<tr>
<td valign="top">

deployment.autoscaling.horizontal.metrics.cpuAverageUtilization

</td>
<td valign="top">

Target value of the average CPU metric across all Connectivity Proxy pods, represented as a percentage of the requested value of the CPU for the pods.

</td>
<td valign="top">

80

</td>
</tr>
<tr>
<td valign="top">

deployment.autoscaling.horizontal.metrics.memoryAverageUtilization

</td>
<td valign="top">

Target value of the average memory metric across all Connectivity Proxy pods, represented as a percentage of the requested value of the memory for the pods.

</td>
<td valign="top">

80

</td>
</tr>
<tr>
<td valign="top">

deployment.autoscaling.vertical.enabled

</td>
<td valign="top">

Enables or disables the V*ertical Pod Autoscaler* mechanism.

> ### Caution:  
> To take effect, the *Vertical Pod Autoscaling* mechanism for the cluster must be enabled. See [Vertical Pod Auto-Scaling](https://github.com/gardener/gardener/blob/master/docs/usage/shoot_autoscaling.md#vertical-pod-auto-scaling) for details \(Github Gardener Kubernetes documentation\).



</td>
<td valign="top">

false

</td>
</tr>
<tr>
<td valign="top">

deployment.autoscaling.vertical.updateMode

</td>
<td valign="top">

Mode in which the *Vertical Pod Autoscale* should operate. See [Vertical Pod Autoscaler Quick start](https://github.com/kubernetes/autoscaler/tree/master/vertical-pod-autoscaler#quick-start) for details \(Github Kubernetes documentation\).

</td>
<td valign="top">

"Off"

</td>
</tr>
<tr>
<td valign="top">

deployment.restartWatcher.enabled

</td>
<td valign="top">

Enables or disables the restart watcher which watches for changes in secrets and configmaps containing the label *connectivityproxy.sap.com/restart*, and restarts the Connectivity Proxy if needed. For more information, see [Automatic Pickup on Resource Changes](automatic-pickup-on-resource-changes-78ddb8f.md).

</td>
<td valign="top">

false

</td>
</tr>
<tr>
<td valign="top">

ingress.annotations

</td>
<td valign="top">

Annotations to add to the Ingress resource.

</td>
<td valign="top">

\{\}

</td>
</tr>
<tr>
<td valign="top">

ingress.className

</td>
<td valign="top">

Class name of the ingress resource. The possible values are "nginx" and "istio".

</td>
<td valign="top">

"nginx"

</td>
</tr>
<tr>
<td valign="top">

ingress.healthcheck.tls.proxy.secretName

</td>
<td valign="top">

Name of the secret that is used for TLS handshake with the Connectivity Proxy. See [External Health Checking](external-health-checking-5c75674.md) for details.

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

ingress.healthcheck.tls.proxy.secretData.caCertificate

</td>
<td valign="top">

CA certificate part of the secret that is used for TLS handshake with the Connectivity Proxy. See [External Health Checking](external-health-checking-5c75674.md) for details.

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

ingress.healthcheck.tls.proxy.secretData.certificate

</td>
<td valign="top">

Certificate part of the secret that is used for TLS handshake with the Connectivity Proxy. See [External Health Checking](external-health-checking-5c75674.md) for details.

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

ingress.healthcheck.tls.proxy.secretData.key

</td>
<td valign="top">

Key part of the secret that is used for TLS handshake with the Connectivity Proxy. See [External Health Checking](external-health-checking-5c75674.md) for details.

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

ingress.healthcheck.tls.secretName

</td>
<td valign="top">

Name of the secret that is used for TLS handshake with external health checking application. See [External Health Checking](external-health-checking-5c75674.md) for details.

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

ingress.healthcheck.tls.secretData.certificate

</td>
<td valign="top">

Certificate part of the secret that is used for TLS handshake with external health checking application. See [External Health Checking](external-health-checking-5c75674.md) for details.

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

ingress.healthcheck.tls.secretData.key

</td>
<td valign="top">

Key part of the secret that is used for TLS handshake with external health checking application. See [External Health Checking](external-health-checking-5c75674.md) for details.

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

ingress.istio.namespace

</td>
<td valign="top">

Installation namespace of Istio. For more information, see [Installing the Connectivity Proxy in Clusters with Istio](installing-the-connectivity-proxy-in-clusters-with-istio-0772710.md).

</td>
<td valign="top">

"istio-system"

</td>
</tr>
<tr>
<td valign="top">

ingress.istio.gateway.selector

</td>
<td valign="top">

Selector that is configured in the Istio ingress gateway \(used in the gateway configuration which is applied on the gateway pods\).

For more information, see [Installing the Connectivity Proxy in Clusters with Istio](installing-the-connectivity-proxy-in-clusters-with-istio-0772710.md).

</td>
<td valign="top">

\{ istio: ingressgateway \}

</td>
</tr>
<tr>
<td valign="top">

ingress.istio.tls.ciphers

</td>
<td valign="top">

Allowlist of enabled TLS ciphers specified as an array of strings.

</td>
<td valign="top">

As determined by Istio: [https://istio.io/latest/docs/reference/config/networking/gateway/\#ServerTLSSettings](https://istio.io/latest/docs/reference/config/networking/gateway/#ServerTLSSettings) , see the `cipherSuites` setting.

</td>
</tr>
<tr>
<td valign="top">

ingress.nginx.tls.ciphers

</td>
<td valign="top">

Enabled TLS ciphers specified in OpenSSL format.

</td>
<td valign="top">

As determined by nginx: [https://nginx.org/en/docs/http/ngx\_http\_ssl\_module.html\#ssl\_ciphers](https://nginx.org/en/docs/http/ngx_http_ssl_module.html#ssl_ciphers)

</td>
</tr>
<tr>
<td valign="top">

ingress.timeouts.proxy.connect

</td>
<td valign="top">

Connect timeout \(in seconds\), for the Ingress controller.

</td>
<td valign="top">

10

</td>
</tr>
<tr>
<td valign="top">

ingress.timeouts.proxy.read

</td>
<td valign="top">

Read timeout \(in seconds\), for the Ingress controller.

> ### Caution:  
> Make sure the load balancer exposing the Ingress controller is also configured to allow longer times. For example, for NGINX with AWS, you need to add a [special annotation for the LB service](https://github.com/kubernetes/ingress-nginx/blob/f48774e6db11468e69d094d79305b5638a3764bc/deploy/aws/l4/service-l4.yaml#L11) of the Ingress controller.



</td>
<td valign="top">

120

</td>
</tr>
<tr>
<td valign="top">

ingress.timeouts.proxy.send

</td>
<td valign="top">

Send timeout \(in seconds\), for the Ingress controller.

</td>
<td valign="top">

120

</td>
</tr>
<tr>
<td valign="top">

ingress.tls.proxy.secretName

</td>
<td valign="top">

Name of the secret that is used for TLS handshake with the Connectivity Proxy. See [Mutual TLS](mutual-tls-7ce7883.md) for details.

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

ingress.tls.proxy.secretData.caCertificate

</td>
<td valign="top">

CA certificate part of the secret that is used for TLS handshake with the Connectivity Proxy. See [Mutual TLS](mutual-tls-7ce7883.md) for details.

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

ingress.tls.proxy.secretData.certificate

</td>
<td valign="top">

Certificate part of the secret that is used for TLS handshake with the Connectivity Proxy. See [Mutual TLS](mutual-tls-7ce7883.md) for details.

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

ingress.tls.proxy.secretData.key

</td>
<td valign="top">

Key part of the secret that is used for TLS handshake with the Connectivity Proxy. See [Mutual TLS](mutual-tls-7ce7883.md) for details.

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

ingress.tls.secretName

</td>
<td valign="top">

Name of the secret that is used for TLS handshake with the Cloud Connector.

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

ingress.tls.secretData.caCertificate

</td>
<td valign="top">

CA certificate part of the secret that is used for TLS handshake with the Cloud Connector.

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

ingress.tls.secretData.certificate

</td>
<td valign="top">

Certificate part of the secret that is used for TLS handshake with the Cloud Connector.

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

ingress.tls.secretData.key

</td>
<td valign="top">

Key part of the secret that is used for TLS handshake with the Cloud Connector.

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

ipv6.preference.enabled

</td>
<td valign="top">

If enabled, the JVM will prefer using IPv6 over IPv4 when connecting to outside resources like BTP endpoints.

</td>
<td valign="top">

false

</td>
</tr>
<tr>
<td valign="top">

transparent-proxy.enabled

</td>
<td valign="top">

Flag for enabling and disabling Transparent Proxy installation as a subchart.

</td>
<td valign="top">

false

</td>
</tr>
</table>

[Back to Top](configuration-guide-eaa8204.md#loioeaa8204fc7484df984b3c321624827ff__top)



<a name="loioeaa8204fc7484df984b3c321624827ff__example"/>

## Example

> ### Caution:  
> The following example shows the full structure and does not represent a productive `values.yaml` file. Many properties listed here are mutually exclusive and should *not be used together* in real situations.

**values.yaml structure example**

```
chart:
  nameSuffix: "a string to append to resource names"
 
config:
  integration:
    auditlog:
      mode: "service"/"console"
      serviceCredentialsKey: "specifies the filename of the mounted auditlog secret"
    connectivityService:
      serviceCredentialsKey: "specifies the filename of the mounted connectivity service secret"
  servers:
    businessDataTunnel:
      enableTls: true/false
      externalHost: "myconnproxy.mycluster.com"
      externalPort: 443
      strictSniEnabled: true/false
      port: 8042
    proxy:
      authorization:
        oauth:
          allowedClientId: "the client id which is allowed as JWT issuer for proxy authorization"
      http:
        allowRemoteConnections: true/false
        enabled: true/false
        enableProxyAuthorization: true/false
        port: 20003
      rfcAndLdap:
        allowRemoteConnections: true/false
        enabled: true/false
        enableProxyAuthorization: true/false
        port: 20001
      socks5:
        allowRemoteConnections: true/false
        enabled: true/false
        enableProxyAuthorization: true/false
        port: 20004
      clientConnection:
        writeTimeoutSeconds: 10
 
  jvm:
    errorFilePath: "directory for JVM error logs"
    heapDumpPath: "directory for JVM heap dumps"
    memory:
      maxHeapSize: 256m
      minHeapSize: 16m
  highAvailabilityMode: "off"/"subdomain"/"path"
  subaccountId: "id of the subaccount, for which the proxy is running"
  subaccountSubdomain: "subdomain of the subaccount, for which the proxy is running"
  tenantMode: dedicated/shared
  serviceChannels:
    enabled: true/false
 
secretConfig:
  integration:
    auditlogService:
      secretData: "base64 encoded auditlog service key"
      secretName: "name of the secret resource, holding the auditlog secret"
    connectivityService:
      secretData: "base64 encoded connectivity_proxy service key"
      secretName: "name of the secret resource, holding the connectivity service secret"
  servers:
    businessDataTunnel:
      secretData:
        caCertificate: "base64 encoded CA certificate"
        certificate: "base64 encoded certificate"
        key: "base64 encoded private key"
      secretName: "name of the secret"
 
deployment:
  affinity:
    podAntiAffinity:
      topologyKey: "topology.kubernetes.io/zone"
  image:
    pullPolicy: "IfNotPresent"
    pullSecret: "name of the pull secret fot the registry"
    registry: "the official SAP image repo"
    repository: "com.sap.cloud.connectivity/connectivity-proxy"
    tag: X.Y.Z
  replicaCount: 1
  regionConfigurationsController:
    resources:
      limits:
        cpu: 1
        memory: 1024M
      requests:
        cpu: 0.1
        memory: 256M
  resources:
    maxFileDescriptorCount: 64000
    limits:
      cpu: 1
      memory: 1024M
    requests:
      cpu: 0.1
      memory: 256M
  autoscaling:
    horizontal:
      enabled: true/false
      maxReplicaCount: 2
      metrics:
        cpuAverageUtilization: 80
        memoryAverageUtilization: 80
    vertical:
      enabled: true/false
      updateMode: "Off"
 
ingress:
  annotations:
    annotation1: value1
    annotation2: value2
  healthcheck:
    tls:
      proxy:
        secretData:
          caCertificate: "base64 encoded CA certificate"
          certificate: "base64 encoded certificate"
          key: "base64 encoded private key"
        secretName: "name of the secret"
      secretData:
        certificate: "base64 encoded certificate"
        key: "base64 encoded private key"
      secretName: "name of the secret"
  timeouts:
    proxy:
      connect: 10
      read: 120
      send: 120
  tls:
    proxy:
      secretData:
        caCertificate: "base64 encoded CA certificate"
        certificate: "base64 encoded certificate"
        key: "base64 encoded private key"
      secretName: "name of the secret"
    secretData:
      caCertificate: "base64 encoded CA certificate"
      certificate: "base64 encoded certificate"
      key: "base64 encoded private key"
    secretName: "name of the secret"
  nginx:
    tls:
      ciphers: "HIGH:!aNULL:!MD5" 
  istio:
    tls:
      ciphers:
      - ECDHE-RSA-AES128-GCM-SHA256
      - ECDHE-RSA-AES256-GCM-SHA384
 
transparent-proxy:
  enabled: true/false
```

[Back to Top](configuration-guide-eaa8204.md#loioeaa8204fc7484df984b3c321624827ff__top)

