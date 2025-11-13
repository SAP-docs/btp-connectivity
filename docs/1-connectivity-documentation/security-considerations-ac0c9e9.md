<!-- loioac0c9e994a754ffcbc4d7061f1c6549d -->

# Security Considerations

Recommended security measures for the Transparent Proxy for Kubernetes.



## Kubernetes Resources Managed by Transparent Proxy

The Transparent Proxy manages *Transparent Proxy Custom Resources*, *Destination Custom Resources*, and *Config Map* resources. All Kubernetes resources require comprehensive protection to keep your cluster secure against both external threats and insider misuse, by enforcing strong RBAC, encryption, and auditing.

**Recommended Security Practices**

Implement these cluster-wide security measures for comprehensive protection for the resources above:

**Access Control**

-   **Enforce least privilege** for all users, service accounts, and controllers
-   Configure proper RBAC policies to control the access for all resources managed by the Transparent Proxy
-   Regularly review and audit permissions

**Encryption & Communication**

-   **Enable TLS everywhere** - API server, *kubelet*, and *etcd* communications
-   **Turn on *etcd* encryption at rest** for all cluster data
-   Use secure communication channels for all cluster operations

**Monitoring & Auditing**

-   **Enable comprehensive audit logging** for all API operations
-   **Ship logs to a centralized system** for monitoring and analysis
-   Set up monitoring dashboards for configuration changes
-   Implement alerting for unusual activity patterns



## Kubernetes Watch Events

The Transparent Proxy listens for **ADDED**, **MODIFIED**, and **DELETED** events for its relevant resources, which are emitted by the Kubernetes API server when resource changes occur.

The Transparent Proxy implements efficient reconciliation which first compares the relevant fields of the resource to the current state. If no meaningful change has occurred, it exits early without performing expensive operations.

Kubernetes has built-in rate limiting that automatically restricts how many API requests can be processed at once. In case of excessive API calls, Kubernetes will automatically throttle the requests, protecting applications from being flooded with too many events to handle.

**Recommended Security Practices**

-   Define default CPU and memory limits for the Transparent Proxy deployment. This contains the blast radius of any potential resource exhaustion, ensuring the controller cannot cause a node-level DoS.
-   Configure proper RBAC policies to control all Kubernetes resources managed by the Transparent Proxy.

