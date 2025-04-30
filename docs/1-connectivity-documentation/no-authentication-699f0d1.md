<!-- loio699f0d10fdaf41a8b92367036a7ed1ff -->

# No Authentication

Create and configure a *No Authentication* destination for an application.

This authentication type is used for destinations that refer to a service on the Internet, an on-premise system, or a *Private Link* endpoint that does not require authentication. The relevant property value is:


<table>
<tr>
<td valign="top">

`Authentication`=`NoAuthentication`

</td>
</tr>
</table>



> ### Note:  
> When a destination is using HTTPS protocol to connect to a Web resource, the JDK truststore is used as truststore for the destination.

> ### Note:  
> `No Authentication` can be used in combination with `ProxyType`=`OnPremise`. In this case, also the `CloudConnectorLocationId` property can be specified. You can connect multiple Cloud Connectors to a subaccount as long as their location ID is different. The value defines the location ID identifying the Cloud Connector over which the connection shall be opened. The default value is the empty string identifying the Cloud Connector that is connected without any location ID.

