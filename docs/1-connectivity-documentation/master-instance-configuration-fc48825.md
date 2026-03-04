<!-- loiofc488257a630490390688714665fa08a -->

# Master Instance Configuration

Read and edit the high availability settings for a Cloud Connector master instance via API.

> ### Note:  
> The APIs below are available as of Cloud Connector version 2.13.0.

> ### Restriction:  
> These APIs are only permitted on a Cloud Connector master instance. The shadow instance rejects the requests with error code *400 – Invalid Request*.



<a name="loiofc488257a630490390688714665fa08a__section_ets_5rw_jlb"/>

## Get Configuration


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/ha/master/config`

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
{haEnabled, haPort, allowedShadowHost}

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

Administrator, Associate Administrator, Subaccount Administrator, Display, Support, Monitoring

</td>
</tr>
</table>

**Response Properties:**

-   `haEnabled`: Boolean value that indicates whether or not a shadow system is allowed to connect.
-   `haPort`: Port on which the shadow instance can connect \(restart required after change\).
-   `allowedShadowHost`: Name of the shadow host \(a string\) that is allowed to connect; an empty string signifies that any host is allowed to connect as shadow.

> ### Note:  
> `haPort` is an optional field in the HA shadow configuration, available as of version 2.17.0. Default value for the `haPort` parameter is the Cloud Connector's UI port.



## Example

```
curl -i -k -u <user>:<password> -X GET https://host>:<port>/api/v1/configuration/connector/ha/master/config

```



<a name="loiofc488257a630490390688714665fa08a__section_syv_5rw_jlb"/>

## Set Configuration


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/ha/master/config`

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
{haEnabled, haPort, allowedShadowHost}

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

INVALID\_REQUEST

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

**Response Properties:**

-   `haEnabled`: Boolean value that indicates whether or not a shadow system is allowed to connect.
-   `haPort`: Port on which the shadow instance can connect \(restart required after change\).
-   `allowedShadowHost`: Name of the shadow host \(a string\) that is allowed to connect. An empty string means that any host is allowed to connect as shadow.

**Errors:**

-   `INVALID_REQUEST` \(400\): if the name of the shadow host is not a valid host name

> ### Note:  
> `haPort` is an optional field in the HA shadow configuration, available as of version 2.17.0. Default value for the `haPort` parameter is the Cloud Connector's UI port.



## Example

```
curl -i -k -u <user>:<password> -X PUT -H 'Content-Type: application/json' -d '{"haEnabled":true}' https://<host>:<port>/api/v1/configuration/connector/ha/master/config

```



<a name="loiofc488257a630490390688714665fa08a__section_urx_5rw_jlb"/>

## Get State


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/ha/master/state`

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
{state, shadowHost}

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

Administrator, Associate Administrator, Subaccount Administrator, Display, Support, Monitoring

</td>
</tr>
</table>

**Response Properties:**

-   `state`: One of the following strings: ALONE, BINDING, CONNECTED or BROKEN.
-   `shadowHost`: Connected shadow host \(a string\)



## Example

```
curl -i -k -u <user>:<password> -X GET https://<host>:<port>/api/v1/configuration/connector/ha/master/state

```



<a name="loiofc488257a630490390688714665fa08a__section_w2z_5rw_jlb"/>

## Set State


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/ha/master/state`

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



</td>
</tr>
<tr>
<td valign="top">

Response

</td>
<td valign="top">

```
{op}

```



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

**Request Properties:**

The value of property `op` is one of the following strings:

-   `SWITCH`: Switch roles with shadow
-   `FORCE_SWITCH`: Take over the shadow role, even if shadow instance does not respond.

**Errors:**

-   `INVALID_REQUEST` \(400\): Value of property `op` is neither SWITCH nor FORCE\_SWITCH.
-   `ILLEGAL_STATE` \(409\): Master system is in a state that does not permit the requested operation.



## Example

```
curl -i -k -u <user>:<password> -X POST -H 'Content-Type: application/json' -d '{"op":"SWITCH"}' https://<host>:<port>/api/v1/configuration/connector/ha/master/state

```



<a name="loiofc488257a630490390688714665fa08a__section_gqd_vrw_jlb"/>

## Reset

A successful call to this API restores default values for all settings related to high availability on the master side.

> ### Caution:  
> Do not perform this call if the shadow is connected to a master.


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/ha/master/state`

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

ILLEGAL\_STATE

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

**Errors:**

-   `ILLEGAL_STATE` \(409\): A shadow instance is connected to the master.



## Example

```
curl -i -k -u <user>:<password> -X DELETE https://<host>:<port>/api/v1/configuration/connector/ha/master/state
```

