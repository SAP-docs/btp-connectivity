<!-- loio03a3ab39cd544e37871b0bf75ad6ca5f -->

# Common On-Premises Connectivity Configuration

Read the Cloud Connector's common on-premises connectivity settings via API.



<a name="loio03a3ab39cd544e37871b0bf75ad6ca5f__section_rcp_l1b_vcb"/>

## Get Principal Propagation Configuration


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/onPremises/ppSettings` 

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
{expirationToleranceInHr, certificateValidityInMin}
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

**Response:**

-   `expirationToleranceInHr`: Integer - duration in hours a principal remains usable after the token has expired
-   `certificateValidityInMin`: Integer - duration in minutes a certificate for principal propagation can be used for backend authentication

> ### Sample Code:  
> **Sample Output**
> 
> ```
> {
>   "expirationToleranceInHr": 1,
>   "certificateValidityInMin": 60
> }
> ```

> ### Sample Code:  
> ```
> curl -i -k -H "Accept: application/json" -u <user>:<password> -X GET https://<host>:<port>/api/v1/configuration/connector/onPremises/ppSettings
> ```



## Set Principal Propagation Configuration


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/onPremises/ppSettings` 

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
{expirationToleranceInHr, certificateValidityInMin}
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

Administrator, Associate Administrator, Subaccount Administrator

</td>
</tr>
</table>

**Request**:

-   `expirationToleranceInHr`: Integer - duration in hours a principal remains usable after the token has expired
-   `certificateValidityInMin`: Integer - duration in minutes a certificate for principal propagation can be used for backend authentication

**Errors**:

-   `INVALID_REQUEST`:
    -   empty input
    -   values not set
    -   invalid values
    -   `expirationToleranceInHr` is not within the range 1-336 \(inclusive\) \(14 days\)
    -   `certificateValidityInMin` is not within the range 1-43200 \(inclusive\) \(30 days\)


> ### Sample Code:  
> **Sample Input**
> 
> ```
> {
>   "expirationToleranceInHr": 1,
>   "certificateValidityInMin": 60
> }
> ```

> ### Sample Code:  
> ```
> curl -i -k -H "Content-Type: application/json" -u <user>:<password> -X PUT https://<host>:<port>/api/v1/configuration/connector/onPremises/ppSettings -d "{\"expirationToleranceInHr\": 1, \"certificateValidityInMin\": 60}"
> ```



## Modify Principal Propagation Configuration


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/onPremises/ppSettings` 

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
{<values to be changed>}
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

Administrator, Associate Administrator, Subaccount Administrator

</td>
</tr>
</table>

**Request**:

One or several values of

-   `expirationToleranceInHr`: Integer - duration in hours a principal remains usable after the token has expired
-   `certificateValidityInMin`: Integer - duration in minutes a certificate for principal propagation can be used for backend authentication

**Errors**:

-   `INVALID_REQUEST`:
    -   empty input
    -   values not set
    -   invalid values
    -   `expirationToleranceInHr` is not within the range 1-336 \(inclusive\) \(14 days\)
    -   `certificateValidityInMin` is not within the range 1-43200 \(inclusive\) \(30 days\)


> ### Sample Code:  
> ```
> curl -i -k -H "Content-Type: application/json" -u <user>:<password> -X PATCH https://<host>:<port>/api/v1/configuration/connector/onPremises/ppSettings
> ```

