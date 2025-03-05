<!-- loio72885a1eee784790a8c8d07538051134 -->

# Subaccount

Manage the Cloud Connector's subaccount settings via API.



<a name="loio72885a1eee784790a8c8d07538051134__operations"/>

## Operations


<table>
<tr>
<td valign="top">

**Subaccount**

</td>
<td valign="top">

[Get Subaccounts](subaccount-72885a1.md#loio72885a1eee784790a8c8d07538051134__getSubs) 

[Create Subaccount \(Master Only\)](subaccount-72885a1.md#loio72885a1eee784790a8c8d07538051134__createSub) 

[Delete Subaccount \(Master Only\)](subaccount-72885a1.md#loio72885a1eee784790a8c8d07538051134__deleteSub) 

[Edit Subaccount \(Master Only\)](subaccount-72885a1.md#loio72885a1eee784790a8c8d07538051134__editSub) 

[Connect/Disconnect Subaccount \(Master Only\)](subaccount-72885a1.md#loio72885a1eee784790a8c8d07538051134__connectSub) 

[Renew Subaccount Certificate \(Master Only\)](subaccount-72885a1.md#loio72885a1eee784790a8c8d07538051134__refreshSubCert) 

[Get Subaccount Configuration](subaccount-72885a1.md#loio72885a1eee784790a8c8d07538051134__getSubConfig) 

</td>
</tr>
<tr>
<td valign="top">

**Recovery Subaccount**

> ### Caution:  
> This feature is deprecated.
> 
> Due to the discontinuation of the *Enhanced Disaster Recovery Service*, the related functionality in the Cloud Connector has been dropped as of version 2.16.
> 
> For more information, see [What's New for SAP Business Technology Platform](https://help.sap.com/whats-new/cf0cb2cb149647329b5d02aa96303f56?Component=Enhanced%2520Disaster%2520Recovery%2520Service&locale=en-US&version=Cloud).



</td>
<td valign="top">

[Create Recovery Subaccount \(Master Only\)](subaccount-72885a1.md#loio72885a1eee784790a8c8d07538051134__createRecovSub) 

[Delete Recovery Subaccount \(Master Only\)](subaccount-72885a1.md#loio72885a1eee784790a8c8d07538051134__deleteRecovSub) 

[Refresh Certificate of Recovery Subaccount \(Master Only\)](subaccount-72885a1.md#loio72885a1eee784790a8c8d07538051134__refreshRecovSubCert) 

[Activate/Deactivate Recovery Subaccount \(Master Only\)](subaccount-72885a1.md#loio72885a1eee784790a8c8d07538051134__activateRecovSub) 

[Takeover \(Master Only\)](subaccount-72885a1.md#loio72885a1eee784790a8c8d07538051134__takeover) 

</td>
</tr>
<tr>
<td valign="top">

**Trust**

</td>
<td valign="top">

[Synchronize Trust List \(Master Only\)](subaccount-72885a1.md#loio72885a1eee784790a8c8d07538051134__syncTrustList)

[Get IDP Trust List](subaccount-72885a1.md#loio72885a1eee784790a8c8d07538051134__getIDPTrustList) 

[Get Application Trust List](subaccount-72885a1.md#loio72885a1eee784790a8c8d07538051134__gestAppTrustList) 

[Enable Or Disable Trust \(Master Only\)](subaccount-72885a1.md#loio72885a1eee784790a8c8d07538051134__enableTrust) 

[Get IDP Trust Properties](subaccount-72885a1.md#loio72885a1eee784790a8c8d07538051134__getIDPTrustProperties) 

[Get Application Trust Properties](subaccount-72885a1.md#loio72885a1eee784790a8c8d07538051134__getAppTrustProperties) 

</td>
</tr>
</table>



<a name="loio72885a1eee784790a8c8d07538051134__getSubs"/>

## Get Subaccounts


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts` 

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
[{regionHost, subaccount, locationID}] 
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

-   `regionHost`: region hosts \(a string\).
-   `subaccount`: subaccount name \(a string\).
-   `locationID`: location identifier for the Cloud Connector instance \(a string\); this property is not available if the default location ID is in use.

Back to [Operations](subaccount-72885a1.md#loio72885a1eee784790a8c8d07538051134__operations)



<a name="loio72885a1eee784790a8c8d07538051134__createSub"/>

## Create Subaccount \(Master Only\)

Creates and connects a subaccount.


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts` 

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
{regionHost, subaccount, cloudUser, cloudPassword, locationID, displayName, description}

```



</td>
</tr>
<tr>
<td valign="top">

Request

\(as of version 2.17.0\)

</td>
<td valign="top">

```
{authenticationData, locationID, displayName, description}
```



</td>
</tr>
<tr>
<td valign="top">

Response

</td>
<td valign="top">

201, created subaccount entity:

```
{regionHost, subaccount, locationID, displayName, description, tunnel}

```



</td>
</tr>
<tr>
<td valign="top">

Errors

</td>
<td valign="top">

INVALID\_REQUEST, INVALID\_CONFIGURATION

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

-   `regionHost`: region host name \(a string\).
-   `subaccount`: subaccount technical name \(a string\).
-   `cloudUser`: user for the specified subaccount and region host.

-   `cloudPassword`: password for the cloud user.

-   `authenticationData`: subaccount authentication data, used instead of `cloudUser`, `cloudPassword` and `regionHost` \(as of version 2.17.0\).
-   `locationID`: location identifier for the Cloud Connector instance \(a string; optional\).
-   `displayName`: display name of the subaccount \(a string; optional\).
-   `description`: subaccount description \(a string; optional\).

**Response Properties**:

-   `regionHost`: region host name \(a string\).
-   `subaccount`: subaccount technical name \(a string\).
-   `locationID`: location ID \(a string\); this property is not available if the default location ID is in use.
-   `displayName`: display name of the subaccount \(a string\); this property is not available if there is no specified display name.
-   `description`: subaccount description \(a string\); this property is not available if there is no description.
-   `tunnel`: object outlining the current state of the tunnel.

**Errors**:

-   INVALID\_REQUEST \(400\): one or more mandatory parameters are missing or invalid.
-   INVALID\_CONFIGURATION \(409\): the subaccount already exists.

Back to [Operations](subaccount-72885a1.md#loio72885a1eee784790a8c8d07538051134__operations)



<a name="loio72885a1eee784790a8c8d07538051134__deleteSub"/>

## Delete Subaccount \(Master Only\)


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>` 

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

NOT\_FOUND, ILLEGAL\_STATE

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

**Errors**:

-   `NOT_FOUND` \(404\): subaccount does not exist \(in the specified region\).
-   `ILLEGAL_STATE` \(409\): there is at least one session that has access to the subaccount.

Back to [Operations](subaccount-72885a1.md#loio72885a1eee784790a8c8d07538051134__operations)



<a name="loio72885a1eee784790a8c8d07538051134__editSub"/>

## Edit Subaccount \(Master Only\)


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>` 

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
{locationID, displayName, description}
```



</td>
</tr>
<tr>
<td valign="top">

Response

</td>
<td valign="top">

```
{regionHost, subaccount, locationID, displayName, description, tunnel}

```



</td>
</tr>
<tr>
<td valign="top">

Errors

</td>
<td valign="top">

NOT\_FOUND

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

-   `locationID`: location identifier for the Cloud Connector instance \(a string; optional\); if this parameter is not supplied the location ID will not change. Revert to the default location ID by supplying the empty string.
-   `displayName`: subaccount display name \(a string; optional\); if this parameter is not supplied the display name will not change. Clear the display name by using an empty string.
-   `description`: subaccount description \(a string; optional\); if this parameter is not supplied the description will not change. Clear the description by using an empty string.

**Response Properties**:

-   `regionHost`: region host name \(a string\).
-   `subaccount`: subaccount technical name \(a string\).
-   `locationID`: location identifier for the Cloud Connector instance \(a string\); this property is not available if the default location ID is in use.
-   `displayName`: display name of the subaccount \(a string\); this property is not available if there is no specified display name.
-   `description`: subaccount description \(a string\); this property is not available if there is no description.
-   `tunnel`: object outlining the current state of the tunnel.

**Errors**:

-   `NOT_FOUND` \(404\): subaccount does not exist \(in the specified region\).

Back to [Operations](subaccount-72885a1.md#loio72885a1eee784790a8c8d07538051134__operations)



<a name="loio72885a1eee784790a8c8d07538051134__connectSub"/>

## Connect/Disconnect Subaccount \(Master Only\)


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/state` 

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
{connected}
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

Request Properties:

-   `connected`: a Boolean value indicating whether the subaccount should be connected \(true\) or disconnected \(false\).

Back to [Operations](subaccount-72885a1.md#loio72885a1eee784790a8c8d07538051134__operations)



<a name="loio72885a1eee784790a8c8d07538051134__refreshSubCert"/>

## Renew Subaccount Certificate \(Master Only\)


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/validity` 

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
{user, password}
```



</td>
</tr>
<tr>
<td valign="top">

Request

\(as of version 2.17.0\)

</td>
<td valign="top">

```
{authenticationData}
```



</td>
</tr>
<tr>
<td valign="top">

Response

</td>
<td valign="top">

```
{regionHost, subaccount, locationID, displayName, description, tunnel}

```



</td>
</tr>
<tr>
<td valign="top">

Errors \(as of version 2.17.0\) 

</td>
<td valign="top">

BAD\_REQUEST

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

-   `user`: \(cloud\) user for the specified region host and subaccount.

-   `password`: password for the \(cloud\) user.

-   `authenticationData`: subaccount authentication data, used instead of `user` and `password` \(as of version 2.17.0\).

**Response Properties**:

-   `regionHost`: region host name \(a string\).
-   `subaccount`: subaccount technical name \(a string\).
-   `locationID`: location identifier for the Cloud Connector instance \(a string\); this property is not available if the default location ID is in use.
-   `displayName`: display name of the subaccount \(a string\); this property is not available if there is no specified display name.
-   `description`: subaccount description \(a string\); this property is not available if there is no description.
-   `tunnel`: object outlining the current state of the tunnel.

**Errors** \(as of version 2.17.0\):

-   `BAD_REQUEST` \(400\): the region in authentication data does not match the region of the subaccount.

Back to [Operations](subaccount-72885a1.md#loio72885a1eee784790a8c8d07538051134__operations)



<a name="loio72885a1eee784790a8c8d07538051134__getSubConfig"/>

## Get Subaccount Configuration


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>` 

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
{regionHost, subaccount, locationID, displayName, description, tunnel:{state, connections, applicationConnections:[], serviceChannels:[]}}

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

**Response Properties**:

-   `regionHost`: region host name \(a string\).
-   `subaccount`: subaccount technical name \(a string\).
-   `locationID`: location ID \(a string\); this property is not available if the default location ID is in use.
-   `displayName`: display name of the subaccount \(a string\); this property is not available if there is no specified display name.
-   `description`: description \(a string\); this property is not available if there is no description.
-   `tunnel`: array of connection tunnels used by the subaccount.
    -   `state`: *Connected*, *ConnectFailure*, or *Disconnected*

    -   `connectedSinceTimeStamp`: connection start time as UTC timestamp
    -   `connections`: number of subaccount connections
    -   `applicationConnections`: array of connections to application instances
    -   `serviceChannels`: type and state of the service channels used \(types: HANA database, Virtual Machine or RFC\)
    -   `subaccountCertificate`: information on the subaccount certificate such as validity period, issuer and subject DN


Back to [Operations](subaccount-72885a1.md#loio72885a1eee784790a8c8d07538051134__operations)



<a name="loio72885a1eee784790a8c8d07538051134__createRecovSub"/>

## Create Recovery Subaccount \(Master Only\)

> ### Caution:  
> Disaster recovery discontinued as of version 2.16. A `POST` request to */api/v1/configuration/subaccounts/<regionHost\>/<subaccount\>/recovery* will trigger a 410 response.

Back to [Operations](subaccount-72885a1.md#loio72885a1eee784790a8c8d07538051134__operations)



<a name="loio72885a1eee784790a8c8d07538051134__deleteRecovSub"/>

## Delete Recovery Subaccount \(Master Only\)

> ### Caution:  
> Disaster recovery discontinued as of version 2.16. A `DELETE` request to */api/v1/configuration/subaccounts/<regionHost\>/<subaccount\>/recovery* will trigger a 410 response.

Back to [Operations](subaccount-72885a1.md#loio72885a1eee784790a8c8d07538051134__operations)



<a name="loio72885a1eee784790a8c8d07538051134__refreshRecovSubCert"/>

## Refresh Certificate of Recovery Subaccount \(Master Only\)

> ### Caution:  
> Disaster recovery discontinued as of version 2.16. A `POST` request to */api/v1/configuration/subaccounts/<regionHost\>/<subaccount\>/recovery/validity* will trigger a 410 response.

Back to [Operations](subaccount-72885a1.md#loio72885a1eee784790a8c8d07538051134__operations)



<a name="loio72885a1eee784790a8c8d07538051134__activateRecovSub"/>

## Activate/Deactivate Recovery Subaccount \(Master Only\)

> ### Caution:  
> Disaster recovery discontinued as of version 2.16. A `PUT` request to */api/v1/configuration/subaccounts/<regionHost\>/<subaccount\>/recovery/state* will trigger a 410 response.

Back to [Operations](subaccount-72885a1.md#loio72885a1eee784790a8c8d07538051134__operations)



<a name="loio72885a1eee784790a8c8d07538051134__takeover"/>

## Takeover \(Master Only\)

> ### Caution:  
> Disaster recovery discontinued as of version 2.16. A `POST` request to */api/v1/configuration/subaccounts/<regionHost\>/<subaccount\>/recovery/takeover* will trigger a 410 response.

Back to [Operations](subaccount-72885a1.md#loio72885a1eee784790a8c8d07538051134__operations)



<a name="loio72885a1eee784790a8c8d07538051134__syncTrustList"/>

## Synchronize Trust List \(Master Only\)

> ### Note:  
> Available as of version 2.14.0.


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/trust` 

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

Back to [Operations](subaccount-72885a1.md#loio72885a1eee784790a8c8d07538051134__operations)



<a name="loio72885a1eee784790a8c8d07538051134__getIDPTrustList"/>

## Get IDP Trust List

> ### Note:  
> Available as of version 2.14.0.


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/trust/idps` 

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
[{id, name, description, certificate, enabled}]

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

An array of objects, each of which represents a trusted IDP through the following properties:

-   `id`: \(unique\) ID of the trusted IDP \(a number\).
-   `name`: name of the trusted IDP \(a string\).
-   `description`: description of the trusted IDP \(a string\)
-   `certificate`: object with the following properties: `issuer` \(a string\), `subjectDN` \(a string\), `notBeforeTimeStamp` \(a UTC long number\), and `notAfterTimeStamp` \(a UTC long number\).
-   `enabled`: flag that indicates whether the IDP is enabled or disabled \(that is, whether the IDP is trusted or not\).

Back to [Operations](subaccount-72885a1.md#loio72885a1eee784790a8c8d07538051134__operations)



<a name="loio72885a1eee784790a8c8d07538051134__gestAppTrustList"/>

## Get Application Trust List

> ### Note:  
> Available as of version 2.14.0.


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/trust/apps` 

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
[{id, name, applicationType, enabled}]

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

An array of objects, each of which represents a trusted application through the following properties:

-   `id`: \(unique\) ID of the trusted application \(a number\).
-   `name`: name of the trusted application \(a string\).
-   `applicationType`: type of the application \(a string, for example 'JAVA' or 'HANA'\).
-   `enabled`: flag that indicates whether the application is enabled or disabled \(that is, whether the application is trusted or not\).

Back to [Operations](subaccount-72885a1.md#loio72885a1eee784790a8c8d07538051134__operations)



<a name="loio72885a1eee784790a8c8d07538051134__enableTrust"/>

## Enable Or Disable Trust \(Master Only\)

Replace <type\> with the type \(either *apps* or *idps*\) that belongs to the specified <id\>.


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/trust/<type>/<id>` 

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
{enabled}

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

NOT\_FOUND

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

-   `enabled`: true or false, indicating the specified trust source should be enabled or disabled.

**Errors**:

-   `NOT_FOUND` \(404\): specified <id\> does not exist for the given <type\>.

Back to [Operations](subaccount-72885a1.md#loio72885a1eee784790a8c8d07538051134__operations)



<a name="loio72885a1eee784790a8c8d07538051134__getIDPTrustProperties"/>

## Get IDP Trust Properties


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/trust/idps/<id>` 

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
{id, name, description, certificate, enabled}

```



</td>
</tr>
<tr>
<td valign="top">

Errors

</td>
<td valign="top">

NOT\_FOUND

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

**Response Properties**:

-   `id`: \(unique\) ID of the trusted IDP \(a number\).
-   `name`: name of the trusted IDP \(a string\).
-   `description`: description of the trusted IDP \(a string\).
-   `certificate`: object with the following properties: `issuer` \(a string\), `subjectDN` \(a string\), `notBeforeTimeStamp` \(a UTC long number\), and `notAfterTimeStamp` \(a UTC long number\).
-   `enabled`: flag that indicates whether the IDP is enabled or disabled \(that is, whether the IDP is trusted or not\).

**Errors**:

-   `NOT_FOUND` \(404\): There is no trusted IDP with the given <id\>

Back to [Operations](subaccount-72885a1.md#loio72885a1eee784790a8c8d07538051134__operations)



<a name="loio72885a1eee784790a8c8d07538051134__getAppTrustProperties"/>

## Get Application Trust Properties


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/trust/apps/<id>` 

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
{id, name, applicationType, enabled}

```



</td>
</tr>
<tr>
<td valign="top">

Errors

</td>
<td valign="top">

NOT\_FOUND

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

**Response Properties**:

-   `id`: \(unique\) ID of the trusted application \(a number\).
-   `name`: name of the trusted application \(a string\).
-   `applicationType`: type of the application \(a string, for example 'JAVA' or 'HANA'\).
-   `enabled`: flag that indicates whether the application is enabled or disabled \(that is, whether the application is trusted or not\).

**Errors**:

-   `NOT_FOUND` \(404\): There is no trusted application with the given <id\>.

Back to [Operations](subaccount-72885a1.md#loio72885a1eee784790a8c8d07538051134__operations)

