<!-- loiob168417d33f4404eae3af052466f1315 -->

# High Availability Settings

Read and edit the high availability settings of a Cloud Connector instance via API.

When installing a Cloud Connector instance, you usually define its high availability role \(master or shadow instance\) during initial configuration, see [Change your Password and Choose Installation Type](initial-configuration-db9170a.md#loiodb9170a7d97610148537d5a84bf79ba2__change_password).

If the high availability role was not defined before, you can set the master or shadow role via this API.

If a shadow instance is connected to the master, this API also lets you switch the roles: the master instance requests the shadow instance to take over the master role, and then takes the shadow role itself.

> ### Note:  
> Editing the high availability settings is only allowed on the master instance, and supports only `shadow` as input.



<a name="loiob168417d33f4404eae3af052466f1315__section_rcp_l1b_vcb"/>

## Get High Availability Settings


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/haRole`

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

"<HA role\>"

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

Administrator, Associate Administrator, Subaccount Administrator, Display, Support, Monitoring

</td>
</tr>
</table>



## Example

```
curl -i -k -u Administrator:<password> https://localhost:8443/api/v1/configuration/connector/haRole

```





<a name="loiob168417d33f4404eae3af052466f1315__section_lys_l1b_vcb"/>

## Set High Availability Settings

Use this API if you want to set the role of a fresh installation \(no role assigned yet\).

As of version 2.12.0, this API also allows to switch the roles if a shadow instance is connected to the master. In this case, the API is only allowed on the master instance and supports only the value `shadow` as input. The master instance requests the shadow instance to take over the master role and then assumes the shadow role itself.


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/haRole`

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

"master" or "shadow"

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

ILLEGAL\_STATE, INVALID\_REQUEST

</td>
</tr>
<tr>
<td valign="top">

Roles

</td>
<td valign="top">

Administrator

</td>
</tr>
</table>

**Errors**:

-   `INVALID_REQUEST` \(400\): If a high-availability role other than "master" or "shadow" is supplied.
-   `ILLEGAL_STATE` \(409\): If changing the high-availability role is not possible; changing the role is only possible if no role has been assigned, or if the current role is master and a shadow system is connected.



## Example

```
curl -i -k -H 'Content-Type: application/json' -d '"shadow"'  -u Administrator:<password> -X POST https://localhost:8443/api/v1/configuration/connector/haRole

```

**Related Information**  


[Master Instance Configuration](master-instance-configuration-fc48825.md "Read and edit the high availability settings for a Cloud Connector master instance via API.")

[Shadow Instance Configuration](shadow-instance-configuration-2f6f677.md "Read and edit the configuration settings for a Cloud Connector shadow instance via API (available as of Cloud Connector version 2.12.0, or, where mentioned, as of version 2.13.0).")

