<!-- loioe933fd930039402c907d5afaa75eb0e1 -->

# System Mappings

Manage the Cloud Connector's system mappings via API.



<a name="loioe933fd930039402c907d5afaa75eb0e1__section_rcp_l1b_vcb"/>

## Get All System Mappings


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/systemMappings` 

</td>
</tr>
<tr>
<td valign="top">

Method

</td>
<td valign="top">

*GET* 

</td>
</tr>
<tr>
<td valign="top">

Request

</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

Response

</td>
<td valign="top">

```
[{virtualHost, virtualPort, localHost, localPort, protocol, backendType, authenticationMode, hostInHeader, description, ...}]

```



</td>
</tr>
<tr>
<td valign="top">

Errors

</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

Roles

</td>
<td valign="top">

Administrator, Subaccount Administrator, Display, Support

</td>
</tr>
</table>

**Response**:

An array of objects with the following properties:

-   `virtualHost`: Virtual host used on the cloud side \(a string\)
-   `virtualPort`: Virtual port used on the cloud side \(a string\)
-   `localHost`: Host on the on-premises side \(a string\)
-   `localPort`: Port on the on-premises side \(a string\)
-   `protocol`: Protocol used when sending requests and receiving responses \(a string\)
-   `backendType`: Type of the backend \(a string\)
-   `authenticationMode`: Authentication mode used on the backend side \(a string\).
-   `hostInHeader`: Policy for setting the host in the response header. Available for HTTP\(S\) protocols only.
-   `totalResourcesCount`: the total number of resources
-   `enabledResourcesCount`: the number of enabled resources
-   `description`: Description for the system mapping \(a string\).
-   `sncPartnerName`: SNC name of an ABAP Server, required for RFCS communication only.
-   `sapRouter`: SAP router route, required only if an SAP router is used.
-   `allowedClients`: Array of strings, describing the SAP clients allowing to execute the calls in this system. Valid clients are 3 letters long. If no clients are defined here, there is no restriction – every client is allowed. Only applicable for RFC-based communication.
-   `blacklistedUsers`: Array of `{client, user}`, describing users that are not allowed to execute the call, even if the client is listed under allowed clients. Only applicable for RFC-based communication.



## Get System Mapping


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/systemMappings/<virtualHost>:<virtualPort>` 

</td>
</tr>
<tr>
<td valign="top">

Method

</td>
<td valign="top">

*GET* 

</td>
</tr>
<tr>
<td valign="top">

Request

</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

Response

</td>
<td valign="top">

```
{virtualHost, virtualPort, localHost, localPort, protocol, backendType, authenticationMode, hostInHeader, description, ...}


```



</td>
</tr>
<tr>
<td valign="top">

Errors

</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

Roles

</td>
<td valign="top">

Administrator, Subaccount Administrator, Display, Support

</td>
</tr>
</table>

**Response**:

An array of objects with the following properties:

-   `virtualHost`: Virtual host used on the cloud side \(a string\)
-   `virtualPort`: Virtual port used on the cloud side \(a string\)
-   `localHost`: Host on the on-premises side \(a string\)
-   `localPort`: Port on the on-premises side \(a string\)
-   `protocol`: Protocol used when sending requests and receiving responses \(a string\)
-   `backendType`: Type of the backend \(a string\)
-   `authenticationMode`: Authentication mode used on the backend side \(a string\).
-   `hostInHeader`: Policy for setting the host in the response header \(a string\). Available for HTTP\(S\) protocols only.
-   `totalResourcesCount`: the total number of resources
-   `enabledResourcesCount`: the number of enabled resources
-   `description`: Description for the system mapping \(a string\).
-   `sncPartnerName`: SNC name of an ABAP Server, required for RFCS communication only.
-   `sapRouter`: SAP router route, required only if an SAP router is used.
-   `allowedClients`: Array of strings, describing the SAP clients allowing to execute the calls in this system. Valid clients are 3 letters long. If no clients are defined here, there is no restriction – every client is allowed. Only applicable for RFC-based communication.
-   `blacklistedUsers`: Array of `{client, user}`, describing users that are not allowed to execute the call, even if the client is listed under allowed clients. Only applicable for RFC-based communication.



<a name="loioe933fd930039402c907d5afaa75eb0e1__section_lys_l1b_vcb"/>

## Create System Mapping \(Master Only\)


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/systemMappings` 

</td>
</tr>
<tr>
<td valign="top">

Method

</td>
<td valign="top">

*POST* 

</td>
</tr>
<tr>
<td valign="top">

Request

</td>
<td valign="top">

```
{virtualHost, virtualPort, localHost, localPort, protocol, backendType, authenticationMode, hostInHeader, description, ...}

