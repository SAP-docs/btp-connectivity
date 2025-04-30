<!-- loio96fc958c23a546e0b2ac55e111aedf6c -->

# Security \(Proxy Authorization\)

Perform proxy authorization for the Connectivity Proxy for Kubernetes.

An important aspect of using the Connectivity Proxy is the proxy authorization, that is, how the access to the proxy is controlled \(protected\), enabling the callers to reach out to on-premise systems exposed via the Cloud Connector.

As described in [Operational Modes](operational-modes-148bbad.md), there are two major categories for consideration: The level of trust in the environment, and the *type of tenancy* \(single vs multi-tenant\). This helps you prevent unwanted callers and is especially useful in scenarios where calls to the proxy can originate from workloads outside of your control, or if you simply want to apply stricter rules.

The authorization of the Connectivity Proxy is based on OAuth and it is provided via integration with the SAP UAA \(aka XSUAA\) service acting as an OAuth server. For a successful authorization request, a JSON Web token \(JWT\) must be sent to the Connectivity Proxy, for which the following is valid:

-   Issued by XSUAA
-   Not expired
-   Passes the signature verification \(the Connectivity Proxy takes care to get the token keys from XSUAA for offline JWT verification\).
-   Its `client_id` \(the client ID of the OAuth client which is part of the respective XSUAA service instance credentials\) matches the allowed client ID in the Connectivity Proxy configuration.

    ```
    config:
      servers:
        proxy:
          authorization:
            oauth:
              allowedClientId: "the client id which is allowed as JWT issuer for proxy authorization"
    ```


> ### Tip:  
> The service instance used to protect the Connectivity Proxy can be any XSUAA service instance.

> ### Note:  
> Based on the above info, the Connectivity Proxy can be protected with the very same service instance you use to perform the user login flow for your application. In this case, you can reuse the login token. However, to achieve separation of concerns, we recommend that you use a dedicated service instance to protect the Connectivity Proxy.



<a name="loio96fc958c23a546e0b2ac55e111aedf6c__section_c3c_nr2_1qb"/>

## Multi-Tenancy and Subscriptions

An important aspect of the proxy authorization is that, when enabled, it is also used to pass the tenant context for the request to the Connectivity Proxy. When you fetch a token for proxy authorization, make sure you do so on behalf of the *correct* tenant, over which you want to call the Connectivity Proxy.

In cases of multi-tenancy, or single-tenancy where the proxy-protecting instance is created in a tenant that is *different* from the one for which the proxy is dedicated, you must *ensure subscriptions* between this tenant and the proxy-protecting instance to fetch a token on behalf of the correct tenant.

