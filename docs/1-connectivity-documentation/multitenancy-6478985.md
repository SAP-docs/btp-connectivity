<!-- loio6478985d12a54d7ab8a4e5abce3972e0 -->

# Multitenancy

Use multitenancy for the transparent proxy for Kubernetes.

The transparent proxy works in two tenant modes: *dedicated* and *shared*. You can change the mode by modifying the Helm property `.config.tenantMode`.

For more information, see [Configuration Guide](configuration-guide-2a22cd7.md).

-   In the *dedicated* tenant mode, the transparent proxy exposes destinations only from the linked Destination service instance and its subaccount. Requests to the transparent proxy remain unchanged.
-   In the *shared* tenant mode, the transparent proxy exposes destinations from any subscribed tenant.



<a name="loio6478985d12a54d7ab8a4e5abce3972e0__section_f4t_vxx_yzb"/>

## HTTP

When requesting a destination through the transparent proxy in shared tenant mode, you must pass the `X-Tenant-Subdomain: <tenant-subdomain>` or `X-Tenant-Id: <tenant-id>` header.

A tenant is successfully onboarded when it is visible in the destination custom resource status. The onboarding of a tenant is dynamic and happens during the first request on behalf of that tenant.



<a name="loio6478985d12a54d7ab8a4e5abce3972e0__section_lk3_vxx_yzb"/>

## Non-HTTP

Tenants are configured in the destination custom resource \(CR\) as an annotation with the key `transparent-proxy.connectivity.api.sap/tenant-subdomains`. The value should be a JSON array of tenant subdomains:

```
"transparent-proxy.connectivity.api.sap/tenant-subdomains": '["tenantSubdomain1", "tenantSubdomain2", ...]'
```

The transparent proxy will create a [Kubernetes Service](https://kubernetes.io/docs/concepts/services-networking/service/) for each of the tenants described in the `transparent-proxy.connectivity.api.sap/tenant-subdomains` annotation. The names of the Kubernetes services will be: `<destination-cr-name>-<tenant-subdomain>`.

Each tenant is successfully onboarded when it is visible in a Destination CR status.

