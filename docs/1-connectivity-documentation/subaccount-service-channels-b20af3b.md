<!-- loiob20af3bf34b441228c2f095744019758 -->

# Subaccount Service Channels

Manage Cloud Connector service channels via API.

> ### Note:  
> Access to *managed* subaccounts is reserved for the role *Administrator* for all methods except for method GET.
> 
> For more information on managed subaccounts, see [Adding a Subaccount](adding-and-managing-subaccounts-f16df12.md#loiof16df12fab9f4fe1b8a4122f0fd54b6e__add) \(step 2\).


<table>
<tr>
<td valign="top">

**Service Channel for HANA Database**

</td>
<td valign="top">

[Get all HANA Service Channels](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__get_hana_all) 

[Get Available HANA Channels](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__get_hana_available) 

[Get HANA Service Channel](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__get_hana) 

[Create HANA Service Channel \(Master Only\)](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__create_hana) 

[Replace HANA Service Channel \(Master Only\)](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__edit_hana) 

</td>
</tr>
<tr>
<td valign="top">

**Service Channel for Virtual Machine**

</td>
<td valign="top">

[Get all Service Channels for Virtual Machines](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__get_vm_all)

[Get Available Channels for Virtual Machines](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__get_vm_available)

[Get Service Channel for a Virtual Machine](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__get_vm)

[Create a Service Channel for a Virtual Machine \(Master Only\)](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__create_vm)

[Replace a Service Channel for a Virtual Machine \(Master Only\)](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__edit_vm) 

</td>
</tr>
<tr>
<td valign="top">

**Service Channel for ABAP Cloud**

</td>
<td valign="top">

[Get all ABAP Cloud Service Channels without SNC](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__get_abap_all)

[Get ABAP Cloud Service Channel without SNC](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__get_abap)

[Create ABAP Cloud Service Channel without SNC \(Master Only\)](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__create_abap)

[Replace ABAP Cloud Service Channel without SNC \(Master Only\)](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__edit_abap) 

[Get all ABAP Cloud SNC-Encrypted Service Channels](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__get_abap_all_SNC)

[Get ABAP Cloud SNC-Encrypted Service Channel](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__get_abap_SNC)

[Create ABAP Cloud SNC-Encrypted Service Channel \(Master Only\)](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__create_abap_SNC)

[Replace ABAP Cloud SNC-Encrypted Service Channel \(Master Only\)](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__edit_abap_SNC) 

</td>
</tr>
<tr>
<td valign="top">

**Service Channel for Kubernetes**

> ### Note:  
> Available as of version 2.15.0.



</td>
<td valign="top">

[Get All Kubernetes Cluster Service Channels](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__get_all_k8s)

[Get Kubernetes Service Channel](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__get_k8s) 

[Create Kubernetes Service Channel \(Master Only\)](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__create_k8s)

[Replace Kubernetes Service Channel \(Master Only\)](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__replace_k8s)

</td>
</tr>
<tr>
<td valign="top">

*General*

</td>
<td valign="top">

[Enable/Disable Service Channel \(Master Only\)](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__enable)

[Delete Service Channel \(Master Only\)](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__delete)

[Delete all Service Channels \(Master Only\)](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__delete_all)

</td>
</tr>
<tr>
<td valign="top">

*Deprecated*

</td>
<td valign="top">

[Get all Service Channels](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__get_all)

[Get Service Channel](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__get)

[Create Service Channel](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__create)

[Replace Service Channel](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__edit)

</td>
</tr>
</table>



<a name="loiob20af3bf34b441228c2f095744019758__get_hana_all"/>

## Get all HANA Service Channels


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/channels/HANA` 

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
[{id, hanaInstanceName, instanceNumber, type, port, enabled, connections, state}]

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

**Response**:

An array of objects, each of which represents a HANA service channel through the following properties:

-   `id`: unique identifier for the service channel \(a positive integer number, starting with 1\). This identifier is unique across all types of service channels.

-   `hanaInstanceName`: name of the HANA instance \(a string\).

-   `instanceNumber`: instance number.

-   `type`: string 'HANA'.

-   `port`: port of the HANA service channel \(a number\).

-   `enabled`: boolean flag indicating whether the channel is enabled and therefore should be open.

-   `connections`: maximal number of open connections.

-   `state`: current connection state; this property is only available if the channel is enabled \(as per property `enabled`\). The value of this property is an object with the properties:

    -   `connected` \(a boolean flag indicating whether the channel is connected\),
    -   `openedConnections` \(the number of open, possibly idle connections\), and
    -   `connectedSinceTimeStamp` \(the time stamp, a UTC long number, for the first time the channel was opened/connected\).


Back to [Top](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__top)



<a name="loiob20af3bf34b441228c2f095744019758__get_hana_available"/>

## Get Available HANA Channels


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/availableChannels/HANA` 

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
[{hanaInstanceName, version, type}]

```



</td>
</tr>
<tr>
<td valign="top">

Errors

</td>
<td valign="top">

RUNTIME\_FAILURE

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

**Response**:

-   `hanaInstanceName`: name of the HANA instance.

-   `version`: version information.

-   `type`: specific HANA database type \(*not* the service channel type\).


**Errors**:

-   RUNTIME\_FAILURE \(500\): the list of available HANA database instances could not be retrieved.

Back to [Top](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__top)



<a name="loiob20af3bf34b441228c2f095744019758__get_hana"/>

## Get HANA Service Channel


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/channels/HANA/<id>` 

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
{id, hanaInstanceName, instanceNumber, type, port, enabled, connections, state, comment}
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

Administrator, Associate Administrator, Subaccount Administrator, Display, Support, Monitoring

</td>
</tr>
</table>

****:

-   `id`: unique identifier for the service channel \(a positive integer number, starting with 1\). This identifier is unique across all types of service channels.

-   `hanaInstanceName`: name of the HANA instance \(a string\).

-   `instanceNumber`: instance number.

-   `type`: string 'HANA'.

-   `port`: port of the HANA service channel \(a number\).

-   `enabled`: boolean flag indicating whether the channel is enabled and therefore should be open.

-   `connections`: maximal number of open connections.

-   `state`: current connection state; this property is only available if the channel is enabled \(as per property `enabled`\). The value of this property is an object with the properties:

    -   `connected` \(a boolean flag indicating whether the channel is connected\),
    -   `openedConnections` \(the number of open, possibly idle connections\), and
    -   `connectedSinceTimeStamp` \(the time stamp, a UTC long number, for the first time the channel was opened/connected\).

-   `comment`: comment or short description; this property is not supplied if no comment was provided.

**Errors**:

-   NOT\_FOUND \(404\): the HANA service channel with the given ID \(that is, <id\>\) or the specified subaccount does not exist.

Back to [Top](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__top)



<a name="loiob20af3bf34b441228c2f095744019758__create_hana"/>

## Create HANA Service Channel \(Master Only\)


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/channels/HANA` 

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
{hanaInstanceName, instanceNumber, connections}

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

INVALID\_REQUEST

</td>
</tr>
<tr>
<td valign="top">

Roles

</td>
<td valign="top">

Administrator, Associate Administrator, Subaccount Administrator

</td>
</tr>
</table>

**Request**:

**Errors**:

-   INVALID\_REQUEST \(400\): invalid or out of range values.

Back to [Top](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__top)



<a name="loiob20af3bf34b441228c2f095744019758__edit_hana"/>

## Replace HANA Service Channel \(Master Only\)


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/channels/HANA/<id>` 

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
{hanaInstanceName, instanceNumber, connections}

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

INVALID\_REQUEST, NOT\_FOUND

</td>
</tr>
<tr>
<td valign="top">

Roles

</td>
<td valign="top">

Administrator, Associate Administrator, Subaccount Administrator

</td>
</tr>
</table>

**Request**:

-   `hanaInstanceName`: name of the HANA instance \(a string\).

-   `instanceNumber`: instance number.

-   `connections`: maximal number of open connections.


**Errors**:

-   INVALID\_REQUEST \(400\): invalid or out of range values.
-   NOT\_FOUND \(404\): the HANA service channel with the given ID \(that is, <id\>\) or the specified subaccount does not exist.

Back to [Top](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__top)



<a name="loiob20af3bf34b441228c2f095744019758__get_vm_all"/>

## Get all Service Channels for Virtual Machines


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/channels/VirtualMachine` 

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
[{id, name, endpointId, type, port, enabled, connections, state}]

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

**Response**:

-   `id`: unique identifier for the service channel \(a positive integer number, starting with 1\). This identifier is unique across all types of service channels.

-   `name`: name of the virtual machine on the cloud platform \(a string\).

-   `endpointId`: unique ID \(GUID\) of the virtual machine \(a string\).

-   `type`: string 'VirtualMachine'.

-   `port`: port of the service channel for the virtual machine \(a number\).

-   `enabled`: boolean flag indicating whether the channel is enabled and therefore should be open.

-   `connections`: maximal number of open connections.

-   `state`: current connection state; this property is only available if the channel is enabled \(as per property `enabled`\). The value of this property is an object with the properties:

    -   `connected` \(a boolean flag indicating whether the channel is connected\),
    -   `openedConnections` \(the number of open, possibly idle connections\), and
    -   `connectedSinceTimeStamp` \(the time stamp, a UTC long number, for the first time the channel was opened/connected\).


Back to [Top](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__top)



<a name="loiob20af3bf34b441228c2f095744019758__get_vm_available"/>

## Get Available Channels for Virtual Machines


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/availableChannels/VirtualMachine` 

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
[{endpointId, name}]

```



</td>
</tr>
<tr>
<td valign="top">

Errors

</td>
<td valign="top">

RUNTIME\_FAILURE

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

**Response**:

-   `name`: name of the virtual machine on the cloud platform \(a string\).

-   `endpointId`: unique ID \(GUID\) of the virtual machine \(a string\).


**Errors**:

-   RUNTIME\_FAILURE \(500\): the list of available virtual machines could not be retrieved.

Back to [Top](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__top)



<a name="loiob20af3bf34b441228c2f095744019758__get_vm"/>

## Get Service Channel for a Virtual Machine


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/channels/VirtualMachine/<id>` 

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
{id, name, endpointId, type, port, enabled, connections, state}

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

Administrator, Associate Administrator, Subaccount Administrator, Display, Support, Monitoring

</td>
</tr>
</table>

**Response**:

-   `id`: unique identifier for the service channel \(a positive integer number, starting with 1\). This identifier is unique across all types of service channels.

-   `name`: name of the virtual machine on the cloud platform \(a string\).

-   `endpointId`: unique ID \(GUID\) of the virtual machine \(a string\).

-   `type`: string 'VirtualMachine'.

-   `port`: port of the service channel for the virtual machine \(a number\).

-   `enabled`: boolean flag indicating whether the channel is enabled and therefore should be open.

-   `connections`: maximal number of open connections.

-   `state`: current connection state; this property is only available if the channel is enabled \(as per property `enabled`\). The value of this property is an object with the properties:

    -   `connected` \(a boolean flag indicating whether the channel is connected\),
    -   `openedConnections` \(the number of open, possibly idle connections\), and
    -   `connectedSinceTimeStamp` \(the time stamp, a UTC long number, for the first time the channel was opened/connected\).


**Errors**:

-   NOT\_FOUND \(404\): the service channel for a virtual machine with the given ID \(that is, <id\>\) or the specified subaccount does not exist.

Back to [Top](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__top)



<a name="loiob20af3bf34b441228c2f095744019758__create_vm"/>

## Create a Service Channel for a Virtual Machine \(Master Only\)


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/channels/VirtualMachine` 

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
{name, endpointId, port, connections}

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

INVALID\_REQUEST

</td>
</tr>
<tr>
<td valign="top">

Roles

</td>
<td valign="top">

Administrator, Associate Administrator, Subaccount Administrator

</td>
</tr>
</table>

**Request**:

-   `name`: name of the virtual machine on the cloud platform \(a string\).

-   `endpointId`: unique ID \(GUID\) of the virtual machine \(a string\).

-   `port`: port of the service channel for the virtual machine \(a number\).

-   `connections`: maximal number of open connections.

**Errors**:

-   INVALID\_REQUEST \(400\): invalid or out of range values.

Back to [Top](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__top)



<a name="loiob20af3bf34b441228c2f095744019758__edit_vm"/>

## Replace Service Channel for a Virtual Machine \(Master Only\)


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/channels/VirtualMachine/<id>` 

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
{name, endpointId, connections}

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

INVALID\_REQUEST, NOT\_FOUND

</td>
</tr>
<tr>
<td valign="top">

Roles

</td>
<td valign="top">

Administrator, Associate Administrator, Subaccount Administrator

</td>
</tr>
</table>

**Request**:

-   `name`: name of the virtual machine on the cloud platform \(a string\).

-   `endpointId`: unique ID \(GUID\) of the virtual machine \(a string\).

-   `port`: port of the service channel for the virtual machine \(a number\).

-   `connections`: maximal number of open connections.

**Errors**:

-   INVALID\_REQUEST \(400\): invalid or out of range values.
-   NOT\_FOUND \(404\): the service channel for a virtual machine with the given ID \(that is, <id\>\) or the specified subaccount does not exist.

Back to [Top](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__top)



<a name="loiob20af3bf34b441228c2f095744019758__get_abap_all"/>

## Get all ABAP Cloud Service Channels without SNC


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/channels/ABAPCloud` 

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
[{id, abapCloudTenantHost, instanceNumber, type, port, enabled, connections, state, comment}]

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

**Response**:

An array of objects, each of which represents an ABAP Cloud service channel through the following properties:

-   `id`: unique identifier for the service channel \(a positive integer number, starting with 1\). This identifier is unique across all types of service channels.

-   `abapCloudTenantHost`: the host name \(a string\).

-   `instanceNumber`: instance number.

-   `type`: string 'ABAPCloud'.

-   `port`: port of the ABAPCloud service channel \(a number\).

-   `enabled`: boolean flag indicating whether the channel is enabled and therefore should be open.

-   `connections`: maximal number of open connections.

-   `state`: current connection state; this property is only available if the channel is enabled \(as per property `enabled`\). The value of this property is an object with the properties:

    -   `connected` \(a boolean flag indicating whether the channel is connected\),
    -   `openedConnections` \(the number of open, possibly idle connections\), and
    -   `connectedSinceTimeStamp` \(the time stamp, a UTC long number, for the first time the channel was opened/connected\).

-   `comment`: optional comment or short description. This property is not supplied if no comment was provided.

Back to [Top](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__top)



<a name="loiob20af3bf34b441228c2f095744019758__get_abap"/>

## Get ABAP Cloud Service Channel without SNC


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/channels/ABAPCloud/<id>` 

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
{id, abapCloudTenantHost, instanceNumber, type, port, enabled, connections, state, comment}

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

Administrator, Associate Administrator, Subaccount Administrator, Display, Support, Monitoring

</td>
</tr>
</table>

**Response**:

-   `id`: unique identifier for the service channel \(a positive integer number, starting with 1\). This identifier is unique across all types of service channels.

-   `abapCloudTenantHost`: the host name \(a string\).

-   `instanceNumber`: instance number.

-   `type`: string 'ABAPCloud'.

-   `port`: port of the ABAPCloud service channel \(a number\).

-   `enabled`: boolean flag indicating whether the channel is enabled and therefore should be open.

-   `connections`: maximal number of open connections.

-   `state`: current connection state; this property is only available if the channel is enabled \(as per property `enabled`\). The value of this property is an object with the properties:

    -   `connected` \(a boolean flag indicating whether the channel is connected\),
    -   `openedConnections` \(the number of open, possibly idle connections\), and
    -   `connectedSinceTimeStamp` \(the time stamp, a UTC long number, for the first time the channel was opened/connected\).

-   `comment`: optional comment or short description. This property is not supplied if no comment was provided.

**Errors**:

-   NOT\_FOUND \(404\): the ABAP Cloud service channel with the given ID \(that is, <id\>\) or the specified subaccount does not exist.

Back to [Top](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__top)



<a name="loiob20af3bf34b441228c2f095744019758__create_abap"/>

## Create ABAP Cloud Service Channel without SNC \(Master Only\)


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/channels/ABAPCloud` 

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
{abapCloudTenantHost, instanceNumber, connections, comment}

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

INVALID\_REQUEST

</td>
</tr>
<tr>
<td valign="top">

Roles

</td>
<td valign="top">

Administrator, Associate Administrator, Subaccount Administrator

</td>
</tr>
</table>

**Request**:

-   `abapCloudTenantHost`: host name \(a string\).

-   `instanceNumber`: instance number.

-   `connections`: maximal number of open connections.

-   `comment`: optional comment or short description \(a string\)

**Errors**:

-   INVALID\_REQUEST \(400\): invalid or out of range values.

Back to [Top](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__top)



<a name="loiob20af3bf34b441228c2f095744019758__edit_abap"/>

## Replace ABAP Cloud Service Channel without SNC \(Master Only\)


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/channels/ABAPCloud/<id>` 

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
{abapCloudTenantHost, instanceNumber, connections, comment}

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

INVALID\_REQUEST, NOT\_FOUND

</td>
</tr>
<tr>
<td valign="top">

Roles

</td>
<td valign="top">

Administrator, Associate Administrator, Subaccount Administrator

</td>
</tr>
</table>

**Request**:

-   `abapCloudTenantHost`: host name \(a string\).

-   `instanceNumber`: instance number.

-   `connections`: maximal number of open connections.

-   `comment`: optional comment or short description \(a string\).

**Errors**:

-   INVALID\_REQUEST \(400\): invalid or out of range values.
-   NOT\_FOUND \(404\): the ABAP Cloud service channel with the given ID \(that is, <id\>\) or the specified subaccount does not exist.

Back to [Top](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__top)



<a name="loiob20af3bf34b441228c2f095744019758__get_abap_all_SNC"/>

## Get all ABAP Cloud SNC-Encrypted Service Channels


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/channels/ABAPCloudSNC` 

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
[{id, abapCloudTenantHost, instanceNumber, type, port, enabled, connections, state, comment}]

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

**Response**:

An array of objects, each of which represents an ABAP Cloud service channel \(SNC-encrypted\) through the following properties:

-   `id`: unique identifier for the service channel \(a positive integer number, starting with 1\). This identifier is unique across all types of service channels.

-   `abapCloudTenantHost`: the host name \(a string\).

-   `instanceNumber`: instance number.

-   `type`: string 'ABAPCloudSNC.

-   `port`: port of the ABAPCloud service channel \(a number\).

-   `enabled`: boolean flag indicating whether the channel is enabled and therefore should be open.

-   `connections`: maximal number of open connections.

-   `state`: current connection state; this property is only available if the channel is enabled \(as per property `enabled`\). The value of this property is an object with the properties:

    -   `connected` \(a boolean flag indicating whether the channel is connected\),
    -   `openedConnections` \(the number of open, possibly idle connections\), and
    -   `connectedSinceTimeStamp` \(the time stamp, a UTC long number, for the first time the channel was opened/connected\).

-   `comment`: optional comment or short description. This property is not supplied if no comment was provided.

Back to [Top](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__top)



<a name="loiob20af3bf34b441228c2f095744019758__get_abap_SNC"/>

## Get ABAP Cloud SNC-Encrypted Service Channel


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/channels/ABAPCloudSNC/<id>` 

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
{id, abapCloudTenantHost, instanceNumber, type, port, enabled, connections, state, comment}

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

Administrator, Associate Administrator, Subaccount Administrator, Display, Support, Monitoring

</td>
</tr>
</table>

**Response**:

-   `id`: unique identifier for the service channel \(a positive integer number, starting with 1\). This identifier is unique across all types of service channels.

-   `abapCloudTenantHost`: the host name \(a string\).

-   `instanceNumber`: instance number.

-   `type`: string 'ABAPCloudSNC.

-   `port`: port of the ABAPCloud service channel \(a number\).

-   `enabled`: boolean flag indicating whether the channel is enabled and therefore should be open.

-   `connections`: maximal number of open connections.

-   `state`: current connection state; this property is only available if the channel is enabled \(as per property `enabled`\). The value of this property is an object with the properties:

    -   `connected` \(a boolean flag indicating whether the channel is connected\),
    -   `openedConnections` \(the number of open, possibly idle connections\), and
    -   `connectedSinceTimeStamp` \(the time stamp, a UTC long number, for the first time the channel was opened/connected\).

-   `comment`: optional comment or short description. This property is not supplied if no comment was provided.

**Errors**:

-   NOT\_FOUND \(404\): the ABAP Cloud service channel with the given ID \(that is, <id\>\) or the specified subaccount does not exist.

Back to [Top](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__top)



<a name="loiob20af3bf34b441228c2f095744019758__create_abap_SNC"/>

## Create ABAP Cloud SNC-Encrypted Service Channel \(Master Only\)


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/channels/ABAPCloudSNC` 

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
{abapCloudTenantHost, instanceNumber, connections, comment}

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

INVALID\_REQUEST

</td>
</tr>
<tr>
<td valign="top">

Roles

</td>
<td valign="top">

Administrator, Associate Administrator, Subaccount Administrator

</td>
</tr>
</table>

**Request**:

-   `abapCloudTenantHost`: host name \(a string\).

-   `instanceNumber`: instance number.

-   `connections`: maximal number of open connections.

-   `comment`: optional comment or short description \(a string\).

**Errors**:

-   INVALID\_REQUEST \(400\): invalid or out of range values.

Back to [Top](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__top)



<a name="loiob20af3bf34b441228c2f095744019758__edit_abap_SNC"/>

## Replace ABAP Cloud SNC-Encrypted Service Channel \(Master Only\)


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/channels/ABAPCloudSNC/<id>` 

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
{abapCloudTenantHost, instanceNumber, connections, comment}

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

INVALID\_REQUEST, NOT\_FOUND

</td>
</tr>
<tr>
<td valign="top">

Roles

</td>
<td valign="top">

Administrator, Associate Administrator, Subaccount Administrator

</td>
</tr>
</table>

**Request**:

-   `abapCloudTenantHost`: host name \(a string\).

-   `instanceNumber`: instance number.

-   `connections`: maximal number of open connections.

-   `comment`: optional comment or short description \(a string\).

**Errors**:

-   INVALID\_REQUEST \(400\): invalid or out of range values.
-   NOT\_FOUND \(404\): the ABAP Cloud service channel with the given ID \(that is, <id\>\) or the specified subaccount does not exist.

Back to [Top](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__top)



<a name="loiob20af3bf34b441228c2f095744019758__get_all_k8s"/>

## Get All Kubernetes Cluster Service Channels


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/channels/K8S` 

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
[{id, type, port, k8sCluster, k8sService, enabled, connections, state, comment}]
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

**Response**:

An array of objects, each of which represents a service channel for a virtual machine through the following properties:

-   `id`: unique identifier for the service channel \(a positive integer number, starting with 1\); this identifier is unique across all types of service channels.
-   `k8sCluster`: host name to access the Kubernetes cluster \(a string\).
-   `k8sService`: host name providiing the service inside of Kubernetes cluster \(a string\).
-   `type`: the string *'K8S'*.
-   `port`: port of the service channel for the virtual machine \(a number\).
-   `enabled`: Boolean flag indicating whether the channel is enabled and therefore should be open.
-   `connections`: maximal number of open connections.
-   `state`: current connection state; this property is only available if the channel is enabled \(as per property `enabled`\). The value of this property is an object with the properties `connected` \(a Boolean flag indicating whether the channel is connected\), `openedConnections` \(the number of open, possibly idle connections\), and `connectedSinceTimeStamp` \(the time stamp, a UTC long number, for the first time the channel was opened/connected\).
-   `comment`: comment or short description; this property is not supplied if no comment was provided.

Back to [Top](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__top)



<a name="loiob20af3bf34b441228c2f095744019758__get_k8s"/>

## Get Kubernetes Service Channel


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/channels/K8S/<id>` 

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
[{id, type, port, k8sCluster, k8sService, enabled, connections, state, comment}]
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

**Response**:

-   `id`: unique identifier for the service channel \(a positive integer number, starting with 1\); this identifier is unique across all types of service channels.
-   `k8sCluster`: host name to access the Kubernetes cluster \(a string\).
-   `k8sService`: host name providiing the service inside of Kubernetes cluster \(a string\).
-   `type`: the string *'K8S'*.
-   `port`: port of the service channel for the virtual machine \(a number\).
-   `enabled`: Boolean flag indicating whether the channel is enabled and therefore should be open.
-   `connections`: maximal number of open connections.
-   `state`: current connection state; this property is only available if the channel is enabled \(as per property `enabled`\). The value of this property is an object with the properties `connected` \(a Boolean flag indicating whether the channel is connected\), `openedConnections` \(the number of open, possibly idle connections\), and `connectedSinceTimeStamp` \(the time stamp, a UTC long number, for the first time the channel was opened/connected\).
-   `comment`: comment or short description; this property is not supplied if no comment was provided.

Back to [Top](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__top)



<a name="loiob20af3bf34b441228c2f095744019758__create_k8s"/>

## Create Kubernetes Service Channel \(Master Only\)


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/channels/K8S` 

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
{k8sCluster, k8sService, port, connections, comment}
```



</td>
</tr>
<tr>
<td valign="top">

Response

</td>
<td valign="top">

201

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

Administrator, Associate Administrator, Subaccount Administrator

</td>
</tr>
</table>

**Request**:

-   `k8sCluster`: Kubernetes cluster host name, optionally with port separated by colon \(a string\).
-   `k8sService`: service host inside the Kubernetes cluster \(a string\).
-   `port`: local port.
-   `connections`: maximal number of open connections.
-   `comment`: optional comment or short description \(a string\).

**Errors**:

-   INVALID\_REQUEST \(400\): invalid or out-of-range values.

Back to [Top](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__top)



<a name="loiob20af3bf34b441228c2f095744019758__replace_k8s"/>

## Replace Kubernetes Service Channel \(Master Only\)


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/channels/K8S/<id>` 

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
{k8sCluster, k8sService, port, connections, comment}
```



</td>
</tr>
<tr>
<td valign="top">

Response

</td>
<td valign="top">

INVALID\_REQUEST, NOT\_FOUND

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

Administrator, Associate Administrator, Subaccount Administrator

</td>
</tr>
</table>

**Request**:

-   `k8sCluster`: Kubernetes cluster host name, optionally with port separated by colon \(a string\).
-   `k8sService`: service host inside the Kubernetes cluster \(a string\).
-   `port`: local port.
-   `connections`: maximal number of open connections.
-   `comment`: optional comment or short description \(a string\).

**Errors**:

-   INVALID\_REQUEST \(400\): invalid or out-of-range values.
-   NOT\_FOUND \(404\): the Kyma service channel with the given ID \(that is, `<id>`\) or the specified subaccount does not exist.

Back to [Top](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__top)



<a name="loiob20af3bf34b441228c2f095744019758__enable"/>

## Enable/Disable Service Channel \(Master Only\)

Use one of the following channel types to replace <type\> in the URI: HANA, VirtualMachine, or ABAPCloud.

> ### Caution:  
> The URI variant without <type\> still works, but it is obsolete and may be removed in a future release. We recommend that you move to using <type\> as soon as possible.


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/channels/<type>/<id>/state` 

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



</td>
</tr>
<tr>
<td valign="top">

Errors

</td>
<td valign="top">

NOT\_FOUND, RUNTIME\_FAILURE

</td>
</tr>
<tr>
<td valign="top">

Roles

</td>
<td valign="top">

Administrator, Associate Administrator, Subaccount Administrator

</td>
</tr>
</table>

**Errors**:

-   NOT\_FOUND \(404\): service channel \(or subaccount\) does not exist.
-   RUNTIME\_FAILURE \(500\): service channel could not be opened \(when attempting to set `enabled:true`\).

Back to [Top](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__top)



<a name="loiob20af3bf34b441228c2f095744019758__delete"/>

## Delete Service Channel \(Master Only\)

> ### Caution:  
> The URI variant without <type\> still works, but it is obsolete and may be removed in a future release. We recommend to move to using <type\> as soon as possible.


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/channels/<type>/<id>` 

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

NOT\_FOUND

</td>
</tr>
<tr>
<td valign="top">

Roles

</td>
<td valign="top">

Administrator, Associate Administrator, Subaccount Administrator

</td>
</tr>
</table>

**Errors**:

-   NOT\_FOUND \(404\): service channel \(or subaccount\) does not exist.

Back to [Top](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__top)



<a name="loiob20af3bf34b441228c2f095744019758__delete_all"/>

## Delete all Service Channels \(Master Only\)

> ### Note:  
> Omit <type\> to delete all service channels, regardless of the type. To delete all service channels of a particular type, replace <type\> with one of the following channel types: HANA, VirtualMachine, or ABAPCloud.


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/channels[/<type>]` 

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

Administrator, Associate Administrator, Subaccount Administrator

</td>
</tr>
</table>

Back to [Top](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__top)



<a name="loiob20af3bf34b441228c2f095744019758__get_all"/>

## Get Service Channels

> ### Caution:  
> **Obsolete**. This API is deprecated and may be removed in a future release. Use the getters for the specific service channel type \(that is, HANA \(database\), Virtual Machine, or ABAP Cloud\) which provide properties tailored for the respective channel type.


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/channels` 

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
[{typeDesc, details, port, enabled, connected, connectionsCount, availableConnectionsCount, connectedSinceTimeStamp}]

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

**Response**:

An array of objects, each of which represents a service channel through the following properties:

-   `typeDesc`: an object specifying the service channel type through the properties `typeKey` and `typeName`.
-   `details`
-   `port`
-   `enabled`
-   `connected`
-   `connectionsCount`
-   `availableConnectionsCount`
-   `connectedSinceTimeStamp`

Back to [Top](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__top)



<a name="loiob20af3bf34b441228c2f095744019758__get"/>

## Get Service Channel

> ### Caution:  
> **Obsolete**. This API is deprecated and may be removed in a future release. Use the getters for the specific service channel type \(that is, HANA \(database\), Virtual Machine, or ABAP Cloud\) which provide properties tailored for the respective channel type.


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/channels/<id>` 

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
[{typeDesc, details, port, enabled, connected, connectionsCount, availableConnectionsCount, connectedSinceTimeStamp}]

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

**Response**:

-   `typeDesc`: an object specifying the service channel type through the properties `typeKey` and `typeName`.
-   `details`
-   `port`
-   `enabled`
-   `connected`
-   `connectionsCount`
-   `availableConnectionsCount`
-   `connectedSinceTimeStamp`

Back to [Top](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__top)



<a name="loiob20af3bf34b441228c2f095744019758__create"/>

## Create Service Channel

> ### Caution:  
> **Obsolete**. This API is deprecated and may be removed in a future release. Create a service channel using the API for the respective channel type, that is, HANA \(database\), Virtual Machine, or ABAP Cloud.


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/channels` 

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
{typeKey,details,serviceNumber,connectionCount}
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

Administrator, Associate Administrator, Subaccount Administrator

</td>
</tr>
</table>

**Request Properties**:

-   `typeKey`: type of service channel. Valid values are HANA\_DB, HCPVM, RFC.
-   `details`:
    -   HANA instance name for HANA\_DB
    -   VM name for HCPVM
    -   S/4HANA Cloud tenant host for RFC

-   `serviceNumber`: service number, which is mapped to a port according to the type of service channel.
-   `connectionCount`: number of connections for the channel.

Back to [Top](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__top)



<a name="loiob20af3bf34b441228c2f095744019758__edit"/>

## Replace Service Channel

> ### Caution:  
> **Obsolete**. This API is deprecated and may be removed in a future release. Replace a service channel using the API for the respective channel type, that is, HANA \(database\), Virtual Machine, or ABAP Cloud.


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/channels/<id>` 

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
{typeKey,details,serviceNumber,connectionCount}
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

Administrator, Associate Administrator, Subaccount Administrator

</td>
</tr>
</table>

Back to [Top](subaccount-service-channels-b20af3b.md#loiob20af3bf34b441228c2f095744019758__top)

