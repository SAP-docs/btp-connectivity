<!-- loio99df2b95fb5245c7921673ad8fc2a542 -->

# System Mapping Resources

Manage the Cloud Connector's system mapping resources via API.

> ### Note:  
> Access to *managed* subaccounts is reserved for the role *Administrator* for all methods except for method GET.
> 
> For more information on managed subaccounts, see [Adding a Subaccount](adding-and-managing-subaccounts-f16df12.md#loiof16df12fab9f4fe1b8a4122f0fd54b6e__add) \(step 2\).



<a name="loio99df2b95fb5245c7921673ad8fc2a542__section_twx_kxj_jrb"/>

## Operations


<table>
<tr>
<td valign="top">

**System Mapping Resources**

</td>
<td valign="top">

[Get all System Mapping Resources](system-mapping-resources-99df2b9.md#loio99df2b95fb5245c7921673ad8fc2a542__get_all_resources)

[Get System Mapping Resource](system-mapping-resources-99df2b9.md#loio99df2b95fb5245c7921673ad8fc2a542__get_resource)

[Create System Mapping Resource](system-mapping-resources-99df2b9.md#loio99df2b95fb5245c7921673ad8fc2a542__create_resource)

[Replace System Mapping Resource](system-mapping-resources-99df2b9.md#loio99df2b95fb5245c7921673ad8fc2a542__edit_resource)

[Delete System Mapping Resource](system-mapping-resources-99df2b9.md#loio99df2b95fb5245c7921673ad8fc2a542__delete_resource)

[Delete all System Mapping Resources](system-mapping-resources-99df2b9.md#loio99df2b95fb5245c7921673ad8fc2a542__delete_all_resources)

</td>
</tr>
<tr>
<td valign="top">

**Allowed Clients**

</td>
<td valign="top">

[Get Allowed Clients for RFC System Mapping](system-mapping-resources-99df2b9.md#loio99df2b95fb5245c7921673ad8fc2a542__get_clients)

[Set Allowed Clients for RFC System Mapping](system-mapping-resources-99df2b9.md#loio99df2b95fb5245c7921673ad8fc2a542__set_clients)

[Add Allowed Clients for RFC System Mapping](system-mapping-resources-99df2b9.md#loio99df2b95fb5245c7921673ad8fc2a542__add_clients)

[Delete an Allowed Client for RFC System Mapping](system-mapping-resources-99df2b9.md#loio99df2b95fb5245c7921673ad8fc2a542__delete_client)

[Delete all Allowed Clients for RFC System Mapping](system-mapping-resources-99df2b9.md#loio99df2b95fb5245c7921673ad8fc2a542__delete_all_clients)

</td>
</tr>
<tr>
<td valign="top">

**Blocked Users**

</td>
<td valign="top">

[Get Blocked Users for RFC System Mapping](system-mapping-resources-99df2b9.md#loio99df2b95fb5245c7921673ad8fc2a542__get_blocked_users)

[Set Blocked Users for RFC System Mapping](system-mapping-resources-99df2b9.md#loio99df2b95fb5245c7921673ad8fc2a542__set_blocked_users)

[Add Blocked Users for RFC System Mapping](system-mapping-resources-99df2b9.md#loio99df2b95fb5245c7921673ad8fc2a542__add_blocked_users)

[Remove one Blocked User for RFC System Mapping](system-mapping-resources-99df2b9.md#loio99df2b95fb5245c7921673ad8fc2a542__remove_user)

[Remove all Blocked Users for RFC System Mapping](system-mapping-resources-99df2b9.md#loio99df2b95fb5245c7921673ad8fc2a542__remove_all_users)

</td>
</tr>
</table>



<a name="loio99df2b95fb5245c7921673ad8fc2a542__get_all_resources"/>

## Get all System Mapping Resources


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/systemMappings/<virtualHost>:<virtualPort>/resources` 

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
[{id, enabled, exactMatchOnly, websocketUpgradeAllowed, description}]

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

An array of objects, each representing a resource through the following properties:

-   `id`: The resource itself, which, depending on the owning system mapping, is either a URL path \(or the leading section of it\), or a RFC function name \(prefix\)
-   `enabled`: Boolean flag indicating whether the resource is enabled.
-   `exactMatchOnly`: Boolean flag determining whether access is granted only if the requested resource is an exact match.
-   `websocketUpgradeAllowed`: Boolean flag indicating whether websocket upgrade is allowed; this property is of relevance only if the owning system mapping employs protocol HTTP or HTTPS.
-   `description`: Description \(a string\); this property is not available unless explicitly set.

Back to [Top](system-mapping-resources-99df2b9.md#loio99df2b95fb5245c7921673ad8fc2a542__top)



<a name="loio99df2b95fb5245c7921673ad8fc2a542__get_resource"/>

## Get System Mapping Resource


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/systemMappings/<virtualHost>:<virtualPort>/resources/<encodedResourceId>` 

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
{id, enabled, exactMatchOnly, websocketUpgradeAllowed, description} 
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

**Response Properties**:

-   `id`: The resource itself, which, depending on the owning system mapping, is either a URL path \(or the leading section of it\), or a RFC function name \(prefix\)
-   `enabled`: Boolean flag indicating whether the resource is enabled.
-   `exactMatchOnly`: Boolean flag determining whether access is granted only if the requested resource is an exact match.
-   `websocketUpgradeAllowed`: Boolean flag indicating whether websocket upgrade is allowed; this property is of relevance only if the owning system mapping employs protocol HTTP or HTTPS.
-   `description`: Description \(a string\); this property is not available unless explicitly set.

Back to [Top](system-mapping-resources-99df2b9.md#loio99df2b95fb5245c7921673ad8fc2a542__top)



<a name="loio99df2b95fb5245c7921673ad8fc2a542__create_resource"/>

## Create System Mapping Resource \(Master Only\)


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/systemMappings/<virtualHost>:<virtualPort>/resources` 

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
{id, enabled, exactMatchOnly, websocketUpgradeAllowed, description}

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

-   `id`: The resource itself, which, depending on the owning system mapping, is either a URL path \(or the leading section of it\), or a RFC function name \(prefix\).
-   `enabled`: Boolean flag indicating whether the resource is enabled \(**optional**\). The default value is `false`.
-   `exactMatchOnly`: Boolean flag determining whether access is granted only if the requested resource is an exact match \(**optional**\). The default value is `false`.
-   `websocketUpgradeAllowed`: Boolean flag indicating whether websocket upgrade is allowed \(**optional**\). The default value is `false`. This property is recognized only if the owning system mapping employs protocol HTTP or HTTPS.
-   `description`: Description \(a string, **optional**\)

> ### Tip:  
> **Encoded Resource ID**
> 
> URI paths may contain the resource ID in order to identify the resource to be edited or deleted. A resource ID, however, may contain characters such as the forward slash that collide with the path separator of the URI and hence require an escape mechanism. We adopted the following simple escape or encoding method for a resource ID:
> 
> 1.  Replace all occurrences of character '+' with '+2B'.
> 2.  Replace all occurrences of character '-' with '+2D'.
> 3.  Replace all occurrences of character '/' with '-'.

Back to [Top](system-mapping-resources-99df2b9.md#loio99df2b95fb5245c7921673ad8fc2a542__top)



<a name="loio99df2b95fb5245c7921673ad8fc2a542__edit_resource"/>

## Replace System Mapping Resource \(Master Only\)


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/systemMappings/<virtualHost>:<virtualPort>/resources/<encodedResourceId>` 

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
{enabled, exactMatchOnly, websocketUpgradeAllowed, description}  
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

**Request Properties**:

-   `enabled`: Boolean flag indicating whether the resource is enabled.
-   `exactMatchOnly`: Boolean flag determining whether access is granted only if the requested resource is an exact match.
-   `websocketUpgradeAllowed`: Boolean flag indicating whether websocket upgrade is allowed; this property is of relevance only if the owning system mapping employs protocol HTTP or HTTPS.
-   `description`: Description \(a string\); this property is not available unless explicitly set.

Back to [Top](system-mapping-resources-99df2b9.md#loio99df2b95fb5245c7921673ad8fc2a542__top)



<a name="loio99df2b95fb5245c7921673ad8fc2a542__delete_resource"/>

## Delete System Mapping Resource \(Master Only\)


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/systemMappings/<virtualHost>:<virtualPort>/resources/<encodedResourceId>` 

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

`NOT_FOUND` 

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

`NOT_FOUND (404)`: Resource was not found

Back to [Top](system-mapping-resources-99df2b9.md#loio99df2b95fb5245c7921673ad8fc2a542__top)



<a name="loio99df2b95fb5245c7921673ad8fc2a542__delete_all_resources"/>

## Delete all System Mapping Resources \(Master Only\)


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<region>/<subaccount>/systemMappings/<virtualHost>:<virtualPort>/resources` 

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

Back to [Top](system-mapping-resources-99df2b9.md#loio99df2b95fb5245c7921673ad8fc2a542__top)



<a name="loio99df2b95fb5245c7921673ad8fc2a542__get_clients"/>

## Get Allowed Clients for RFC System Mapping

> ### Note:  
> Available as of version 2.14.

Returns the list of allowed ABAP clients for the system mapping definition.


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<region>/<subaccount>/systemMappings/<virtualHost>:<virtualPort>/allowedClients` 

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
[client, ...]

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

**Response Properties**:

-   Array of allowed clients:

    -   `client`: ABAP client


> ### Note:  
> An empty list means that every client is allowed.

Back to [Top](system-mapping-resources-99df2b9.md#loio99df2b95fb5245c7921673ad8fc2a542__top)



<a name="loio99df2b95fb5245c7921673ad8fc2a542__set_clients"/>

## Set Allowed Clients for RFC System Mapping

> ### Note:  
> Available as of version 2.14.


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<region>/<subaccount>/systemMappings/<virtualHost>:<virtualPort>/allowedClients` 

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
[client, ...]

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

Administrator, Associate Administrator, Subaccount Administrator

</td>
</tr>
</table>

**Request Properties**:

-   Array of allowed clients:

    -   `client`: ABAP client


The existing list of available clients will be cleaned and populated by the provided in request.

Back to [Top](system-mapping-resources-99df2b9.md#loio99df2b95fb5245c7921673ad8fc2a542__top)



<a name="loio99df2b95fb5245c7921673ad8fc2a542__add_clients"/>

## Add Allowed Clients for RFC System Mapping

> ### Note:  
> Available as of version 2.14.

Adds more ABAP clients to the allowed list for the system mapping definition.


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<region>/<subaccount>/systemMappings/<virtualHost>:<virtualPort>/allowedClients` 

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
[client, ...]

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

Administrator, Associate Administrator, Subaccount Administrator

</td>
</tr>
</table>

**Request Properties**:

-   Array of allowed clients:

    -   `client`: ABAP client


Clients provided in this request will be added to the existing list. Clients that are already listed will be ignored.

Back to [Top](system-mapping-resources-99df2b9.md#loio99df2b95fb5245c7921673ad8fc2a542__top)



<a name="loio99df2b95fb5245c7921673ad8fc2a542__delete_client"/>

## Delete an Allowed Client for RFC System Mapping

> ### Note:  
> Available as of version 2.14.


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<region>/<subaccount>/systemMappings/<virtualHost>:<virtualPort>/allowedClients/<client>` 

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

Back to [Top](system-mapping-resources-99df2b9.md#loio99df2b95fb5245c7921673ad8fc2a542__top)



<a name="loio99df2b95fb5245c7921673ad8fc2a542__delete_all_clients"/>

## Delete all Allowed Clients for RFC System Mapping

> ### Note:  
> Available as of version 2.14.


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<region>/<subaccount>/systemMappings/<virtualHost>:<virtualPort>/allowedClients` 

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

> ### Note:  
> An empty list means that every client is allowed.

Back to [Top](system-mapping-resources-99df2b9.md#loio99df2b95fb5245c7921673ad8fc2a542__top)



<a name="loio99df2b95fb5245c7921673ad8fc2a542__get_blocked_users"/>

## Get Blocked Users for RFC System Mapping

> ### Note:  
> Available as of version 2.14.

Returns the list of blocked ABAP users for the system mapping definition.


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<region>/<subaccount>/systemMappings/<virtualHost>:<virtualPort>/blockedClientUsers` 

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
[{client, user}, ...]

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

**Response Properties**:

-   Array of blocked users:

    -   `client`: ABAP client
    -   `user`: User name


Back to [Top](system-mapping-resources-99df2b9.md#loio99df2b95fb5245c7921673ad8fc2a542__top)



<a name="loio99df2b95fb5245c7921673ad8fc2a542__set_blocked_users"/>

## Set Blocked Users for RFC System Mapping

> ### Note:  
> Available as of version 2.14.

Sets or replaces the list of blocked ABAP users for the system mapping definition.


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<region>/<subaccount>/systemMappings/<virtualHost>:<virtualPort>/blockedClientUsers` 

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
[{client, user}, ...]

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

Administrator, Associate Administrator, Subaccount Administrator

</td>
</tr>
</table>

**Request Properties**:

-   Array of blocked users:

    -   `client`: ABAP client
    -   `user`: User name


Back to [Top](system-mapping-resources-99df2b9.md#loio99df2b95fb5245c7921673ad8fc2a542__top)



<a name="loio99df2b95fb5245c7921673ad8fc2a542__add_blocked_users"/>

## Add Blocked Users for RFC System Mapping

> ### Note:  
> Available as of version 2.14.

Adds the provided list of blocked ABAP users to the current list.


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<region>/<subaccount>/systemMappings/<virtualHost>:<virtualPort>/blockedClientUsers` 

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
[{client, user}, ...]

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

Administrator, Associate Administrator, Subaccount Administrator

</td>
</tr>
</table>

**Request Properties**:

-   Array of blocked users:

    -   `client`: ABAP client
    -   `user`: User name


Back to [Top](system-mapping-resources-99df2b9.md#loio99df2b95fb5245c7921673ad8fc2a542__top)



<a name="loio99df2b95fb5245c7921673ad8fc2a542__remove_user"/>

## Remove one Blocked User for RFC System Mapping

> ### Note:  
> Available as of version 2.14.

Removes one user from the list of blocked ABAP users for the system mapping definition.


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<region>/<subaccount>/systemMappings/<virtualHost>:<virtualPort>/blockedClientUsers/<client>:<user>` 

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

Back to [Top](system-mapping-resources-99df2b9.md#loio99df2b95fb5245c7921673ad8fc2a542__top)



<a name="loio99df2b95fb5245c7921673ad8fc2a542__remove_all_users"/>

## Remove all Blocked Users for RFC System Mapping

> ### Note:  
> Available as of version 2.14.

Removes the list of blocked ABAP users for the system mapping definition.


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<region>/<subaccount>/systemMappings/<virtualHost>:<virtualPort>/blockedClientUsers` 

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

Back to [Top](system-mapping-resources-99df2b9.md#loio99df2b95fb5245c7921673ad8fc2a542__top)

