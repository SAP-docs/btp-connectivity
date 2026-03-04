<!-- loio8aed644c6bce4bcabfd31d1c74e8fec4 -->

# Common Properties

Read and edit the Cloud Connector's common properties via API.



<a name="loio8aed644c6bce4bcabfd31d1c74e8fec4__section_rcp_l1b_vcb"/>

## Get Common Properties


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector`

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
{ha, description}
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

-   **Response Properties**:
    -   `ha`: Cloud Connector instance assigned to a high-availability role. Its value is either the string *master* or *shadow*.

    -   `description`: Description of the Cloud Connector.





<a name="loio8aed644c6bce4bcabfd31d1c74e8fec4__section_tp5_hhk_vpb"/>

## Get Version

> ### Note:  
> Available as of version 2.14.0.


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/connector/version` 

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
{version}
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

-   **Response Properties**:

    `version`: A string; the Cloud Connector version.




<a name="loio8aed644c6bce4bcabfd31d1c74e8fec4__section_lys_l1b_vcb"/>

## Set Description \(Master Only\)


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector` 

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
{description}
```



</td>
</tr>
<tr>
<td valign="top">

Response

</td>
<td valign="top">

```
{ha, description}

```



</td>
</tr>
<tr>
<td valign="top">

Errors

</td>
<td valign="top">

`INVALID_REQUEST` 

</td>
</tr>
<tr>
<td valign="top">

Roles

</td>
<td valign="top">

Administrator, Associate Administrator

</td>
</tr>
</table>

-   **Request Properties**:

    `description`: A string; use an empty string to remove the description.


-   **Response Properties**:
    -   `ha`: Cloud Connector instance assigned to a high-availability role. Its value is either the string *master* or *shadow*.

    -   `description`: Description of the Cloud Connector.


-   **Errors**:

    `INVALID_REQUEST` \(\(400\): The value of `description` is not a JSON string.

    > ### Note:  
    > `null` is not a JSON string.




## Get Available Cipher Suites


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/availableCipherSuites` 

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
[cipherSuite, ...]

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

Administrator, Subaccount Administrator, Display, Support, Monitoring

</td>
</tr>
</table>

-   **Response**:
    -   list of:

        -   `cipherSuite`: cipher suite name like TLS\_AES\_128\_GCM\_SHA256 \(a string\)




