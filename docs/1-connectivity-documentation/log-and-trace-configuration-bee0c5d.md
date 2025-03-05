<!-- loiobee0c5d8f2714665ab56cecd13acf740 -->

# Log and Trace Configuration

Read and edit the Cloud Connector's log and trace settings via API.

The Cloud Connector provides subaccount-independent logs, also known as *cross-account settings*, and log settings related to subaccounts.

The location of API for cross-account settings is `/api/v1/configuration/connector/logAndTrace`. Subaccount-related settings can be done here: `/api/v1/configuration/connector/logAndTrace/subaccounts/<regionHost>/<subaccount>`.

Configuration changes are applied to the corresponding locations. The API method is PATCH, allowing you to set only relevant values. PUT and DELETE methods are not implemented.

-   `Cloud Connector Loggers` are logged with output to `scc_core.trc`.
-   `other Loggers` are logged with output to `scc_core.trc`.



<a name="loiobee0c5d8f2714665ab56cecd13acf740__section_m1b_3tz_5cc"/>

## Get Cross-Account Configuration


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/logAndTrace` 

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
{sccLogLevel, otherLogLevel, tlsTrace, cpicTraceLevel, cleanup, rolloverThreshold, logAndTracePath}

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

**Response Properties:**

-   `sccLogLevel`: log level for Cloud Connector log locations, one of OFF, ERROR, WARN, INFO, DEBUG, TRACE, ALL.

-   `otherLogLevel`: log level for all other than Cloud Connector log locations, one of OFF, ERROR, WARN, INFO, DEBUG, TRACE, ALL.

-   `isSslTraceActive`: SSL Trace currently active in runtime. If differs to sslTrace, a restart is required.

-   `sslTrace`: SSL Trace stored in configuration. \(true or false\). A restart is required to activate the setting.

-   `cpicTraceLevel`: trace level of CPIC layer \(0 - off, 1 - general information, 2 - detailed trace, 3 - verbose level\)

-   `cleanup`: number of days to keep the log files \(0 means do not clean up the old log files\)

-   `rolloverThreshold`: size in megabytes for the scc\_core.trc files. 20 files will be kept before the oldest is overwritten.

-   `logAndTracePath`: path for log and trace files


> ### Note:  
> `otherLogLevel` should only be changed if requested by SAP support.



<a name="loiobee0c5d8f2714665ab56cecd13acf740__section_a4t_htz_5cc"/>

## Change Cross-Account Configuration


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/logAndTrace` 

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
{sccLogLevel , otherLogLevel, tlsTrace, cpicTraceLevel, cleanup, rolloverThreshold }

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

-   `sccLogLevel`: log level for Cloud Connector log locations, one of OFF, ERROR, WARN, INFO, DEBUG, TRACE, ALL.
-   `otherLogLevel`: log level for all other than Cloud Connector log locations, one of OFF, ERROR, WARN, INFO, DEBUG, TRACE, ALL.
-   `sslTrace`: SSL Trace stored in configuration. \(true or false\). A restart may require to activate the setting.
-   `cpicTraceLevel`: trace level of CPIC layer \(0 - off, 1 - general information, 2 - detailed trace, 3 - verbose level\)
-   `cleanup`: number of days to keep the log files \(0 means do not clean up the old log files\)
-   `rolloverThreshold`: size in megabytes for the scc\_core.trc files. The unit MB must be included, i.e. a valid value is '75 MB' \(with or without space\), for instance. 20 files will be kept before the oldest gets overwritten.

> ### Note:  
> The request may contain only the properties to be changed. All other settings keep their values.



<a name="loiobee0c5d8f2714665ab56cecd13acf740__section_ywk_htz_5cc"/>

## Get Subaccount-Related Configuration


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/logAndTrace/subaccounts/<regionHost>/<subaccount>` 

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
{trafficTrace, payloadSncTrace}        

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

**Response Properties:**

-   `trafficTrace`: the traffic \(payload\) trace for the specified subaccount \(true or false\).
-   `payloadSncTrace`: the SNC payload for the specified subaccount for Cloud ABAP communication \(true or false\).



<a name="loiobee0c5d8f2714665ab56cecd13acf740__section_rcp_l1b_vcb"/>

## Change Subaccount-Related Configuration


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/logAndTrace/subaccounts/<regionHost>/<subaccount>` 

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



</td>
</tr>
<tr>
<td valign="top">

Response

</td>
<td valign="top">

```
{trafficTrace, payloadSncTrace}

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

Administrator, Subaccount Administrator, Support

</td>
</tr>
</table>

**Request Properties:**

-   `trafficTrace`: activates or deactivates the traffic \(payload\) trace for the specified subaccount \(true or false\).

-   `payloadSncTrace`: activates or deactivates the snc payload for the specified subaccount for Cloud ABAP communication \(true or false\).


