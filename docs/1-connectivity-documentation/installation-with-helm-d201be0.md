<!-- loiod201be05a4aa444898fd20bcecb1ebbb -->

# Installation with Helm

Use the Helm chart to configure and manage the lifecycle of the Transparent Proxy.

> ### Note:  
> Current version of the Transparent Proxy is 1.8.0.

The Transparent Proxy delivery includes a Helm chart that you can use for lifecycle management. The Helm allows full configuration via [the standard Helm method of a "values.yaml" file](https://helm.sh/docs/chart_template_guide/values_files/).

> ### Note:  
> If Istio is not present in the cluster, you must manually set up the *certificate manager*. Alternatively, you can disable encryption within the cluster by setting `encryptionEnabled` to `false`. However, the latter is not recommended for use in production environments.

The Transparent Proxy Helm chart is available via the RBSC \(*repository-based shipment channel*\) Helm repository and DockerHub.



<a name="loiod201be05a4aa444898fd20bcecb1ebbb__section_rg5_cdb_ycc"/>

## Prerequisites

1.  Prepare credentials for the Destination service instance : see [Destination Service Integration](destination-service-integration-cd02e5c.md) \(step 3\).
2.  Fill all other properties in `values.yaml` for your scenario, as described in [Configuration Guide](configuration-guide-2a22cd7.md).

    > ### Caution:  
    > Do not extract the archive and modify the default `values.yml` file included there. Instead, use your own `values.yml` and only include fields that should be overridden.

    > ### Note:  
    > By default, mTLS encryption is enabled using [cert-manager](https://cert-manager.io/). You should check the [Configuration Guide](configuration-guide-2a22cd7.md) to modify the configuration settings according to your setup, for example, referencing your *cert-manager Issuer* or *ClusterIssuer*.

    > ### Tip:  
    > Encryption for the Transparent Proxy components can also be disabled for test purposes or if you have implemented your own mTLS sidecar solution, for example, Istio.

    **Example: Transparent Proxy values.yaml Snippet**

    > ### Sample Code:  
    > ```
    > deployment:
    >   image:
    >     ## Тhe name of the registry from which the Transparent Proxy will be downloaded.
    >     registry: docker.io
    >     ## Тhe name of the repository from which the Transparent Proxy will be downloaded.
    >     repository: sapse
    >     ## Оne of Always, Never, IfNotPresent. For more information, see https://kubernetes.io/docs/concepts/containers/images#updating-images.
    >     pullPolicy: IfNotPresent
    >     ## Тhe secret used for authenticating against the repository. (Not required when using the DockerHub registry).
    >     #pullSecret: ""
    >     ## Тhe version of the Transparent Proxy images that are to be deployed. By default, it is the chart version
    >     #tag:
    >   replicas:
    >     ## Тhe amount of transparent HTTP proxy pods to start.
    >     http: 1
    >     ## Тhe amount of transparent TCP proxy pods for each TCP destination to start.
    >     tcp: 1
    >   resources:
    >     http:
    >       requests:
    >         ## The K8s scheduler uses this information to decide which node to place the pod on. If there are no nodes with the specified amount of CPU resources, the pod won't be scheduled (and therefore started).
    >         cpu: 0.2
    >         ## The K8s scheduler uses this information to decide which node to place the Pod on. If there are no nodes with the specified amount of memory, the pod won't be scheduled (and therefore started).
    >         memory: 256M
    >       limits:
    >         ## The Kubelet enforces the limit so that the running container is not allowed to use more CPU resources than the set limit. In case the limit is crossed, the process would be throttled.
    >         cpu: 0.4
    >         ## The Kubelet enforces the limit so that the running container is not allowed to use more memory than the set limit. In case the limit is crossed, the process would be terminated with an out-of-memory (OOM) error.
    >         memory: 512M
    >     tcp:
    >       requests:
    >         ## The K8s scheduler uses this information to decide which node to place the pod on. If there are no nodes with the specified amount of CPU resources, the pod won't be scheduled (and therefore started).
    >         cpu: 0.05
    >         ## The K8s scheduler uses this information to decide which node to place the Pod on. If there are no nodes with the specified amount of memory, the pod won't be scheduled (and therefore started).
    >         memory: 32M
    >       limits:
    >         ## The Kubelet enforces the limit so that the running container is not allowed to use more CPU resources than the set limit. In case the limit is crossed, the process would be throttled.
    >         cpu: 0.1
    >         ## The Kubelet enforces the limit so that the running container is not allowed to use more memory than the set limit. In case the limit is crossed, the process would be terminated with an out-of-memory (OOM) error.
    >         memory: 64M
    >   autoscaling:
    >     http:
    >       vertical:
    >         ## Enables or disables the Vertical Pod Autoscaler mechanism for http proxy pods. In order for this configuration to take effect, the Vertical Pod Autoscaling mechanism for the cluster should be enabled. See Vertical Pod Auto-Scaling for details
    >         ## Cannot enable both horizontal and vertical autoscaling. If you want vertical autoscaling deployment.autoscaling.http.horizontal.enabled should not be set to true
    >         enabled: false
    >         ##  The mode in which the Vertical Pod Autoscaler should operate. For more details see https://github.com/kubernetes/autoscaler/tree/master/vertical-pod-autoscaler#quick-start
    >         updateMode: "Off"
    >       horizontal:
    >         ## Enables or disables the Horizontal Pod Autoscaler mechanism see  Horizontal Pod Autoscaler(Kubernetes documentation) for http proxy pods.
    >         ## Cannot enable both horizontal and vertical autoscaling.If you want horizontal autoscaling deployment.autoscaling.http.vertical.enabled should not be set to true
    >         enabled: false
    >         ## Upper limit for the number of http Transparent Proxy replicas to which the autoscaler can scale up. It should be higher than deployment.replicas.http.
    >         maxReplicaCount: 2
    >         metrics:
    >           ## Target value of the average CPU metric across all transparent http proxy pods, represented as a percentage of the requested value of the CPU for the pods.
    >           cpuAverageUtilization: 80
    >           ## Target value of the average memory metric across all transparent http proxy pods, represented as a percentage of the requested value of the memory for the pods.
    >           memoryAverageUtilization: 80
    >     tcp:
    >       horizontal:
    >         ## Enables or disables the Horizontal Pod Autoscaler mechanism see  Horizontal Pod Autoscaler(Kubernetes documentation) for tcp proxy pods.
    >         ## Cannot enable both horizontal and vertical autoscaling.If you want horizontal autoscaling deployment.autoscaling.tcp.vertical.enabled should not be set to true
    >         enabled: false
    >         ## Upper limit for the number of tcp Transparent Proxy replicas to which the autoscaler can scale up. It should be higher than deployment.replicas.tcp.
    >         maxReplicaCount: 2
    >         metrics:
    >           ## Target value of the average CPU metric across all transparent tcp proxy pods for a given destination instance, represented as a percentage of the requested value of the CPU for the pods.
    >           cpuAverageUtilization: 80
    >           ## Target value of the average memory metric across transparent tcp proxy pods for a given destination instance, represented as a percentage of the requested value of the memory for the pods.
    >           memoryAverageUtilization: 80
    >       vertical:
    >         ## Enables or disables the Vertical Pod Autoscaler mechanism for tcp proxy pods. In order for this configuration to take effect, the Vertical Pod Autoscaling mechanism for the cluster should be enabled. See Vertical Pod Auto-Scaling for details
    >         ## Cannot enable both horizontal and vertical autoscaling. If you want vertical autoscaling deployment.autoscaling.tcp.horizontal.enabled should not be set to true
    >         enabled: false
    >         updateMode: "Off"
    > config:
    >   logging:
    >     ## The initial log level across all Transparent Proxy components. Accepted log levels are: trace, debug, info, warn, error, fatal.
    >     ## The log levels can be changed dynamically, see https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/transparent-proxy-troubleshooting?locale=en-US&q=transparent%20proxy#change-log-levels-of-the-transparent-proxy-components
    >     level: info
    >   ## Defines the tenant mode in which Transparent Proxy is working in. Default value "dedicated" means that only Destinations in the subaccount defined in Destination Service key could be exposed and accessed via TP.
    >   ## The other option "shared" shows that the proxy could work with different subscribed tenants to the provider in the service key. Then, on each request "X-Tenant-Subdomain" or "X-Tenant-Id" header becomes required in this mode.
    >   tenantMode: dedicated
    >   security:
    >     accessControl:
    >       destinations:
    >         ## Defines the default scope of Destination CRs. Possible values are “namespaced” or “clusterWide”. See https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/destination-custom-resource-scope?locale=en-US&q=transparent%20proxy
    >         defaultScope: "namespaced"
    >     communication:
    >       internal:
    >         ## Enables/Disables mTLS communication between the Transparent Proxy components. Make sure to install cert-manager in advance.
    >         #It should be disabled only in test environments or if you implement your own mTLS solution like Istio for example.
    >         encryptionEnabled: true
    >         ## Certificate management types cert-manager.io(https://cert-manager.io/docs/) and cert.gardener.cloud(https://github.com/gardener/cert-management) are currently supported
    >         # certManager:
    >             # issuerRef:
    >             ##  The name of the installed cert-manager issuer.
    >             #   name:
    >             ##  The cert-manager custom k8s resource type of the CA - should be one of (Issuer or ClusterIssuer). Only applicable for cert-manager.io.
    >             #   kind:
    >             ##  The namespace of the installed cert-manager issuer(only applicable for cert.gardener.cloud).
    >             #   namespace:
    >             ## Certificate properties are only applicable for cert-manager.io. If specified when using cert.gardener.cloud - will be ignored.
    >             # certificate:
    >               # privateKey:
    >                 ## Check cert-manager private key docs - https://cert-manager.io/docs/reference/api-docs/#cert-manager.io/v1.CertificatePrivateKey
    >                 # algorithm: ECDSA
    >                 ## Check cert-manager private key docs - https://cert-manager.io/docs/reference/api-docs/#cert-manager.io/v1.CertificatePrivateKey
    >                 # encoding: PKCS8
    >                 ## Check cert-manager private key docs - https://cert-manager.io/docs/reference/api-docs/#cert-manager.io/v1.CertificatePrivateKey
    >                 # size: 256
    >               ## The duration for which the certificates will be valid. Minimum accepted duration is 1 hour. Value must be in units accepted by Go time.ParseDuration https://golang.org/pkg/time/#ParseDuration
    >               # duration: 720h
    >               ## How long before the currently issued certificate’s expiry cert-manager should renew the certificate. Value must be in units accepted by Go time.ParseDuration https://golang.org/pkg/time/#ParseDuration
    >               # renewBefore: 120h
    >   ## The mode in which Transparent Proxy operates with the Destinations in the cluster. Possible values are "all" or "labelSelector".
    >   ## If "labelSelector" set, TP operates only in namespaces labeled with "transparent-proxy.connectivity.api.sap/namespace:<namespace where TP is installed in>"
    >   managedNamespacesMode: "all"
    >   manager:
    >     ## The execution interval on which the destination resource updates are fetched and applied to the cluster.
    >     ## It is not advisable to set this value higher than 5 if there are frequent updates on the destinations.
    >     executionIntervalMinutes: 3
    >   integration:
    >     destinationService:
    >       ## Name of the default destination service instance to be used when 'destinationServiceInstanceName' is not provided in the Destination Custom Resource spec.
    >       defaultInstanceName: <default-dest-service-instance-name>
    >       ## The connect timeout used when getting access tokens and destination service clients. [1, 60] seconds allowed.
    >       connectionTimeoutSeconds: 5
    >       ## The read timeout used when getting access tokens and destination service clients. [1, 60] seconds allowed.
    >       readTimeoutSeconds: 10
    >       instances:
    >     ##     Name of the destination service instance that is described. It could be used as config.integration.destinationService.defaultInstanceName or it can be referenced in the Destination Custom Resource spec as destinationServiceInstanceName.
    >           - name: <dest-service-instance-name>
    >             serviceCredentials:
    >     ##         The key in the Destination service secret resource, which holds the base64 encoded value of the destination service key. (info) Make sure to provide the right key for an existing secret. Required when Transparent Proxy should create secret and not required when describing an existing secret.
    >               secretKey: <secret-key>
    >     ##         The name of the existing secret, which holds the credentials for the Destination service or the name of the secret to be created based on "secretName", "secretData", "secretKey" fields.
    >               secretName: <secret-name>
    >     ##         The base64 encoded value of the service key, obtained from the Destination service instance. Required when Transparent Proxy should create secret and not required when describing an existing secret.
    >               secretData: <secret-data>
    >     ##         The namespace of the existing secret to be used, which holds the credentials for the Destination service. This field should not be present if there is no existing secret and Transparent Proxy would create one based on "secretName", "secretData", "secretKey" fields
    >     #          secretNamespace:
    >     #          privateKey:
    >     ##           The name of K8s secret, which holds the private key to authenticate if using an x509-based service key to the Destination service.
    >     #            secretName: x509-svc-key-private-key
    >     ##           The name of the internal key inside the K8s secret holding the private key to authenticate if using an x509-based service key to the Destination service.
    >     #            secretInternalKey: pk.pem
    >     connectivityProxy:
    >       ## The connect timeout is to be used when accessing an HTTP system with ProxyType=OnPremise through the Connectivity Proxy. [1, 60] seconds allowed.
    >       connectionTimeoutSeconds: 1
    > ```




<a name="loiod201be05a4aa444898fd20bcecb1ebbb__section_ucd_m1g_rtb"/>

## Deploy \(DockerHub\)

The Transparent Proxy Helm chart is available in DockerHub.

You can directly install it with one command:

```
helm install transparent-proxy oci://registry-1.docker.io/sapse/transparent-proxy --version <version of helm chart> --namespace <namespace> -f <path-to-values.yaml>
```



<a name="loiod201be05a4aa444898fd20bcecb1ebbb__section_jxx_xbp_y5b"/>

## Deploy from Repository Based Shipment Channel \(RBSC\)

**Registry:** 73554900100900006891.helmsrv.cdn.repositories.cloud.sap

**Tag:** 1.8.0

**Authorization**: See [RBSC documentation](https://help.sap.com/viewer/0a64be17478d4f5ba45d14ab62b0d74c/Cloud/en-US/7e83dfc309834942b441fc2106c5b7f5.html).

```
helm repo add transparent-proxy-helm https://73554900100900006891.helmsrv.cdn.repositories.cloud.sap --username <user> --password <pass>
helm pull transparent-proxy-helm/transparent-proxy --version=<version of helm chart> 
helm repo update
```

\(Optional\) Prepare the Docker image configuration for the repository authentication if want to use a registry different from *docker.io*:

-   Create docker secret:

    ```
    kubectl create secret docker-registry docker-secret --docker-server=73554900100900006891.dockersrv.cdn.repositories.cloud.sap --docker-username=<rbsc-user> --docker-password=<password>
    ```

-   Place the name of secret it in the `values.yaml` for the `deployment.image.pullSecret` property.

    For more information, see [Configuration Guide](configuration-guide-2a22cd7.md).




<a name="loiod201be05a4aa444898fd20bcecb1ebbb__section_sps_m1g_rtb"/>

## Update / Upgrade / Downgrade

> ### Caution:  
> Changing any of the `values.yaml` configurations using *helm upgrade* may result in the restart of some or all Transparent Proxy components.

When you have a Transparent Proxy deployed on the cluster, you may want to maintain it by changing configurations and/or changing its version. To do so, follow these steps:

1.  Get the Transparent Proxy Helm chart. It can be the same version as the one currently installed or a different version that you want to upgrade or downgrade.
2.  Prepare the `values.yaml` file for your scenario, as described in [Configuration](configuration-guide-2a22cd7.md#loio2a22cd7872964e6a9ceb5af72920cfd0__config). Here you can just modify the one you used previously by applying the changes you desire.
3.  Use the Helm CLI to upgrade the Transparent Proxy:

    ```
    helm upgrade transparent-proxy oci://registry-1.docker.io/sapse/transparent-proxy --version <version of helm chart> --namespace <namespace> -f <path-to-new-values.yaml>
    ```




<a name="loiod201be05a4aa444898fd20bcecb1ebbb__section_tk4_p1g_rtb"/>

## Undeploy

If you need to remove the Transparent Proxy from your cluster or from a namespace, you can delete all resources installed by Helm except for the [Custom Resource Definition](https://kubernetes.io/docs/tasks/extend-kubernetes/custom-resources/custom-resource-definitions/) \(CRD\) of type `destinations.destination.connectivity.api.sap` using the Helm CLI:

```
helm uninstall transparent-proxy
```

If you need to remove the CRD of type `destinations.destination.connectivity.api.sap`, you can do it manually using [kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl).

```
kubectl delete crd destinations.destination.connectivity.api.sap
```

This will delete the CRD `destinations.destination.connectivity.api.sap` as well as all custom resources of type `destination.connectivity.api.sap` in the cluster.



<a name="loiod201be05a4aa444898fd20bcecb1ebbb__section_stj_nlc_zxb"/>

## Deploy/Update/Undeploy using Landscaper

To deploy/update/undeploy the Transparent Proxy on a Kubernetes cluster via Landscaper, look at the following [Guided Tour with Landscaper](https://github.com/gardener/landscaper/tree/master/docs/guided-tour). You will need an LAAS instance that you can request from the corresponding team, or launch a local one using the Landscaper CLI.

