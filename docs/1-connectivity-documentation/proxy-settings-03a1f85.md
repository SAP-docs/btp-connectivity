<!-- loio03a1f85a40594b05871dfe20c5232c6b -->

# Proxy Settings

Read and edit the Cloud Connector's proxy settings via API.



<a name="loio03a1f85a40594b05871dfe20c5232c6b__section_rcp_l1b_vcb"/>

## Get Proxy Settings


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/proxy` 

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
{host, port, user}
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

-   `host`: the name of the proxy host \(a string\)
-   `port`: the port of the proxy host \(a string\)
-   `user`: the user name \(a string\)

> ### Sample Code:  
> ```
> curl -ik -u Administrator:<password> https://localhost:8443/api/v1/configuration/connector/proxy
> 
> ```



<a name="loio03a1f85a40594b05871dfe20c5232c6b__section_lys_l1b_vcb"/>

## Set Proxy Settings \(Master Only\)


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/proxy` 

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
{host, port, user, password}
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

`INVALID_REQUEST`, `FORBIDDEN_REQUEST` 

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

-   `host`: the name of the proxy host \(a string\)
-   `port`: the port of the proxy host \(a string\)
-   `user`: the user name \(a string\)
-   `password`: the password \(a string - optional\)

**Errors:**

-   `INVALID_REQUEST` \(400\): invalid values were supplied, or mandatory values are missing.
-   `FORBIDDEN_REQUEST` \(403\): the target of the call is a shadow instance.

The following example sets empty `user` and `password`.

> ### Sample Code:  
> ```
> curl -ik -u Administrator:<password> https://localhost:8443/api/v1/configuration/connector/proxy -X PUT -H 'Content-Type: application/json' -d '{"host":"proxy", "port":"8080"}'
> 
> ```

This request removes the proxy configuration.

> ### Sample Code:  
> ```
> curl -ik -u Administrator:<password> https://localhost:8443/api/v1/configuration/connector/proxy -X PUT -H 'Content-Type: application/json' -d '{}'
> 
> ```



<a name="loio03a1f85a40594b05871dfe20c5232c6b__section_jd2_nmy_c4b"/>

## Remove Proxy Settings \(Master Only\)


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/proxy` 

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

`FORBIDDEN_REQUEST` 

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

-   `FORBIDDEN_REQUEST` \(403\): the target of the call is a shadow instance.

> ### Sample Code:  
> ```
> curl -ik -u Administrator:<password> https://localhost:8443/api/v1/configuration/connector/proxy -X DELETE
> 
> 
> ```

