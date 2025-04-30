<!-- loio255f562a1658470eae270b91223083c2 -->

# Audit Logging

Use audit logging for the Connectivity Proxy for Kubernetes.

At runtime, the Connectivity Proxy produces audit messages for the relevant auditable events. These audit messages help you gather audit data which can be useful for identifying possible attacks or unwanted access attempts. The audit messages are written on the standard output and it is up to the operator of the Connectivity Proxy to configure the surrounding infrastructure in a way that these audit messages are collected, stored, protected from tampering, rotated when necessary, and so on.

> ### Note:  
> When written to the standard system output, the audit log messages are preceded by the prefix `[AUDIT-EVENT]` to distinguish them from the other logs.



<a name="loio255f562a1658470eae270b91223083c2__section_rnx_3qq_1qb"/>

## Audit Messages

In the table below, the left column shows a description of the security event, the right column shows the corresponding audit message. These messages are written on behalf of the consumer tenant.

> ### Note:  
> The *<message\>* field of the audit message should be treated as case insensitive.


<table>
<tr>
<th valign="top">

Operation

</th>
<th valign="top">

Audit Message

</th>
</tr>
<tr>
<td valign="top">

`[Security Event]`

**Successfully opened tunnel** 

from Cloud Connector to Connectivity Proxy.

</td>
<td valign="top">

```
{"user":"YYY","data":"{"action":"open connectivity tunnel","message":"tunnel handshake success","tunnelId":"NNN","objectName":"connectivity tunnel management","clientId":"FFF","loggedByClass":"com.sap.core.connectivity.tunnel.server.TunnelServerHandshaker","handshakeDetails":"success"}","tenant":"TTT"}

```



</td>
</tr>
<tr>
<td valign="top">

`[Security Event]`

**Failed attempt to open tunnel** 

from Cloud Connector to Connectivity Proxy.

</td>
<td valign="top">

```
{"user":"YYY","data":"{"action":"open connectivity tunnel","message":"tunnel handshake failure","tunnelId":"NNN","objectName":"connectivity tunnel management","clientId":"FFF","loggedByClass":"com.sap.core.connectivity.tunnel.server.TunnelServerHandshaker","handshakeDetails":"UUU"}","tenant":"TTT"}

```



</td>
</tr>
</table>

In the table above, there are multiple keys with UPPER CASE values. At runtime, these keys hold real scenario values:

-   YYY: User executing the operation, if known. If the request is not done on behalf of a user, the value will be `fallback_for_missing_user`.
-   NNN: Secure tunnel between the Connectivity Proxy and the Cloud Connector.
-   TTT: Tenant on whose behalf the operation is executed.
-   FFF: Remote client \(unique identifier of a particular installation\) of the Cloud Connector.
-   UUU: Additional information about the event.

