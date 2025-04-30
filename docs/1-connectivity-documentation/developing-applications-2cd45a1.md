<!-- loio2cd45a1a110542239fb3591089fab8e7 -->

# Developing Applications

Find information on Connectivity concepts, scenarios, and components to develop your SAP BTP application.

> ### Note:  
> The on-premise use cases described in this guide are also applicable to virtual private cloud \(VPC\) environments.


<table>
<tr>
<th valign="top">

Task

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

[Concepts](concepts-ebffc82.md)

</td>
<td valign="top">

Find information on basic concepts of SAP BTP Connectivity.

</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Connectivity Scenarios**

</td>
</tr>
<tr>
<td valign="top">

[Principal Propagation](principal-propagation-e2cbb48.md)

</td>
<td valign="top">

Forward the identity of a cloud user to a remote system. This process is called principal propagation \(also known as user propagation or user principal propagation\).

</td>
</tr>
<tr>
<td valign="top">

[Invoking ABAP Function Modules via RFC](invoking-abap-function-modules-via-rfc-fa4adc9.md)

</td>
<td valign="top">

Call a remote-enabled function module \(RFM\) in an on-premise or cloud ABAP server from your Cloud Foundry application, using the RFC protocol.

</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Components**

</td>
</tr>
<tr>
<td valign="top">

[Consuming the Connectivity Service](consuming-the-connectivity-service-313b215.md)

</td>
<td valign="top">

Connect your Cloud Foundry application to an on-premise system.

</td>
</tr>
<tr>
<td valign="top">

[Consuming the Destination Service](consuming-the-destination-service-7e30625.md)

</td>
<td valign="top">

Retrieve and store technical information about the destination that is required to consume a target remote service from your application.

</td>
</tr>
<tr>
<td valign="top">

[Using the Connectivity Proxy](using-the-connectivity-proxy-f3c1ef4.md)

</td>
<td valign="top">

Use the Connectivity Proxy for Kubernetes to connect workloads on a Kubernetes cluster to on-premise systems.

The Connectivity Proxy offers multiple proxy endpoints which are communication protocol-specific: TCP \(via SOCKS5\), HTTP, RFC \(invoking ABAP functions\), and LDAP.

</td>
</tr>
<tr>
<td valign="top">

[Using the Transparent Proxy](using-the-transparent-proxy-c5257cf.md)

</td>
<td valign="top">

Use the Transparent Proxy for Kubernetes to connect workloads on a Kubernetes cluster to Internet or on-premise applications.

The Transparent Proxy lightens the way your Kubernetes workloads connect to remote systems using BTP destinations of type `Internet` and `OnPremise`.

</td>
</tr>
</table>

