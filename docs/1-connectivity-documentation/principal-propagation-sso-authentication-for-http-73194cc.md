<!-- loio73194cc419894433994c5f0444b4c6a1 -->

# Principal Propagation SSO Authentication for HTTP

Forward the identity of a cloud user from a Cloud Foundry application to a backend system via HTTP to enable single sign-on \(SSO\).



## Context

A *PrincipalPropagation* destination enables single sign-on \(SSO\) by forwarding the identity of a cloud user to the Cloud Connector, and from there to the target on-premise system. In this way, the cloud user's identity can be provided without manual logon.

> ### Note:  
> This authentication type applies only for on-premise connectivity.



## Configuration Steps

You can create and configure a *PrincipalPropagation* destination by using the properties listed below, and deploy it on SAP BTP. For more information, see [Managing Destinations](managing-destinations-84e45e0.md).



## Properties

The table below lists the destination properties for *PrincipalPropagation* authentication type.


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
<td valign="top" colspan="2">

**Required**

</td>
</tr>
<tr>
<td valign="top">

`Name`

</td>
<td valign="top">

Destination name. Must be unique for the destination level.

</td>
</tr>
<tr>
<td valign="top">

`Type`

</td>
<td valign="top">

Destination type. Use `HTTP` for all HTTP\(S\) destinations.

</td>
</tr>
<tr>
<td valign="top">

`URL`

</td>
<td valign="top">

Virtual URL of the protected on-premise application.

</td>
</tr>
<tr>
<td valign="top">

`Authentication`

</td>
<td valign="top">

Authentication type. Use `PrincipalPropagation` as value.

</td>
</tr>
<tr>
<td valign="top">

`ProxyType`

</td>
<td valign="top">

You can only use proxy type `OnPremise`.

</td>
</tr>
<tr>
<td valign="top">

**Optional**

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

`CloudConnectorLocationId`

</td>
<td valign="top">

> ### Note:  
> Required only if multiple Cloud Connectors are connected to a subaccount.

You can connect multiple Cloud Connectors to a subaccount as long as their location ID is different. The location ID specifies the Cloud Connector over which the connection is opened. The default value is an empty string identifying the Cloud Connector that is connected without any location ID.

For more information, see [Adding a Subaccount](adding-and-managing-subaccounts-f16df12.md#loiof16df12fab9f4fe1b8a4122f0fd54b6e__add) \(step 3e\).

</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Additional**

</td>
</tr>
<tr>
<td valign="top">

`URL.headers.<header-key>`

</td>
<td valign="top">

A static key prefix used as a namespace grouping of the URL's HTTP headers whose values will be sent to the target endpoint. For each HTTP header's key, you must add a `URL.headers` prefix separated by dot-delimiter. For example:

> ### Sample Code:  
> ```
> {
>     ...
>     "URL.headers.<header-key-1>" : "<header-value-1>",
>     ...
>     "URL.headers.<header-key-N>": "<header-value-N>",
> }
> ```

> ### Note:  
> This is a naming convention. As the call to the target endpoint is performed on the client side, the service only provides the configured properties. The expectation for the client-side processing logic is to parse and use them. If you are using higher-level libraries and tools, please check if they support this convention.



</td>
</tr>
<tr>
<td valign="top">

`URL.queries.<query-key>`

</td>
<td valign="top">

A static key prefix used as a namespace grouping of URL's query parameters whose values will be sent to the target endpoint. For each query parameter's key, you must add a `URL.queries` prefix separated by dot-delimiter. For example:

> ### Sample Code:  
> ```
> {
>     ...
>     "URL.queries.<query-key-1>" : "<query-value-1>",
>     ...
>     "URL.queries.<query-key-N>": "<query-value-N>",
> }
> ```

> ### Note:  
> This is a naming convention. As the call to the target endpoint is performed on the client side, the service only provides the configured properties. The expectation for the client-side processing logic is to parse and use them. If you are using higher-level libraries and tools, please check if they support this convention.



</td>
</tr>
</table>



## Example

```ini

Name=OnPremiseDestination
Type=HTTP 
URL= http://virtualhost:80
Authentication=PrincipalPropagation
ProxyType=OnPremise

```



**Related Information**  


[Principal Propagation](principal-propagation-e2cbb48.md "Enable single sign-on (SSO) by forwarding the identity of cloud users to a remote system or service.")

