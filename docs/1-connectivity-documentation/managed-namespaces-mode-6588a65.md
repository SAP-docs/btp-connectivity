<!-- loio6588a65269bd45a297ebcd6a3baef157 -->

# Managed Namespaces Mode

Manage namespaces for the Transparent Proxy for Kubernetes.

The Transparent Proxy can operate in either:

-   All namespaces in the cluster, or
-   Only in namespaces labeled in the following way: *transparent-proxy.connectivity.api.sap/namespace:<namespace where Transparent Proxy is installed\>*.

To configure this feature, set the Helm property `config.managedNamespacesMode` to either:

-   `all`

    This is the default setting, indicating the proxy operates with destination custom resources across all namespaces in the cluster.

-   `labelSelector`

    Restricting the proxy to operate only in namespaces with the specific label.


For more information, see [Configuration Guide](configuration-guide-2a22cd7.md).

