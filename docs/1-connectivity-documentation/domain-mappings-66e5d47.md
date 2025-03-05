<!-- loio66e5d47520854c32903b6da4b9337d96 -->

# Domain Mappings

Manage the Cloud Connector's configuration for domain mappings via API.



<a name="loio66e5d47520854c32903b6da4b9337d96__section_rcp_l1b_vcb"/>

## Get Domain Mappings


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/domainMappings` 

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
[{virtualDomain, internalDomai}] 
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

**Response:**

An array of objects, each representing a domain mapping through the following properties:

-   `virtualDomain`: Domain used on the cloud side
-   `internalDomain`: Domain used on the on-premises side



<a name="loio66e5d47520854c32903b6da4b9337d96__section_lys_l1b_vcb"/>

## Create Domain Mapping \(Master Only\)


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/domainMappings` 

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
{virtualDomain, internalDomain}
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



<a name="loio66e5d47520854c32903b6da4b9337d96__section_msy_ktm_mpb"/>

## Replace Domain Mapping \(Master Only\)


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/domainMappings/<internalDomain>` 

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
{virtualDomain, internalDomain} 
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

**Request:**

-   `virtualDomain`: New virtual domain
-   `internalDomain`: New internal domain

**Errors:**

-   NOT\_FOUND \(404\): Domain mapping does not exist.

> ### Note:  
> The internal domain in the URI path \(i.e., <internalDomain\>\) is the current internal domain of the domain mapping that is to be edited. It may differ from the new internal domain set in the request.



<a name="loio66e5d47520854c32903b6da4b9337d96__section_ldr_52b_vcb"/>

## Delete Domain Mapping \(Master Only\)


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/domainMappings/<internalDomain>` 

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

**Errors:**

-   NOT\_FOUND \(404\): Domain mapping does not exist.



## Delete All Domain Mappings \(Master Only\)


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/subaccounts/<regionHost>/<subaccount>/domainMappings` 

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

