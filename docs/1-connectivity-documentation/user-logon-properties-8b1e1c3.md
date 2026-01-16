<!-- loio8b1e1c3b3e284d61bc167e84d4c9d7a1 -->

# User Logon Properties

Configure user logon properties for RFC destinations in the SAP BTP cockpit.

User logon properties for RFC destinations cover different types of user credentials, as well as the ABAP system client and the logon language.

The currently supported logon mechanism uses *user* and *password* as credentials.

In the *Destinations* editor, you can configure the user logon properties for a destination in section *Authentication* of the *Destination Details* panel.


<table>
<tr>
<th valign="top">

Label in Destinations Editor

</th>
<th valign="top">

Property

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

Logon Language

</td>
<td valign="top">

`jco.client.lang`

</td>
<td valign="top">

Optional property. Represents the logon language. If the property is not provided, the user's or system's default language is used. Valid values are two-character ISO language codes or one-character SAP language codes.

</td>
</tr>
<tr>
<td valign="top">

User

</td>
<td valign="top">

`jco.client.user`

</td>
<td valign="top">

Represents the user to be used for logging on to the ABAP system.

> ### Note:  
> *Authentication Type* must be set to `CONFIGURED_USER`.

The value is case-insensitive and the maximum length is 12 characters.

> ### Caution:  
> When *Proxy Type* is set to `Internet` \(that is, a WebSocket RFC connection\), the checkbox *Use TLS client certificate login* must be unchecked to see the input field in the *Destinations* editor.



</td>
</tr>
<tr>
<td valign="top">

Alias User

</td>
<td valign="top">

`jco.client.alias_user`

</td>
<td valign="top">

Represents the user to be used for logging on to the ABAP system.

> ### Note:  
> *Authentication Type* must be set to `CONFIGURED_USER`.

Either `jco.client.user` or `jco.client.alias_user` must be specified. The alias user may be up to 40 characters long and is case-sensitive.

> ### Caution:  
> When *Proxy Type* is set to `Internet` \(that is, a WebSocket RFC connection\), the checkbox *Use TLS client certificate login* must be unchecked to see the input field in the *Destinations* editor.



</td>
</tr>
<tr>
<td valign="top">

Password

</td>
<td valign="top">

`jco.client.passwd`

</td>
<td valign="top">

Represents the password of the user that is used.

> ### Note:  
> *Authentication Type* must be set to `CONFIGURED_USER`.

> ### Note:  
> Passwords in systems of SAP NetWeaver releases lower than 7.0 are case-insensitive and can be only eight characters long. For releases 7.0 and higher, passwords are case-sensitive with a maximum length of 40.
> 
> > ### Caution:  
> > When *Proxy Type* is set to `Internet` \(that is, using a WebSocket RFC connection\), the checkbox *Use TLS client certificate login* must be unchecked to see the input field in the *Destinations* editor.



</td>
</tr>
<tr>
<td valign="top">

Use TLS client certificate login

</td>
<td valign="top">

`jco.client.tls_client_certificate_logon`

</td>
<td valign="top">

> ### Note:  
> *Authentication Type* must be set to `CONFIGURED_USER`.

If the checkbox is checked or the value in a property file is set to `1`, the client certificate provided by the key store \(must be configured in addition\) is used for authentication, and the *User*, *Alias User* and *Password* input fields will be hidden. If the checkbox is unchecked or the value in a property file is set to `0`, the basic credentials must be provided.

</td>
</tr>
<tr>
<td valign="top">

Key Store Location

</td>
<td valign="top">

`KeyStoreLocation`

</td>
<td valign="top">

The name of the key store file that contains the client certificate for client certificate authentication against the remote WebSocket RFC server. Mandatory, if the checkbox *Use TLS client certificate login* is checked or `jco.client.tls_client_certificate_logon` is `1`.

</td>
</tr>
<tr>
<td valign="top">

Key Store Password

</td>
<td valign="top">

`KeyStorePassword`

</td>
<td valign="top">

The password for the key store file specified via `KeyStoreLocation`.

> ### Caution:  
> We strongly recommended that you use only key stores that are protected with a password.



</td>
</tr>
<tr>
<td valign="top">

Authentication Type

</td>
<td valign="top">

`jco.destination.auth_type`

</td>
<td valign="top">

> ### Note:  
> SAP BTP supports the propagation of business users \(principal propagation\) and technical users from the cloud application towards on-premise systems.
> 
> In both cases, a specific access token representing the business user or technical user is retrieved in the RFC runtime \(for example, in JCo or SAP BTP ABAP environment\), which can then be sent to the Connectivity service.
> 
> For more information, see [Authenticating Users against On-Premises Systems](authenticating-users-against-on-premises-systems-b643fbe.md).

-   If the property is not provided in a file, its default value `CONFIGURED_USER` is used. In this case, you must specify *user*, *password*, or other credentials directly.
-   To enable single sign-on via principal propagation \(an access token representing the business user logged on in the cloud application is forwarded to the on-premise system\), set the value to `PrincipalPropagation`. In this case, you do not need to provide `jco.client.user` and `jco.client.passwd` in the configuration.
-   To enable technical user propagation \(an access token representing the technical user is forwarded to the on-premise system\), set the value to `TechnicalUserPropagation`. In this case, you do not need to provide `jco.client.user` and `jco.client.passwd` in the configuration.

> ### Note:  
> For `PrincipalPropagation`, we recommend that you do not use the *RepositoryDefaultCredentials*, since there are special permissions needed \(for metadata lookup in the backend\) that not all business application users might have.



</td>
</tr>
<tr>
<td valign="top">

Client ID

</td>
<td valign="top">

`jco.client.tech_user_id`

</td>
<td valign="top">

Client ID of the application.

Mandatory when setting *Authentication Type*/`jco.destination.auth_type` to `TechnicalUserPropagation`. The *Client ID* is used to retrieve the access token from the OAuth Server.

</td>
</tr>
<tr>
<td valign="top">

Client Secret

</td>
<td valign="top">

`jco.client.tech_user_secret`

</td>
<td valign="top">

Client secret for the Client ID.

Mandatory when setting *Authentication Type*/`jco.destination.auth_type` to `TechnicalUserPropagation`.

</td>
</tr>
<tr>
<td valign="top">

Token Service URL

</td>
<td valign="top">

`jco.client.tech_user_service_url`

</td>
<td valign="top">

URL of the token service, against which the token exchange is performed.

Mandatory when setting *Authentication Type*/`jco.destination.auth_type` to `TechnicalUserPropagation`.

> ### Remember:  
> The token service is not accessed through the Cloud Connector, but directly over the Internet.

When using the Authorization and Trust Management service \(xsuaa\) as token service for *Technical User Propagation*, the URL should follow this example:

`https://{tenant}.authentication.us10.hana.ondemand.com/oauth/token → https://mytenant.authentication.us10.hana.ondemand.com/oauth/token`

</td>
</tr>
</table>