```



</td>
</tr>
<tr>
<td valign="top">

Response

</td>
<td valign="top">

201 on success

</td>
</tr>
<tr>
<td valign="top">

Errors

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Roles

</td>
<td valign="top">

Administrator, Subaccount Administrator

</td>
</tr>
</table>

**Request Properties**:

-   `virtualHost`: Virtual host used on the cloud side \(a string\)
-   `virtualPort`: Virtual port used on the cloud side \(a string\)
-   `localHost`: Host on the on-premises side \(a string\)
-   `localPort`: Port on the on-premises side \(a string\)
-   `protocol`: Protocol used when sending requests and receiving responses, which must be one of the following strings: `HTTP, HTTPS, RFC, RFCS, LDAP, LDAPS, TCP, TCPS`.
-   `backendType`: Type of the backend system. Valid values are`abapSys, netweaverCE, netweaverGW, applServerJava, BC, PI, hana, otherSAPsys, nonSAPsys`.
-   `authenticationMode`: Authentication mode to be used on the backend side, which must be one of the following strings: `NONE,` `NONE_RESTRICTED`, `X509_GENERAL, X509_RESTRICTED, KERBEROS`.
-   `hostInHeader`: Policy for setting the host in the response header. This property is applicable to HTTP\(S\) protocols only, and it is **optional**. If set, it must be one of the following strings: `internal, virtual`. The default is `virtual`. You may also use all capital letters, i.e. `INTERNAL` and `VIRTUAL`.
-   `description`: Description for the system mapping \(string, optional\). The default is no description, i.e. the empty string.
-   `sncPartnerName`: SNC name of an ABAP Server, required for RFCS communication only.
-   `sapRouter`: SAP router route, required only if an SAP router is used.
-   `allowedClients`: Array of strings, describing the SAP clients allowing to execute the calls in this system. Valid clients are 3 letters long. If no clients are defined here, there is no restriction – every client is allowed. Only applicable for RFC-based communication.
-   `blacklistedUsers`: Array of `{client, user}`, describing users that are not allowed to execute the call, even if the client is listed under allowed clients. Only applicable for RFC-based communication.

> ### Note:  
> The authentication modes `NONE_RESTRICTED` and `X509_RESTRICTED` prevent the Cloud Connector from sending the system certificate in any case, whereas `NONE` and `X509_GENERAL` will send the system certificate if the circumstances allow it.



<a name="loioe933fd930039402c907d5afaa75eb0e1__section_bcf_42b_vcb"/>

## Delete System Mapping \(Master Only\)


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/systemMappings`/<virtualHost\>:<virtualPort\>

</td>
</tr>
<tr>
<td valign="top">

Method

</td>
<td valign="top">

*DELETE* 

</td>
</tr>
<tr>
<td valign="top">

Request

</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

Response

</td>
<td valign="top">

204 on success

</td>
</tr>
<tr>
<td valign="top">

Errors

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Roles

</td>
<td valign="top">

Administrator, Subaccount Administrator

</td>
</tr>
</table>



<a name="loioe933fd930039402c907d5afaa75eb0e1__section_xkk_42b_vcb"/>

## Delete All System Mappings \(Master Only\)


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/systemMappings` 

</td>
</tr>
<tr>
<td valign="top">

Method

</td>
<td valign="top">

*DELETE* 

</td>
</tr>
<tr>
<td valign="top">

Request

</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

Response

</td>
<td valign="top">

204 on success

</td>
</tr>
<tr>
<td valign="top">

Errors

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Roles

</td>
<td valign="top">

Administrator, Subaccount Administrator

</td>
</tr>
</table>



<a name="loioe933fd930039402c907d5afaa75eb0e1__section_jrl_42b_vcb"/>

## Replace System Mapping \(Master Only\)


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/systemMappings/virtualHost:virtualPort` 

</td>
</tr>
<tr>
<td valign="top">

Method

</td>
<td valign="top">

*PUT* 

</td>
</tr>
<tr>
<td valign="top">

Request

</td>
<td valign="top">

```
{virtualHost, virtualPort, localHost, localPort, protocol, backendType, authenticationMode, hostInHeader, description, ...}

```



</td>
</tr>
<tr>
<td valign="top">

Response

</td>
<td valign="top">

204 on success

</td>
</tr>
<tr>
<td valign="top">

Errors

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Roles

</td>
<td valign="top">

Administrator, Subaccount Administrator

</td>
</tr>
</table>

**Request Properties**:

-   `virtualHost`: Virtual host used on the cloud side \(a string\)
-   `virtualPort`: Virtual port used on the cloud side \(a string\)

-   `localHost`: Host on the on-premises side \(a string\)
-   `localPort`: Port on the on-premises side \(a string\)
-   `protocol`: Protocol used when sending requests and receiving responses, which must be one of the following strings: `HTTP, HTTPS, RFC, RFCS, LDAP, LDAPS, TCP, TCPS`.
-   `backendType`: Type of the backend system. Valid values are`abapSys, netweaverCE, netweaverGW, applServerJava, BC, PI, hana, otherSAPsys, nonSAPsys`.
-   `authenticationMode`: Authentication mode to be used on the backend side, which must be one of the following strings: `NONE,` `NONE_RESTRICTED`, `X509_GENERAL, X509_RESTRICTED, KERBEROS`.
-   `hostInHeader`: Policy for setting the host in the response header; this property is **optional**. If set, it must be one of the following strings: `internal, virtual`. The default is `virtual`. You may also use all capital letters, i.e. `INTERNAL` and `VIRTUAL`.
-   `description`: Description for the system mapping \(string, optional\). The default is no description, i.e. the empty string.
-   `sncPartnerName`: SNC name of an ABAP Server, only set for RFCS communication.
-   `sapRouter`: SAP router route, only set if an SAP router is used.
-   `allowedClients`: Array of strings, describing the SAP clients allowing to execute the calls in this system. Valid clients are 3 letters long. If no clients are defined here, there is no restriction – every client is allowed. Only applicable for RFC-based communication.
-   `blacklistedUsers`: Array of `{client, user}`, describing users, that are not allowed to execute the call, even if the client is listed under allowed clients. Only applicable for RFC-based communication.

> ### Note:  
> The authentication modes `NONE_RESTRICTED` and `X509_RESTRICTED` prevent the Cloud Connector from sending the system certificate in any case, whereas `NONE` and `X509_GENERAL` will send the system certificate if the circumstances allow it.

