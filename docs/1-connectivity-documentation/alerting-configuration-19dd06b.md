<!-- loio19dd06bd609141faa83b1fefd337159c -->

# Alerting Configuration

Read and edit the Cloud Connector's alerting settings via API.



<a name="loio19dd06bd609141faa83b1fefd337159c__section_rcp_l1b_vcb"/>

## Get Alerting Configuration


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/alerting` 

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
{thresholds, emailNotification, checkInterval}
 
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

Administrator, Subaccount Administrator, Support, Display

</td>
</tr>
</table>

**Response Properties:**

-   `thresholds`: thresholds
    -   `cpuLoad`: CPU load in percent
    -   `cpuLoadViolationTolerance`: CPU load violation tolerance in seconds
    -   `freeDiskSpace`: free disc space in Mb
    -   `certificateValidity`: End of validity period of certificates in days until expiration

-   `emailNotification`: Alerts categories to be reported via configured e-mail
    -   `ha`: high availability: alerts related to HA communication and state management
    -   `tunnels`: alerts related to BTP cloud connectivity
    -   `serviceChannels`: service channels
    -   `CPU`: alerts related to CPU load
    -   `freeDiskSpace`: alerts related to exhausted disk space
    -   `certificates`: alerts related to expiring certificates

-   `checkInterval`: operability check interval in seconds



## Example

```
curl -i -k -H 'Accept:application/json' 
-u <user>:<password> -X GET https://<scchost>:8443/api/v1/configuration/connector/alerts
```



<a name="loio19dd06bd609141faa83b1fefd337159c__section_s2y_gdb_1dc"/>

## Set Alerting Configuration


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/alerting` 

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
{thresholds, emailNotification, checkInterval}

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

Administrator, Subaccount Administrator, Support

</td>
</tr>
</table>

**Request Properties:**

-   `thresholds`: thresholds
    -   `cpuLoad`: CPU load in percent
    -   `cpuLoadViolationTolerance`: CPU load violation tolerance in seconds
    -   `freeDiskSpace`: free disc space in Mb
    -   `certificateValidity`: End of validity period of certificates in days until expiration

-   `emailNotification`: Alerts categories to be reported via configured e-mail
    -   `ha`: high availability: alerts related to HA communication and state management
    -   `tunnels`: alerts related to BTP cloud connectivity
    -   `serviceChannels`: service channels
    -   `CPU`: alerts related to CPU load
    -   `freeDiskSpace`: alerts related to exhausted disk space
    -   `certificates`: alerts related to expiring certificates

-   `checkInterval`: operability check interval in seconds



## Example

```
curl -i -k -u <user>:<password> -H 'Content-Type:application/json' -d '{"thresholds":{}, "emailNotification":{}, "checkInterval":30}' 
-X PUT https://<scchost>:8443/api/v1/configuration/connector/alerts
```



<a name="loio19dd06bd609141faa83b1fefd337159c__section_dj2_hdb_1dc"/>

## Change Provided Values in Alerting Configuration


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/alerting` 

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

Administrator, Subaccount Administrator, Support, Display

</td>
</tr>
</table>

**Request Properties:**

One or multiple values of:

-   `thresholds`: thresholds
    -   `cpuLoad`: CPU load in percent
    -   `cpuLoadViolationTolerance`: CPU load violation tolerance in seconds
    -   `freeDiskSpace`: free disc space in Mb
    -   `certificateValidity`: End of validity period of certificates in days until expiration

-   `emailNotification`: Alerts categories to be reported via configured e-mail
    -   `ha`: high availability: alerts related to HA communication and state management
    -   `tunnels`: alerts related to BTP cloud connectivity
    -   `serviceChannels`: service channels
    -   `CPU`: alerts related to CPU load
    -   `freeDiskSpace`: alerts related to exhausted disk space
    -   `certificates`: alerts related to expiring certificates

-   `checkInterval`: operability check interval in seconds



## Example

```
curl -i -k -u <user>:<password> -H 'Content-Type:application/json' -d '{"checkInterval":30}' 
-X PATCH https://<scchost>:8443/api/v1/configuration/connector/alerts
```

