<!-- loiof6d753f031a7482dac7a60bad815e07c -->

# TCP Destinations

Create and manage SAP BTP destinations using the TCP protocol for communication.

> ### Note:  
> The on-premise use cases described in this guide are also applicable to virtual private cloud \(VPC\) environments.



## Properties

To configure a destination of this authentication type, you must specify all the required properties.


<table>
<tr>
<th valign="top">

Cockpit Label

</th>
<th valign="top">

JSON Key

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

**Required**

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Name

</td>
<td valign="top">

`Name` 

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

`Type`

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

`Address` 

</td>
<td valign="top">

*<virtual\_host\>:<virtual\_port\>* of the on-premise application or or <host\>:<port\> of the Internet application. The address may use *tcp://* as protocol scheme.

</td>
</tr>
<tr>
<td valign="top">

Proxy Type

</td>
<td valign="top">

`ProxyType` 

</td>
<td valign="top">

`Internet`, `OnPremise`, or `PrivateLink`

</td>
</tr>
<tr>
<td valign="top" colspan="3">

**Additional**

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

**Key**

</td>
<td valign="top">

**Description**

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

`tcp.nodelay`

</td>
<td valign="top">

Activates or deactivates TCP delay.

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

`tcp.socket.linger`

</td>
<td valign="top">

Sets the linger state of the associated socket.

The linger state specifies whether and for how long a socket maintains the connection after calling the `Close()` method if there is still data to be sent.

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

`tcp.socket.sndbuf`

</td>
<td valign="top">

*Send* buffer size in Bytes.

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

`tcp.socket.rcvbuf`

</td>
<td valign="top">

*Receive* buffer size in Bytes.

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

`tcp.socket.timeout`

</td>
<td valign="top">

Amount of time the TCP client waits for a *send* or *receive* operation to complete successfully.

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

`tcp.socket.keepalive`

</td>
<td valign="top">

Specifies if *keepalive* messages can be sent.

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

`tcp.socket.reuseaddr`

</td>
<td valign="top">

Specifies if a TCP server can bind to an address to prevent multiple servers from binding to the same address.

</td>
</tr>
</table>

