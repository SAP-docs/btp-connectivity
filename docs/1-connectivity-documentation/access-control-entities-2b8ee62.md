<!-- loio2b8ee62d19db43649365f82f78b185a0 -->

# Access Control Entities

Manage RFC-specific access control entities for the Cloud Connector via API.

[Get List Of Allowed Clients](access-control-entities-2b8ee62.md#loio2b8ee62d19db43649365f82f78b185a0__get_allowed)

[Get List Of Blocked Client/User Pairs](access-control-entities-2b8ee62.md#loio2b8ee62d19db43649365f82f78b185a0__get_blocked)

[Create Allowed Clients \(Master Only\)](access-control-entities-2b8ee62.md#loio2b8ee62d19db43649365f82f78b185a0__create_allowed)

[Extend Allowed Clients \(Master Only\)](access-control-entities-2b8ee62.md#loio2b8ee62d19db43649365f82f78b185a0__extend_allowed)

[Create Blocked Client/User Pairs \(Master Only\)](access-control-entities-2b8ee62.md#loio2b8ee62d19db43649365f82f78b185a0__create_blocked)

[Extend Blocked Client/User Pairs \(Master Only\)](access-control-entities-2b8ee62.md#loio2b8ee62d19db43649365f82f78b185a0__extend_blocked)

[Delete All Allowed Clients \(Master Only\)](access-control-entities-2b8ee62.md#loio2b8ee62d19db43649365f82f78b185a0__delete_clients)

[Delete All Blocked Client/User Pairs \(Master Only\)](access-control-entities-2b8ee62.md#loio2b8ee62d19db43649365f82f78b185a0__delete_blocked)

[Remove an Item from the List of Allowed Clients \(Master Only\)](access-control-entities-2b8ee62.md#loio2b8ee62d19db43649365f82f78b185a0__remove_allowed)

[Remove an Item from the List of Blocked Client/User Pairs \(Master Only\)](access-control-entities-2b8ee62.md#loio2b8ee62d19db43649365f82f78b185a0__remove_pair)



<a name="loio2b8ee62d19db43649365f82f78b185a0__get_allowed"/>

## Get List Of Allowed Clients


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/systemMappings/<virtualHost>:<virtualPort>/allowedClients` 

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
[{client}]

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

List of objects, each representing an allowed client:

-   `client`: client name


Back to [Top](access-control-entities-2b8ee62.md#loio2b8ee62d19db43649365f82f78b185a0__top)



<a name="loio2b8ee62d19db43649365f82f78b185a0__get_blocked"/>

## Get List Of Blocked Client/User Pairs


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/systemMappings/<virtualHost>:<virtualPort>/blockedClientUsers` 

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
[{client, user}]

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

List of objects, each representing a blocked client and user:

-   `client`: client name

    `user`: user name


Back to [Top](access-control-entities-2b8ee62.md#loio2b8ee62d19db43649365f82f78b185a0__top)



<a name="loio2b8ee62d19db43649365f82f78b185a0__create_allowed"/>

## Create Allowed Clients \(Master Only\)


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/systemMappings/<virtualHost>:<virtualPort>/allowedClients` 

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
[client]

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

**Request**:

List of strings, each representing an allowed client.

Back to [Top](access-control-entities-2b8ee62.md#loio2b8ee62d19db43649365f82f78b185a0__top)



<a name="loio2b8ee62d19db43649365f82f78b185a0__extend_allowed"/>

## Add Allowed Clients \(Master Only\)


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/systemMappings/<virtualHost>:<virtualPort>/allowedClients` 

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
[client]

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

**Request**:

List of strings, each representing an allowed client.

Back to [Top](access-control-entities-2b8ee62.md#loio2b8ee62d19db43649365f82f78b185a0__top)



<a name="loio2b8ee62d19db43649365f82f78b185a0__create_blocked"/>

## Create Blocked Client/User Pairs \(Master Only\)


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/systemMappings/<virtualHost>:<virtualPort>/blockedClientUsers` 

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
[{client, user}]

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

**Request**:

List of objects, each representing a blocked client and user:

-   `client`: ABAP client

-   `user`: ABAP user


Back to [Top](access-control-entities-2b8ee62.md#loio2b8ee62d19db43649365f82f78b185a0__top)



<a name="loio2b8ee62d19db43649365f82f78b185a0__extend_blocked"/>

## Add Blocked Client/User Pairs \(Master Only\)


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/systemMappings/<virtualHost>:<virtualPort>/blockedClientUsers` 

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
[{client, user}]
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

**Request**:

List of objects, each representing a blocked client and user:

-   `client`: ABAP client

-   `user`: ABAP user


Back to [Top](access-control-entities-2b8ee62.md#loio2b8ee62d19db43649365f82f78b185a0__top)



<a name="loio2b8ee62d19db43649365f82f78b185a0__delete_clients"/>

## Delete All Allowed Clients \(Master Only\)


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/systemMappings/<virtualHost>:<virtualPort>/allowedClients` 

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

Back to [Top](access-control-entities-2b8ee62.md#loio2b8ee62d19db43649365f82f78b185a0__top)



<a name="loio2b8ee62d19db43649365f82f78b185a0__delete_blocked"/>

## Delete All Blocked Client/User Pairs \(Master Only\)


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/systemMappings/<virtualHost>:<virtualPort>/blockedClientUsers` 

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

Back to [Top](access-control-entities-2b8ee62.md#loio2b8ee62d19db43649365f82f78b185a0__top)



<a name="loio2b8ee62d19db43649365f82f78b185a0__remove_allowed"/>

## Remove an Item from the List of Allowed Clients \(Master Only\)


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/systemMappings/<virtualHost>:<virtualPort>/allowedClients/<client>` 

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

Administrator, Subaccount Administrator 

</td>
</tr>
</table>

Back to [Top](access-control-entities-2b8ee62.md#loio2b8ee62d19db43649365f82f78b185a0__top)



<a name="loio2b8ee62d19db43649365f82f78b185a0__remove_pair"/>

## Remove an Item from the List of Blocked Client/User Pairs \(Master Only\)


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/systemMappings/<virtualHost>:<virtualPort>/blockedClientUsers/<client>:<user>` 

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

Back to [Top](access-control-entities-2b8ee62.md#loio2b8ee62d19db43649365f82f78b185a0__top)

