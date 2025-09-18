<!-- loio60c0a459311942ae89312976cdd684dc -->

# Lifecycle Management

Use the Connectivity Proxy image and the Connectivity Proxy Helm chart to manage the life cycle of the Connectivity Proxy for Kubernetes.

The Connectivity Proxy delivery includes the following main components:

-   [Connectivity Proxy Image](lifecycle-management-60c0a45.md#loio60c0a459311942ae89312976cdd684dc__image): the functional component that packages all the binaries and utilities.
-   [Connectivity Proxy Helm Chart](lifecycle-management-60c0a45.md#loio60c0a459311942ae89312976cdd684dc__chart): used for configuring and managing the life cycle of the Connectivity Proxy via the popular Helm package manager. For more information, see [Operations via Helm](operations-via-helm-23fc110.md).



<a name="loio60c0a459311942ae89312976cdd684dc__image"/>

## Connectivity Proxy Image

The Connectivity Proxy image is a standard Docker image containing all the required binaries for the Connectivity Proxy. This includes the Connectivity Proxy binaries themselves, a JVM \(SapMachine\), and other important utilities.

**Connectivity Proxy Image in DockerHub**

The Connectivity Proxy image is available via the DockerHub image repository, see [https://hub.docker.com/r/sapse/connectivity-proxy](https://hub.docker.com/r/sapse/connectivity-proxy).

**Pull information** \(for the latest version\):

-   **Registry**: docker.io
-   **Repository**: sapse/connectivity-proxy
-   **Tag**: 2.18.0

**Example**:

> ### Sample Code:  
> ```
> docker pull docker.io/sapse/connectivity-proxy:2.18.0
> 
> ```

**Connectivity Proxy Image in the Repository-Based Shipment Channel \(RBSC\)**

The Connectivity Proxy image is available via the RBSC docker image repository. This requires having an S-user with associated licenses.

> ### Note:  
> Contact your account manager to clarify access to the repository.

**Pull information** \(for the latest version\):

-   **Registry**: 73554900100900005672.dockersrv.cdn.repositories.cloud.sap
-   **Repository**: com.sap.cloud.connectivity/connectivity-proxy
-   **Tag**: 2.18.0
-   **Authorization**: see [Manage Technical Users in SAP Repositories Management](https://help.sap.com/viewer/0a64be17478d4f5ba45d14ab62b0d74c/Cloud/en-US/7e83dfc309834942b441fc2106c5b7f5.html) \(RBSC documentation\).

**Example**:

```
docker pull 73554900100900005672.dockersrv.cdn.repositories.cloud.sap/com.sap.cloud.connectivity/connectivity-proxy:2.18.0

```

[Back to Top](lifecycle-management-60c0a45.md#loio60c0a459311942ae89312976cdd684dc__top)



<a name="loio60c0a459311942ae89312976cdd684dc__chart"/>

## Connectivity Proxy Helm Chart

The Connectivity Proxy delivery also includes a Helm chart that you can use for life cycle management. It is the recommended way to perform life cycle management. The Connectivity Proxy Helm provides full configuration capabilities via the standard Helm method of a `values.yaml` file \(see [Configuration Guide](configuration-guide-eaa8204.md)\).

**Connectivity Proxy Helm Chart in the Repository-Based Shipment Channel \(RBSC\)**

The Connectivity Proxy Helm chart is available via the RBSC Helm repository. This requires having an S-user with associated licenses.

> ### Note:  
> Contact your account manager to clarify access to the repository.

**Pull information** \(for the latest version\):

-   **Registry**: 73554900100900005672.helmsrv.cdn.repositories.cloud.sap
-   **Repository**: com.sap.cloud.connectivity/connectivity-proxy
-   **Tag**: 2.18.0
-   **Authorization**: see [Manage Technical Users in SAP Repositories Management](https://help.sap.com/viewer/0a64be17478d4f5ba45d14ab62b0d74c/Cloud/en-US/7e83dfc309834942b441fc2106c5b7f5.html) \(RBSC documentation\).

**Example**:

```
helm repo add connectivity https://73554900100900005672.helmsrv.cdn.repositories.cloud.sap --username <user> --password <pass>
helm pull connectivity/connectivity-proxy --version=
```

[Back to Top](lifecycle-management-60c0a45.md#loio60c0a459311942ae89312976cdd684dc__top)

**Related Information**  


[Operations via Helm](operations-via-helm-23fc110.md "Use the Helm chart to configure and manage the life cycle of the Connectivity Proxy for Kubernetes.")

[Operations via Separate YAML Files](operations-via-separate-yaml-files-2b0002b.md "Using separate YAML files to configure and manage the life cycle of the Connectivity Proxy for Kubernetes.")

[Configuration Guide](configuration-guide-eaa8204.md "Find an overview of configuration parameters for the Connectivity Proxy for Kubernetes.")

[Additional Security Aspects](additional-security-aspects-0cd3a3a.md "Considerations on security for the traffic flow and configuration of the Connectivity Proxy for Kubernetes.")

[Sizing Recommendations](sizing-recommendations-204822a.md "Find basic sizing guidance for the Connectivity Proxy for Kubernetes.")

