<!-- loio024ab69a759844d0866e7d605a0a2598 -->

# Solution Management Configuration

Manage the Cloud Connector's solution management configuration via API.



<a name="loio024ab69a759844d0866e7d605a0a2598__section_rcp_l1b_vcb"/>

## Get Solution Management Configuration


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/solutionManagement` 

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
{hostAgentPath, isEnabled, dsrEnabled}
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

-   `isEnabled`: flag indicating if reporting to solution management is active.
-   `hostAgentPath`: path for host agent executable.
-   `dsrEnabled`: indicating if DSR reporting is active.



<a name="loio024ab69a759844d0866e7d605a0a2598__section_ubs_zvh_snb"/>

## Example

```
curl -ik -u <user>:<password>  https://<host>:<port>/api/v1/configuration/connector/solutionManagement
```



<a name="loio024ab69a759844d0866e7d605a0a2598__section_lys_l1b_vcb"/>

## Activate Solution Management Reporting

This API turns on the integration with the Solution Manager. The prerequisite is an available Host Agent. You can specify a path to the Host Agent executable, if you don't use the default path.


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/solutionManagement` 

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
{hostAgentPath, dsrEnabled}
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

INVALID\_CONFIGURATION, RUNTIME\_FAILURE

</td>
</tr>
<tr>
<td valign="top">

Roles

</td>
<td valign="top">

Administrator, Support

</td>
</tr>
</table>

**Response Properties**:

-   `hostAgentPath`: path for host agent executable \(string, optional\).
-   `dsrEnabled`: flag indicating if DSR reporting is active \(boolean, optional\)

**Errors**:

-   `INVALID_CONFIGURATION` \(409\): host agent executable is not a file or does not exist.
-   `RUNTIME_FAILURE` \(500\): failure when executing the host agent executable.



## Example

```
curl -ik -u <user>:<password>  https://<host>:<port>/api/v1/configuration/connector/solutionManagement -X POST
```

or, if configuration has to be changed:

```
curl -ik -u <user>:<password>  https://<host>:<port>/api/v1/configuration/connector/solutionManagement -X POST -d "{\"hostAgentPath\":\"new/path/to/hostAgent\"}" -H "Content-Type:application/json"

```



<a name="loio024ab69a759844d0866e7d605a0a2598__section_j4c_12b_vcb"/>

## Deactivate Solution Management Reporting


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/solutionManagement` 

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

Administrator, Support

</td>
</tr>
</table>



## Example

```
curl -ik -u <user>:<password>  https://<host>:<port>/api/v1/configuration/connector/solutionManagement -X DELETE

```



## Get Registration File

Generates a zip file containing the registration file for the solution management LMDB \(Landscape Management Database\).

> ### Note:  
> Available as of Cloud Connector version 2.12.0.


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/solutionManagement/registrationFile` 

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

Administrator, Support

</td>
</tr>
</table>

