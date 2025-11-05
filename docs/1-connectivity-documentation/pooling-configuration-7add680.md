<!-- loio7add680d1a5a409fb71d397f5e7d10e1 -->

# Pooling Configuration

Configure pooling properties for RFC destinations in the SAP BTP cockpit.



<a name="loio7add680d1a5a409fb71d397f5e7d10e1__section_N1001A_N10011_N10001"/>

## Overview

This group of JCo properties covers different settings for the behavior of the destination's connection pool. All properties are optional.

In the *Destinations* editor in the cockpit, the configuration must be provided in the *Pooling Configuration* panel.


<table>
<tr>
<th valign="top">

Label in Destinations Editor

</th>
<th valign="top">

Property

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

Pool Capacity

</td>
<td valign="top">

`jco.destination.pool_capacity`

</td>
<td valign="top">

Represents the maximum number of idle connections kept open by the destination. A value of `0` has the effect of no connection pooling, that is, connections will be closed after each request. The default value is `1`.

</td>
</tr>
<tr>
<td valign="top">

Peak Limit

</td>
<td valign="top">

`jco.destination.peak_limit`

</td>
<td valign="top">

Represents the maximum number of active connections you can create for a destination simultaneously. Value `0` allows an unlimited number of active connections. Otherwise, if the value is less than the value of `jco.destination.pool_capacity`, it will be automatically increased to this value.

Default setting is the value of `jco.destination.pool_capacity`. If `jco.destination.pool_capacity` is not specified, the default is `0` \(unlimited\).

</td>
</tr>
<tr>
<td valign="top">

Maximum Get Client Time

</td>
<td valign="top">

`jco.destination.max_get_client_time`

</td>
<td valign="top">

Represents the maximum time in milliseconds to wait for a free connection in case the maximum number of active connections is already allocated by applications. The default value is 30000 \(30 seconds\).

</td>
</tr>
<tr>
<td valign="top">

Expiration Time

</td>
<td valign="top">

`jco.destination.expiration_time`

</td>
<td valign="top">

Represents the time in milliseconds after which idle connections that are available in the pool can be closed. The default value is 60000 \(60 seconds\).

</td>
</tr>
<tr>
<td valign="top">

Expiration Check Period

</td>
<td valign="top">

`jco.destination.expiration_check_period`

</td>
<td valign="top">

Represents the interval in milliseconds for the timeout checker thread to check the idle connections in the pool for expiration. The default value is 60000 \(60 seconds\).

</td>
</tr>
<tr>
<td valign="top">

Pool Check Connection

</td>
<td valign="top">

`jco.destination.pool_check_connection`

</td>
<td valign="top">

If the checkbox *Pool Check Connection* is checked or when setting the property in a file to be imported to `1`, a pooled connection will be checked for corruption before being used for the next function module execution. Thus, it is possible to recognize corrupted connections and avoid exceptions passed to applications when connectivity is working in principle \(default is that the checkbox is unchecked or the value is `0`\).

> ### Note:  
> Turning on this check has performance impact for stateless communication. This is due to an additional low-level ping to the server, which takes a certain amount of time for non-corrupted connections, depending on latency.



</td>
</tr>
</table>



<a name="loio7add680d1a5a409fb71d397f5e7d10e1__section_N100A0_N10011_N10001"/>

## Pooling Details

-   Each destination is associated with a connection factory and, if the pooling feature is used, with a connection pool.
-   Initially, the destination's connection pool is empty, and the JCo runtime does not preallocate any connection. The first connection will be created when the first function module invocation is performed. The `peak_limit` property describes how many connections can be created simultaneously, if applications allocate connections in different sessions at the same time. A connection is allocated either when a stateless function call is executed, or when a connection for a stateful call sequence is reserved within a session.
-   After the *<peak\_limit\>* number of connections has been allocated \(in *<peak\_limit\>* number of sessions\), the next session will wait for at most *<max\_get\_client\_time\>* milliseconds until a different session releases a connection \(either finishes a stateless call or ends a stateful call sequence\). In case the waiting session does not get any connection during the *<max\_get\_client\_time\>* period, the function request will be aborted with *JCoException* with the key `JCO_ERROR_RESOURCE`.
-   Connections that are no longer used by applications are returned to the destination pool. There is at most a *<pool\_capacity\>* number of connections kept open by the pool. Further connections \(*<peak\_limit\>* - *<pool\_capacity\>*\) will be closed immediately after usage. The pooled connections \(open connections in the pool\) are marked as expired if they are not used again during *<expiration\_time\>* milliseconds. All expired connections will be closed by a timeout checker thread which executes the check every *<expiration\_check\_period\>* milliseconds.

