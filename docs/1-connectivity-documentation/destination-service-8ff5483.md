<!-- loio8ff5483fef564eae9f34fe092d1bddcd -->

# Destination Service

Learn how to manage destinations and consume the Destination service in SAP BTP, multi-cloud foundation.

> ### Note:  
> The on-premise use cases described in this guide are also applicable to virtual private cloud \(VPC\) environments.

The Destination service lets you find the information that is required to access a remote service or system from your cloud application.

-   For the connection to an on-premise system, you can use this service together with the Connectivity service.
    -   For Kubernetes environments, use the Destination service, the Connectivity Proxy and the Transparent Proxy for connections to the target system.

-   For the connection to any other Web application, you can use the Destination service without the Connectivity service.
    -   For Kubernetes environments, use the Destination service and the Transparent Proxy for automated and seamless connections to the target system.

-   Manages routing and authentication details, as well as custom scenario-specific parameters.
-   Performs authentication flows based on the configured details.


<table>
<tr>
<td valign="top">

[Destination Service: Administration](destination-service-administration-29925f2.md)

</td>
<td valign="top">

Manage the Destination service in SAP BTP, multi-cloud foundation.

</td>
</tr>
<tr>
<td valign="top">

[Consuming the Destination Service](consuming-the-destination-service-7e30625.md)

</td>
<td valign="top">

Retrieve and store technical information about the destination to consume a target remote service from your application.

</td>
</tr>
</table>

**Related Information**  


[Getting Started](getting-started-daca64d.md "Use SAP BTP Connectivity for your application in the multi-cloud foundation: available services, components and use cases.")

[Connectivity Service](connectivity-service-bd2d4f4.md "Learn how to manage and consume the Connectivity service in SAP BTP, multi-cloud foundation.")

[Cloud Connector](cloud-connector-e6c7616.md "Learn more about the Cloud Connector: features, scenarios and setup.")

[Connectivity Proxy for Kubernetes](connectivity-proxy-for-kubernetes-e661713.md "Use the Connectivity Proxy for Kubernetes to connect workloads on a Kubernetes cluster to on-premise systems.")

[Transparent Proxy for Kubernetes](transparent-proxy-for-kubernetes-acc64ad.md "Use the Transparent Proxy for Kubernetes to connect workloads on a Kubernetes cluster to Internet and on-premise applications.")

