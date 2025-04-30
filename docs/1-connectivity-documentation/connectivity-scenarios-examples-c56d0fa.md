<!-- loioc56d0fa91f474347aa569311d0d15044 -->

# Connectivity Scenarios: Examples

Find some typical examples for Connectivity scenarios and the corresponding Connectivity services, components and processes needed.

> ### Note:  
> The on-premise use cases described in this guide are also applicable to virtual private cloud \(VPC\) environments.



<a name="loioc56d0fa91f474347aa569311d0d15044__section_kk1_vtv_x2c"/>

## Cloud to Cloud

**Connecting Cloud Foundry Applications to Cloud Systems**

You can consume a cloud service or system from SAP BTP, Cloud Foundry environment. Use the Destination service to store and manage your connection configuration data \(including credentials, certificates, URL, headers, queries, etc.\) at design time, and automate the OAuth2 token retrieval process at runtime for your application.

For more information, see [Destination Service](destination-service-8ff5483.md).

**Connecting Kubernetes Applications to Cloud Systems**

You can consume a cloud service or system from your Kubernetes environment. Use the Transparent Proxy for Kubernetes to enhance developers' user experience and simplify the consumption of end systems. For example:

-   Developing an application that requires consumption of an SAP HANA database.
-   Adding new functionality that requires the consumption of an SAP BTP service.
-   Creating new SAP Fiori-based user interfaces that require consumption of an ODата service.
-   Adding new functionality that requires integration with third-party APIs.
-   An application requires data exchange or service consumption via a RESTful API.

For more information, see [Transparent Proxy for Kubernetes](transparent-proxy-for-kubernetes-acc64ad.md).



<a name="loioc56d0fa91f474347aa569311d0d15044__section_slw_5tv_x2c"/>

## Cloud to On-Premise

**Connecting Cloud Foundry Applications to On-Premise Systems**

You can consume an on-premise system from SAP BTP, Cloud Foundry environment. Use the Connectivity service and the Cloud Connector to implement a specific scenario. For example:

-   Creating new SAP Fiori-based user interfaces that require consumption of an ODата service.
-   An application requires data exchange or service consumption via a RESTful API.
-   Extending an application that requires consumption of an ABAP system via RFC.
-   Develop an application that requires interaction with a mail server for E-mail operations.
-   Develop an application that requires interaction with a relational or non-relational database \(e.g. SAP HANA, MySQL, PostgreSQL, MongoDB\).
-   A new functionality in an application requires user authentication and directory services integration using an LDAP server.
-   An application needs to transfer files to and from an FTP server.
-   Enable single sign-on \(SSO\) by forwarding the identity of cloud users to a remote system or service \(user propagation / principal propagation\).

For more information, see [Connectivity Service](connectivity-service-bd2d4f4.md), [Destination Service](destination-service-8ff5483.md), [Cloud Connector](cloud-connector-e6c7616.md), [Principal Propagation](principal-propagation-e2cbb48.md).

**Connecting Kubernetes Applications to On-Premise Systems**

You can consume an on-premise system from your SAP Kyma, or any other Kubernetes environment. Use the Connectivity Service, Connectivity Proxy, Transparent Proxy, and Cloud Connector to implement a specific scenario. For example:

-   Creating new SAP Fiori-based user interfaces that require consumption of an ODата service.
-   An application requires data exchange or service consumption via a RESTful API.
-   Extending an application that requires consumption of APIs in an ABAP system via RFC.
-   Develop an application that requires interaction with a mail server for E-mail operations.
-   Develop an application that requires interaction with a relational or non-relational database \(e.g. HANA, MySQL, PostgreSQL, MongoDB\).
-   A new functionality in an application requires user authentication and directory services integration using an LDAP server.
-   An application needs to transfer files to and from an FTP server.
-   Enable single sign-on \(SSO\) by forwarding the identity of cloud users to a remote system or service \(user propagation / principal propagation\).

For more information, see [Connectivity Service](connectivity-service-bd2d4f4.md), [Destination Service](destination-service-8ff5483.md), [Connectivity Proxy for Kubernetes](connectivity-proxy-for-kubernetes-e661713.md), [Transparent Proxy for Kubernetes](transparent-proxy-for-kubernetes-acc64ad.md), [Cloud Connector](cloud-connector-e6c7616.md), [Principal Propagation](principal-propagation-e2cbb48.md).



<a name="loioc56d0fa91f474347aa569311d0d15044__section_bxq_5tv_x2c"/>

## On-Premise to Cloud \(Service Channels\)

You can connect to a cloud service from your on-premise network using service channels of the Cloud Connector. For example:

-   Configure an RFC connection from your on-premise system to SAP S/4HANA Cloud.

    For scenarios that need to call from on-premise systems to SAP BTP, ABAP environment using RFC, you can establish a connection to an ABAP Cloud tenant host.


-   Configure a connection to a service in a Kubernetes cluster.

    Create a service channel to establish a connection to a service in a Kubernetes cluster that is not directly exposed to external access.


For more information, see [Using Service Channels](using-service-channels-16f6342.md).

