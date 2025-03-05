<!-- loio16f63429a2344b8baec1c81cafe5d0fa -->

# Using Service Channels

Configure Cloud Connector service channels to connect your on-premises network to specific services on SAP BTP or to an ABAP Cloud system.



## Context

Cloud Connector service channels provide access from an external network to specific services on SAP BTP, or to an ABAP Cloud system. The called services are not exposed to direct access from the Internet. The Cloud Connector ensures that the connection is always available and communication is secured.


<table>
<tr>
<th valign="top">

Service Channel Type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

**RFC Connection** to an ABAP Cloud system

</td>
<td valign="top">

The service channel for **RFC** supports calls from on-premises systems to an ABAP Cloud system using RFC.

</td>
</tr>
<tr>
<td valign="top">

**K8s Cluster** \(TCP connection to a SAP BTP Kubernetes cluster\)

</td>
<td valign="top">

Service channel to establish a connection to a service in a Kubernetes cluster on SAP BTP.

</td>
</tr>
</table>



## Next Steps

[Configure a Service Channel for RFC](configure-a-service-channel-for-rfc-18602c2.md)

[Configure a Service Channel for a Kubernetes Cluster](configure-a-service-channel-for-a-kubernetes-cluster-d6d395e.md)

**Related Information**  


[Service Channels: Port Overview](service-channels-port-overview-449dbf5.md "A service channel overview lets you see the details of all service channels that are used by a Cloud Connector installation.")

