<!-- loiof6d753f031a7482dac7a60bad815e07c -->

# TCP Destinations

Create and manage SAP BTP destinations using the TCP protocol for communication.

> ### Note:  
> Currently, you can create and manage TCP destinations only via the Destination service REST API.
> 
> For more information, see [Destination Service REST API](destination-service-rest-api-23ccafb.md).

> ### Note:  
> The on-premise use cases described in this guide are also applicable to virtual private cloud \(VPC\) environments.

**Mandatory Destination Configuration Fields**


<table>
<tr>
<th valign="top">

Property

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

Name

</td>
<td valign="top">

Destination name

</td>
</tr>
<tr>
<td valign="top">

Type

</td>
<td valign="top">

Destination type. Use `TCP`.

</td>
</tr>
<tr>
<td valign="top">

Address

</td>
<td valign="top">

<virtual\_host\>:<virtual\_port\> of the on-premise application

</td>
</tr>
<tr>
<td valign="top">

ProxyType

</td>
<td valign="top">

`OnPremise`

</td>
</tr>
</table>

