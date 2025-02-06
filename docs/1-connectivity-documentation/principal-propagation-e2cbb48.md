<!-- loioe2cbb48def4342048362039cc157b12e -->

# Principal Propagation

Enable single sign-on \(SSO\) by forwarding the identity of cloud users to a remote system or service.

The Connectivity and Destination services let you forward the identity of a cloud user to a remote system. This process is called principal propagation \(also known as *user propagation* or *user principal propagation*\). It uses a JSON Web token \(JWT\) as exchange format for the user information.

Two scenarios are supported: Cloud to on-premise \(using the Connectivity service\) and cloud to cloud \(using the Destination service\).

-   [Scenario: Cloud to On-Premise](scenario-cloud-to-on-premise-70b8ef3.md): The user is propagated from a cloud application to an on-premise system using a destination configuration with authentication type `PrincipalPropagation`.

    > ### Note:  
    > This scenario requires the Cloud Connector to connect to your on-premise system.

    > ### Note:  
    > The on-premise use cases described in this guide are also applicable to virtual private cloud \(VPC\) environments.


-   [Scenario: Cloud to Cloud](scenario-cloud-to-cloud-65b11d4.md): The user is propagated from a cloud application to another remote \(cloud\) system using a destination configuration with authentication type `OAuth2SAMLBearerAssertion`.

For more information on setting up destinations, see:

-   [Create HTTP Destinations](create-http-destinations-783fa1c.md)
-   [Create RFC Destinations](create-rfc-destinations-9b3cc68.md)

