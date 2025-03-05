<!-- loio35f9d40075c349d48108835256cd44cb -->

# Audit Log Configuration

Read and edit the Cloud Connector's audit log settings via API.



<a name="loio35f9d40075c349d48108835256cd44cb__section_rcp_l1b_vcb"/>

## Get Cross-Subaccount Audit Log Configuration


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/auditLog` 

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
{level, cleanup, logPath} 
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

Administrator, Subaccount Administrator, Support, Display

</td>
</tr>
</table>

**Response:**

Current cross-subaccount audit log configuration.

-   `level`: OFF, SECURITY, ALL
-   `cleanup`: `0` \(logs will be retained indefinitely\), or number of days the audit logs will be retained.
-   `logPath`: path for audit logs



## Example

```
curl -i -k -u <user>:<password> https://localhost:8443/api/v1/configuration/connector/auditLog
```



<a name="loio35f9d40075c349d48108835256cd44cb__section_s2y_gdb_1dc"/>

## Change Cross-Subaccount Audit Log Configuration


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/auditLog` 

</td>
</tr>
<tr>
<td valign="top">

Method

</td>
<td valign="top">

*PATCH* 

</td>
</tr>
<tr>
<td valign="top">

Request

</td>
<td valign="top">

```
{level, cleanup}

```



</td>
</tr>
<tr>
<td valign="top">

Response

</td>
<td valign="top">



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

Administrator, Subaccount Administrator, Support

</td>
</tr>
</table>

**Request:**

Current subaccount independent audit log configuration.

-   `level`: OFF, SECURITY, ALL
-   `cleanup`: use `0` to never remove logs; otherwise 14, 30, 90,180, or 365 to retain logs for the respective number of days.

> ### Note:  
> `logPath` cannot be changed on a running Cloud Connector. To change the audit log path, use the script `changeAuditLogPath` located in your Cloud Connector installation directory.



## Example

```
curl -i -k -u <user>:<password> -X PATCH https://localhost:8443/api/v1/configuration/connector/auditLog --data '{"level"="SECURITY"}'
```



<a name="loio35f9d40075c349d48108835256cd44cb__section_dj2_hdb_1dc"/>

## Get Subaccount-Related Audit Log Configuration


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/auditLog/subaccounts/<regionHost>/<subaccount>` 

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
{level}      

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

Administrator, Subaccount Administrator, Support, Display

</td>
</tr>
</table>

**Response:**

-   `level`: OFF, SECURITY, ALL



## Example

```
curl -i -k -u <user>:<password> https://localhost:8443/api/v1/configuration/connector/auditLog/subaccounts/<regionHost>/<subaccount>
```



<a name="loio35f9d40075c349d48108835256cd44cb__section_e3h_hdb_1dc"/>

## Change Subaccount-Related Audit Log Configuration


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/auditLog/subaccounts/<regionHost>/<subaccount>` 

</td>
</tr>
<tr>
<td valign="top">

Method

</td>
<td valign="top">

*PATCH* 

</td>
</tr>
<tr>
<td valign="top">

Request

</td>
<td valign="top">

```
{level}
```



</td>
</tr>
<tr>
<td valign="top">

Response

</td>
<td valign="top">



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

Administrator, Subaccount Administrator, Support

</td>
</tr>
</table>

**Request:**

-   `level`: OFF, SECURITY, ALL



## Example

```
curl -i -k -u <user>:<password> https://localhost:8443/api/v1/configuration/connector/auditLog/subaccounts/<regionHost>/<subaccount> --data='{level="ALL"}'
```

