<!-- loio2f6f67716d6944919fcdc43c92ceefb8 -->

# Shadow Instance Configuration

Read and edit the configuration settings for a Cloud Connector shadow instance via API \(available as of Cloud Connector version 2.12.0, or, where mentioned, as of version 2.13.0\).

> ### Note:  
> The APIs below are only permitted on a Cloud Connector shadow instance. The master instance will reject the requests with error code ***403 – FORBIDDEN\_REQUEST***.



<a name="loio2f6f67716d6944919fcdc43c92ceefb8__section_ets_5rw_jlb"/>

## Get Configuration


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/ha/shadow/config`

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
{masterHost, masterPort, ownHost, haPort, checkIntervalInSeconds, takeoverDelayInSeconds, connectTimeoutInMillis, requestTimeoutInMillis}

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

-   `masterHost`: Host name of the master instance \(string\)
-   `masterPort`: Port of the master instance \(string or number\)
-   `ownHost`: Host name of the shadow instance \(string\)
-   `haPort`: Own port for HA communication \(restart required after change\).
-   `checkIntervalInSeconds`: Time between two health checks against the master instance \(number\)
-   `takeoverDelayInSeconds`: The time a master instance may stay unreachable before the shadow instance takes over \(number\)
-   `connectTimeoutInMillis`: Timeout for connection attempts between shadow and master instance \(number\)
-   `requestTimeoutInMillis`: Timeout for requests between shadow and master instance \(number\)

> ### Note:  
> This API may take some time to fetch the own hosts from the environment.

> ### Note:  
> `haPort` is a new field in the HA shadow configuration, available as of version 2.17.0. Default value for the `haPort` parameter is the Cloud Connector's UI port.



## Example

```
curl -i -k -u <user>:<password> -X GET https://<host>:<port>/api/v1/configuration/connector/ha/shadow/config

```



<a name="loio2f6f67716d6944919fcdc43c92ceefb8__section_syv_5rw_jlb"/>

## Set Configuration


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/ha/shadow/config`

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
{masterPort, masterHost, ownHost, haPort, checkIntervalInSeconds, takeoverDelayInSeconds, connectTimeoutInMillis, requestTimeoutInMillis}

```



</td>
</tr>
<tr>
<td valign="top">

Response

</td>
<td valign="top">

```
{masterPort, masterHost, ownHost, haPort, checkIntervalInSeconds, takeoverDelayInSeconds, connectTimeoutInMillis, requestTimeoutInMillis}

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

Administrator

</td>
</tr>
</table>

**Request Properties:**

-   `masterHost`: Host name of the master instance \(string\)
-   `masterPort`: Port of the master instance \(string or number\)
-   `ownHost`: Host name of the shadow instance \(string\)
-   `haPort`: Own port for HA communication \(restart required after change\).
-   `checkIntervalInSeconds`: Time between two health checks against the master instance \(number\)
-   `takeoverDelayInSeconds`: The time a master instance may stay unreachable before the shadow instance takes over \(number\)
-   `connectTimeoutInMillis`: Timeout for connection attempts between shadow and master instance \(number\)
-   `requestTimeoutInMillis`: Timeout for requests between shadow and master instance \(number\)

**Response Properties:**

See *Request Properties*.

> ### Note:  
> `haPort` is an optional field in the HA shadow configuration, available as of version 2.17.0. Default value for the `haPort` parameter is the Cloud Connector's UI port.



## Example

```
curl -i -k -u <user>:<password> -X PUT https://<host>:<port>/api/v1/configuration/connector/ha/shadow/config
  -H 'Content-Type: application/json' -d '{"masterHost":"localhost", "masterPort":"8443", "ownHost":"localhost",
      "checkIntervalInSeconds":30, "takeoverDelayInSeconds":10, "connectTimeoutInMillis":1000,
      "requestTimeoutInMillis":12000}'
```



<a name="loio2f6f67716d6944919fcdc43c92ceefb8__section_urx_5rw_jlb"/>

## Get State

> ### Note:  
> Available as of version 2.13.0.


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/ha/shadow/state`

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
{state, ownHosts, stateMessage, masterVersions} 

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

-   `state`: Possible string values are: INITIAL, DISCONNECTED, DISCONNECTING, HANDSHAKE, INITSYNC, READY, or LOST.
-   `ownHosts`: List of alternative host names for the shadow instance.
-   `stateMessage`: Message providing details on the current state. This property may not always be present. Typically, this property is available if an error occurred \(for example, a failed attempt to connect to the master instance\).
-   `masterVersions`: Overview of relevant component versions of the master system, including a flag \(*property ok*\) that indicates whether or not there are incompatibility issues because of differing master and shadow versions.

    > ### Note:  
    > This property is only available if the shadow instance is connected to the master instance, or if there has been a successful connection to the master system at some point in the past.




## Example

```
curl -i -k -u <user>:<password> -X GET https://<host>:<port>/api/v1/configuration/connector/ha/shadow/state

```



<a name="loio2f6f67716d6944919fcdc43c92ceefb8__section_w2z_5rw_jlb"/>

## Change State


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/ha/shadow/state`

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
{op, user, password}

```



</td>
</tr>
<tr>
<td valign="top">

Errors

</td>
<td valign="top">

INVALID\_REQUEST, ILLEGAL\_STATE, RUNTIME\_FAILURE

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

-   `op`: String value representing the state change operation. Possible values are CONNECT or DISCONNECT.
-   `user`: User for logon to the master instance
-   `password`: Password for logon to the master instance

**Errors:**

-   `INVALID_REQUEST` \(400\): Invalid or missing property values were supplied; this includes wrong user or password
-   `ILLEGAL_STATE` \(409\): The requested operation cannot be executed given the current state of master and shadow instance. This typically means the master instance does not allow high availability.
-   `RUNTIME_FAILURE` \(500\): communication error between shadow and master, e.g. handshake failure or master does not respond.

> ### Note:  
> The logon credentials are used for initial logon to master instance only. If a shadow instance is disconnected from its master instance, it will reconnect to the \(same\) master instance using a certificate. Hence, user and password can be omitted when reconnecting.



## Example

```
curl -i -k -u <user>:<password> -X POST https://<host>:<port>/api/v1/configuration/connector/ha/shadow/state
           -H 'Content-Type: application/json' -d '{"op":"CONNECT", "user":"<user on master>", "password":"<password>"}'
curl -i -k -u <user>:<password> -X POST https://<host>:<port>/api/v1/configuration/connector/ha/shadow/state
          -H 'Content-Type: application/json' -d '{"op":"DISCONNECT"}'
```



<a name="loio2f6f67716d6944919fcdc43c92ceefb8__section_gqd_vrw_jlb"/>

## Reset

> ### Note:  
> Available as of version 2.13.0.

A successful call to this API deletes master host and port, and restores default values for all other settings related to a connection to the master.

> ### Caution:  
> Do not perform this call if the shadow is connected to a master.


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/ha/shadow/state`

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

-   `ILLEGAL_STATE` \(409\): the shadow is currently connected to a master.



## Example

```
curl -i -k -u <user>:<password> -X DELETE https://<host>:<port>/api/v1/configuration/connector/ha/shadow/state

```

