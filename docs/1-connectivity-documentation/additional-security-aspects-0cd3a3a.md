<!-- loio0cd3a3acb120485bb808d3ff3a939e79 -->

# Additional Security Aspects

Considerations on security for the traffic flow and configuration of the Connectivity Proxy for Kubernetes.



<a name="loio0cd3a3acb120485bb808d3ff3a939e79__section_aks_ckm_1qb"/>

## Security of Traffic Flow *within* a Cluster

This section refers to the traffic flow between a workload from a Kubernetes cluster and the Connectivity Proxy running in the same cluster.

The traffic between a workload running in the cluster and the HTTP and LDAP/RFC proxies is not encrypted. The traffic to the SOCKS5 proxy can be SSL-encrypted if the client application initiates an SSL connection. The HTTP and LDAP/RFC proxies are disabled by default for a Connectivity Proxy installation. If you want to enable them, add the following configuration in the `values.yml` file:

```
config:
  servers:
    proxy:
      rfcAndLdap:
        enabled: true
      http:
        enabled: true
```

> ### Note:  
> All business data that is transmitted between the Connectivity Proxy in the cluster and the Cloud Connector is sent over an SSL-encrypted tunnel.



<a name="loio0cd3a3acb120485bb808d3ff3a939e79__section_bks_ckm_1qb"/>

## Security of Traffic Flow *from Outside* a Cluster

This section refers to the traffic flow between the Cloud Connector and the Connectivity Proxy running in a Kubernetes cluster.

By default, the connections between the Cloud Connector and the Ingress load balancer in the Kubernetes cluster are SSL-encrypted. If you want to enable mutual TLS for the connections from the Ingress to the Connectivity Proxy or have ent-to-end mutual TLS between the Cloud Connector and the Connectivity Proxy, follow the procedures described in [Mutual TLS](mutual-tls-7ce7883.md).



<a name="loio0cd3a3acb120485bb808d3ff3a939e79__section_srq_zjm_1qb"/>

## Security of Connectivity Proxy Configuration Data

This section refers to any security-sensitive configuration data which is required for the Connectivity Proxy.

The Connectivity Proxy installation requires some configuration data to be supplied via a Kubernetes secret.

By default, the Kubernetes secrets are stored as unencrypted base64-encoded strings and are transmitted in base64-encoded format, so they are basically accessible by persons with access to the cluster.

See the [Kubernetes documentation](https://kubernetes.io/docs/concepts/configuration/secret/) for details on how to secure the usage of secrets in a cluster.

