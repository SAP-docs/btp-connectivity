<!-- loiob643fbecb14e4c89ab3c03b21200cb08 -->

# Authenticating Users against On-Premises Systems

Authentication types supported by the Cloud Connector.

Currently, the Cloud Connector supports **basic authentication**, **principal propagation**, and **technical user propagation** as user authentication types towards internal systems. The destination configuration of the used cloud application defines which of these types is used for the actual communication to an on-premises system through the Cloud Connector, see [Managing Destinations](managing-destinations-84e45e0.md).

-   To use **basic authentication**, configure an on-premises system to accept basic authentication and to provide one or multiple service users. No additional steps are necessary in the Cloud Connector for this authentication type.
-   To use **principal propagation** or **technical user propagation**, you must explicitly configure trust to those cloud entities from which user tokens are accepted as valid.

    For more information, see [Configuring Principal Propagation](configuring-principal-propagation-c84d4d0.md) and [Configuring Technical User Propagation](configuring-technical-user-propagation-b62e588.md).

-   When using HTTP as communication protocol, you can also perform a logon using the Cloud Connector system certificate, if there is no principal provided by the cloud side. The access control entry must be configured for this.

    > ### Note:  
    > For HTTP, also some other token-based authentication methods might work between the cloud application and the backend, depending on the backend capabilities.


**Related Information**  


[Configuring Principal Propagation](configuring-principal-propagation-c84d4d0.md "Use principal propagation to simplify the access of SAP BTP users to on-premises systems.")

[Configuring Technical User Propagation](configuring-technical-user-propagation-b62e588.md "Use technical user propagation to provide access of technical users to on-premises systems.")

