<!-- loio8b1e1c3b3e284d61bc167e84d4c9d7a1 -->

# User Logon Properties

JCo properties that cover different types of user credentials, as well as the ABAP system client and the logon language.

The currently supported logon mechanism uses user or password as credentials.


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

`jco.client.client`

</td>
<td valign="top">

Represents the client to be used in the ABAP system. Valid format is a three-digit number.

</td>
</tr>
<tr>
<td valign="top">

`jco.client.lang`

</td>
<td valign="top">

Optional property. Represents the logon language. If the property is not provided, the user's or system's default language is used. Valid values are two-character ISO language codes or one-character SAP language codes.

</td>
</tr>
<tr>
<td valign="top">

`jco.client.user`

</td>
<td valign="top">

Represents the user to be used for logging on to the ABAP system. Max. 12 characters long.

> ### Note:  
> When working with the *Destinations* editor in the cockpit, enter the value in the *<User\>* field. Do not enter it as additional property.



</td>
</tr>
<tr>
<td valign="top">

`jco.client.alias_user`

</td>
<td valign="top">

Represents the user to be used for logging on to the ABAP system. Either `jco.client.user` or `jco.client.alias_user` must be specified. The alias user may be up to 40 characters long.

> ### Note:  
> When working with the *Destinations* editor in the cockpit, enter the value in the *<Alias User\>* field. Do not enter it as additional property.



</td>
</tr>
<tr>
<td valign="top">

`jco.client.passwd`

</td>
<td valign="top">

Represents the password of the user that is used.

> ### Note:  
> Passwords in systems of SAP NetWeaver releases lower than 7.0 are case-insensitive and can be only eight characters long. For releases 7.0 and higher, passwords are case-sensitive with a maximum length of 40.

> ### Note:  
> When working with the *Destinations* editor in the cockpit, enter this password in the *<Password\>* field. Do not enter it as additional property.



</td>
</tr>
<tr>
<td valign="top">

`jco.client.tls_client_certificate_logon`

</td>
<td valign="top">

When set to `1`, the client certificate provided by the *KeyStore*, which must be configured in addition, is used for authentication instead of `jco.client.user`/`jco.client.alias_user` and `jco.client.passwd`. This property is only relevant for a connection using WebSocket RFC \(*<Proxy Type\>*=Internet\).

The default value is `0`.

> ### Note:  
> When working with the Destinations editor in the cockpit, the *<User\>*, *<Alias User\>* and *<Password\>* fields are hidden when setting the property to `1`.

For more information on WebSocket RFC, see also:

[WebSocket RFC](https://help.sap.com/viewer/753088fc00704d0a80e7fbd6803c8adb/202009.001/en-US/51f1edadb2754e539f6e6335dd1eb4cc.html)

</td>
</tr>
<tr>
<td valign="top">

`jco.destination.auth_type`

</td>
<td valign="top">

Optional property.

> ### Note:  
> SAP BTP supports the propagation of business users \(principal propagation\) and technical users from the cloud application towards on-premise systems.
> 
> In both cases, a specific access token representing the business user or technical user is retrieved in the RFC runtime \(for example, in JCo or SAP BTP ABAP environment\), which can then be sent to the Connectivity service.
> 
> For more information, see [Authenticating Users against On-Premises Systems](authenticating-users-against-on-premises-systems-b643fbe.md).

-   If the property is not provided, its default value `CONFIGURED_USER` is used. In this case, user, password, or other credentials are specified directly.
-   To enable single sign-on via principal propagation \(an access token representing the business user logged on in the cloud application is forwarded to the on-premise system\), set the value to `PrincipalPropagation`. In this case, you do not need to provide `jco.client.user` and `jco.client.passwd` in the configuration.
-   To enable technical user propagation \(an access token representing the technical user is forwarded to the on-premise system\), set the value to `TechnicalUserPropagation`. In this case, you do not need to provide `jco.client.user` and `jco.client.passwd` in the configuration.

> ### Note:  
> For `PrincipalPropagation`/`TechnicalUserPropagation`, you should configure the properties `jco.destination.repository.user` and `jco.destination.repository.passwd` instead, since there are special permissions needed \(for metadata lookup in the back end\) that not all business/technical users might have.



</td>
</tr>
<tr>
<td valign="top">

`jco.client.tech_user_id`

</td>
<td valign="top">

> ### Note:  
> Only needed for `jco.destination.auth_type`=`TechnicalUserPropagation`.

Client ID of the application.

</td>
</tr>
<tr>
<td valign="top">

`jco.client.tech_user_secret`

</td>
<td valign="top">

> ### Note:  
> Only needed for `jco.destination.auth_type`=`TechnicalUserPropagation`.

Client secret for the Client ID.

</td>
</tr>
<tr>
<td valign="top">

`jco.client.tech_user_service_url`

</td>
<td valign="top">

> ### Note:  
> Only needed for `jco.destination.auth_type`=`TechnicalUserPropagation`.

URL of the token service, against which the token exchange is performed.

> ### Remember:  
> The token service is not accessed through the Cloud Connector, but through the Internet.



</td>
</tr>
</table>

