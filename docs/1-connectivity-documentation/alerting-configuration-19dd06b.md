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
{thresholds, notification}
 
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

-   `thresholds`: thresholds
    -   `cpuLoad`: CPU load in percent
    -   `cpuLoadViolationToleranceSec`: CPU load violation tolerance in seconds

    -   `freeDiskSpaceMb`: free disc space in MB

    -   `freeDiscForAuditLogMb`: \(optional, only if external AuditLog is configured\) free disc space on volume configured for external audit log

    -   `freeDiscForTraceMb`: \(optional, only if external Trace is configured\) free disc space on volume configured for external trace

    -   `certificateValidityDays`: End of validity period of certificates in days until expiration


-   `notification`: Alerts categories to be reported via configured e-mail
    -   `ha`: high availability: alerts related to HA communication and state management
    -   `tunnels`: alerts related to SAP BTP cloud connectivity
    -   `serviceChannels`: service channels
    -   `CPU`: alerts related to CPU load
    -   `freeDiskSpace`: alerts related to exhausted disk space
    -   `certificates`: alerts related to expiring certificates
    -   `troubleshooting`: alerts about new troubleshooting diagnose




## Example

```
curl -i -k -H 'Accept:application/json' -u <user>:<password> -X GET https://<host>:<port>/api/v1/configuration/connector/alerting
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
{thresholds, notification}

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

Administrator

</td>
</tr>
</table>

**Request Properties:**

-   `thresholds`: thresholds
    -   `cpuLoad`: CPU load in percent
    -   `cpuLoadViolationToleranceSec`: CPU load violation tolerance in seconds

    -   `freeDiskSpaceMb`: free disc space in MB

    -   `freeDiscForAuditLogMb`: \(optional, only if external AuditLog is configured\) free disc space on volume configured for external audit log

    -   `freeDiscForTraceMb`: \(optional, only if external Trace is configured\) free disc space on volume configured for external trace

    -   `certificateValidityDays`: End of validity period of certificates in days until expiration


-   `notification`: Alerts categories to be reported via configured e-mail
    -   `ha`: high availability: alerts related to HA communication and state management
    -   `tunnels`: alerts related to SAP BTP cloud connectivity
    -   `serviceChannels`: service channels
    -   `CPU`: alerts related to CPU load
    -   `freeDiskSpace`: alerts related to exhausted disk space
    -   `certificates`: alerts related to expiring certificates
    -   `troubleshooting`: alerts about new troubleshooting diagnose




## Example

```
curl -i -k -u <user>:<password> -H 'Content-Type:application/json' -d '{"notification":{<values>}, "thresholds":{<values>}}' 
-X PUT https://<host>:<port>/api/v1/configuration/connector/alerting
```



<a name="loio19dd06bd609141faa83b1fefd337159c__section_dj2_hdb_1dc"/>

## Modify Alerting Configuration


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

Administrator

</td>
</tr>
</table>

**Request Properties:**

One or several values of:

-   `thresholds`: thresholds
    -   `cpuLoad`: CPU load in percent
    -   `cpuLoadViolationToleranceSec`: CPU load violation tolerance in seconds

    -   `freeDiskSpaceMb`: free disc space in MB

    -   `freeDiscForAuditLogMb`: \(optional, only if external AuditLog is configured\) free disc space on volume configured for external audit log

    -   `freeDiscForTraceMb`: \(optional, only if external Trace is configured\) free disc space on volume configured for external trace

    -   `certificateValidityDays`: End of validity period of certificates in days until expiration


-   `notification`: Alerts categories to be reported via configured e-mail
    -   `ha`: high availability: alerts related to HA communication and state management
    -   `tunnels`: alerts related to SAP BTP cloud connectivity
    -   `serviceChannels`: service channels
    -   `CPU`: alerts related to CPU load
    -   `freeDiskSpace`: alerts related to exhausted disk space
    -   `certificates`: alerts related to expiring certificates
    -   `troubleshooting`: alerts about new troubleshooting diagnose




## Example

```
curl -i -k -u <user>:<password> -H 'Content-Type:application/json' -d '{"notification":{"cpuLoad":90}}' 
-X PATCH https://<host>:<port>/api/v1/configuration/connector/alerting
```

