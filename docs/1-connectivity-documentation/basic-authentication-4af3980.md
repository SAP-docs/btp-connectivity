<!-- loio4af3980f96fc467a8f0edad2c7f23f2f -->

# Basic Authentication

Create and configure a *Basic Authentication* destination for an application.

Authentication type *Basic Authentication* is used for destinations that refer to a service on the Internet, an on-premise system, or a *Private Link* endpoint that requires basic authentication.



## Properties

To configure a destination of this authentication type, you must specify all the required properties.

> ### Caution:  
> Do not use your *own personal credentials* in the *<User\>* and *<Password\>* fields. Always use a *technical user* instead.


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
<td valign="top" colspan="2">

**Required**

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

Destination name. Must be unique for the destination level.

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

Destination type. Use `HTTP` as value for all HTTP\(S\) destinations.

</td>
</tr>
<tr>
<td valign="top">

URL

</td>
<td valign="top">

`URL`

</td>
<td valign="top">

URL of the protected resource on the called application.

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

`Internet`, `OnPremise`, or `PrivateLink`.

</td>
</tr>
<tr>
<td valign="top">

Authentication

</td>
<td valign="top">

`Authentication`

</td>
<td valign="top">

Authentication type. Use `BasicAuthentication` as value.

</td>
</tr>
<tr>
<td valign="top">

User

</td>
<td valign="top">

`User` 

</td>
<td valign="top">

User name of the *technical* user to be used.

</td>
</tr>
<tr>
<td valign="top">

Password

</td>
<td valign="top">

`Password` 

</td>
<td valign="top">

Password of the *technical* user to be used.

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

`Preemptive`

</td>
<td valign="top">

If this property is not set or is set to `TRUE` \(that is, the default behavior is to use preemptive sending\), the authentication token is sent preemptively. Otherwise, it relies on the challenge from the server \(401 HTTP code\). The default value \(used if no value is explicitly specified\) is `TRUE`. For more information about preemptiveness, see [http://tools.ietf.org/html/rfc2617\#section-3.3](http://tools.ietf.org/html/rfc2617#section-3.3).

</td>
</tr>
</table>

> ### Note:  
> When a destination is using the HTTPS protocol to connect to a Web resource, the JDK truststore is used as truststore for the destination.

> ### Note:  
> `Basic Authentication` can be used in combination with `ProxyType`=`OnPremise`. In this case, also the `CloudConnectorLocationId` property can be specified. You can connect multiple Cloud Connectors to a subaccount as long as their location ID is different. The value defines the location ID identifying the Cloud Connector over which the connection shall be opened. The default value is the empty string identifying the Cloud Connector that is connected without any location ID.

The response for "find a destination" contains an `authTokens` object in the format given below. For more information on the fields in `authTokens`, see ["Find a Destination" Response Structure](find-a-destination-response-structure-83a3f3b.md).

> ### Sample Code:  
> ```
> "authTokens": [
> 						{
> 						"type": "Basic",
> 						"value": "dGVzdDpwYXNzMTIzNDU=",
> 						"http_header": {
> 						"key":"Authorization",
> 						"value":"Basic dGVzdDpwYXNzMTIzNDU="
> 						}
> 						}
> 						]
> ```

