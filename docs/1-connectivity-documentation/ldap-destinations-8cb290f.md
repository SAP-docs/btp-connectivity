<!-- loio8cb290f7fb4a4d92994487299e1ccd8b -->

# LDAP Destinations

Find information about LDAP destinations for on-premise connections from an SAP BTP subaccount.

> ### Note:  
> The on-premise use cases described in this guide are also applicable to virtual private cloud \(VPC\) environments.


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
<td valign="top" colspan="3">

**Required**

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

Name of the target LDAP server.

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

Choose `LDAP`.

</td>
</tr>
<tr>
<td valign="top">

URL

</td>
<td valign="top">

`ldap.url`

</td>
<td valign="top">

Address of the target LDAP server.

</td>
</tr>
<tr>
<td valign="top">

Proxy Type

</td>
<td valign="top">

`ldap.proxyType` 

</td>
<td valign="top">

`OnPremise` 

</td>
</tr>
<tr>
<td valign="top">

Authentication

</td>
<td valign="top">

`ldap.authentication`

</td>
<td valign="top">

`NoAuthentication` or `BasicAuthentication` 

</td>
</tr>
<tr>
<td valign="top" colspan="3">

**Optional**

</td>
</tr>
<tr>
<td valign="top">

Description

</td>
<td valign="top">

`Description`

</td>
<td valign="top">

Free text describing the LDAP destination.

</td>
</tr>
<tr>
<td valign="top">

Location ID

</td>
<td valign="top">

`CloudConnectorLocationId` 

</td>
<td valign="top">

If more than one Cloud Connector is connected to your subaccount, enter the location ID of the Cloud Connector that is used to connect to the target LDAP server.

</td>
</tr>
</table>

**Related Information**  


[Create LDAP Destinations](create-ldap-destinations-2d11ff6.md "Create LDAP destinations in the Destinations editor (SAP BTP cockpit).")

