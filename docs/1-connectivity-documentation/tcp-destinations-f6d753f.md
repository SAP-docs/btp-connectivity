<!-- loiof6d753f031a7482dac7a60bad815e07c -->

# TCP Destinations

Create and manage SAP BTP destinations using the TCP protocol for communication.

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

*<virtual\_host\>:<virtual\_port\>* of the on-premise application or or <host\>:<port\> of the Internet application. The address may use *tcp://* as protocol scheme.

</td>
</tr>
<tr>
<td valign="top">

ProxyType

</td>
<td valign="top">

`Internet`, `OnPremise`, or `PrivateLink`

</td>
</tr>
</table>



