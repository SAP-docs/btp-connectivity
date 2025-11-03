<!-- loioab6eac92978f469e9eabe3d477ca2411 -->

# Target System Configuration

Learn about the JCo properties you can use to configure the target sytem information in an RFC destination.

> ### Note:  
> This documentation refers to SAP BTP, multi-cloud foundation. If you are looking for information about the Neo environment, see [Target System Configuration](https://help.sap.com/viewer/b865ed651e414196b39f8922db2122c7/Cloud/en-US/f8fac995b0144a0b8ec0801b8f7bab3e.html "Learn about the JCo properties you can use to configure the target sytem information in an RFC destination (Neo environment).") :arrow_upper_right: \(Neo environment\).



<a name="loioab6eac92978f469e9eabe3d477ca2411__content"/>

## Content

[Overview](target-system-configuration-ab6eac9.md#loioab6eac92978f469e9eabe3d477ca2411__overview)

[Proxy Types](target-system-configuration-ab6eac9.md#loioab6eac92978f469e9eabe3d477ca2411__proxy)

[Direct Connection](target-system-configuration-ab6eac9.md#loioab6eac92978f469e9eabe3d477ca2411__direct)

[Load Balancing Connection](target-system-configuration-ab6eac9.md#loioab6eac92978f469e9eabe3d477ca2411__load)

[WebSocket Connection](target-system-configuration-ab6eac9.md#loioab6eac92978f469e9eabe3d477ca2411__web)



<a name="loioab6eac92978f469e9eabe3d477ca2411__overview"/>

## Overview

You can use the following configuration types alternatively:

-   Direct connection to an ABAP application server
-   Load balancing connection to a group of ABAP application servers via a message server
-   WebSocket connection to an ABAP application server \(RFC over Internet\)

    > ### Note:  
    > When using a WebSocket connection, the target ABAP system must be exposed to the Internet.


Depending on the configuration you use, different properties are mandatory or optional.

To improve performance, consider using optional properties additionally, such as `jco.client.serialization_format`. For more information, see [JCo documentation](https://support.sap.com/en/product/connectors/jco.html).

Back to [Content](target-system-configuration-ab6eac9.md#loioab6eac92978f469e9eabe3d477ca2411__content)



<a name="loioab6eac92978f469e9eabe3d477ca2411__proxy"/>

## Proxy Types

The field *<Proxy Type\>* lets you choose between `Internet` and `OnPremise`. When choosing `OnPremise`, the RFC communication is routed over a Cloud Connector that is connected to the subaccount. When choosing `Internet`, the RFC communciation is done over a WebSocket connection.

Back to [Content](target-system-configuration-ab6eac9.md#loioab6eac92978f469e9eabe3d477ca2411__content)



<a name="loioab6eac92978f469e9eabe3d477ca2411__direct"/>

## Direct Connection

To use a direct connection \(connection without load balancing\) to an application server over Cloud Connector, you must set the value for *<Proxy Type\>* to `OnPremise`.


<table>
<tr>
<th valign="top">

Property

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`jco.client.ashost`

</td>
<td valign="top">

Represents the application server host to be used. For configurations on SAP BTP, the property must match a virtual host entry in the Cloud Connector *Access Control* configuration. The property indicates that a direct connection is established.

</td>
</tr>
<tr>
<td valign="top">

`jco.client.sysnr`

</td>
<td valign="top">

Represents the so-called "system number" and has two digits. It identifies the logical port on which the application server is listening for incoming requests. For configurations on SAP BTP, the property must match a virtual port entry in the Cloud Connector *Access Control* configuration.

> ### Note:  
> The virtual port in the above access control entry must be named `sapgw<##>`, where *<\#\#\>* is the value of `sysnr`.



</td>
</tr>
<tr>
<td valign="top">

`jco.client.client`

</td>
<td valign="top">

Represents the client to be used in the ABAP system. Valid format is a 3-digit number.

</td>
</tr>
</table>

Back to [Content](target-system-configuration-ab6eac9.md#loioab6eac92978f469e9eabe3d477ca2411__content)



<a name="loioab6eac92978f469e9eabe3d477ca2411__load"/>

## Load Balancing Connection

To use load balancing to a system over Cloud Connector, you must set the value for *<Proxy Type\>* to `OnPremise`.


<table>
<tr>
<th valign="top">

Property

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`jco.client.mshost`

</td>
<td valign="top">

Represents the message server host to be used. For configurations on SAP BTP, the property must match a virtual host entry in the Cloud Connector *Access Control* configuration. The property indicates that load balancing is used for establishing a connection.

</td>
</tr>
<tr>
<td valign="top">

`jco.client.group`

</td>
<td valign="top">

Optional property. Identifies the group of application servers that is used, the so-called "logon group". If the property is not specified, the group `PUBLIC` is used.

</td>
</tr>
<tr>
<td valign="top">

`jco.client.r3name`

</td>
<td valign="top">

Represents the three-character system ID of the ABAP system to be addressed. For configurations on SAP BTP, the property must match a virtual port entry in the Cloud Connector *Access Control* configuration.

> ### Note:  
> The virtual port in the above access control entry must be named `sapms<###>`, where *<\#\#\#\>* is the value of `r3name`.



</td>
</tr>
<tr>
<td valign="top">

`jco.client.msserv`

</td>
<td valign="top">

Represents the port on which the message server is listening for incoming requests. you can use this property as an alternative to `jco.client.r3name`. One of these two must be present. For configurations on SAP BTP, the property must match a virtual port entry in the Cloud Connector *Access Control* configuration. You can therefore avoid lookups in the `/etc/services` file \(`<Install_Drive>\Windows\System32\drivers\etc\services`\) on the Cloud Connector host.

</td>
</tr>
<tr>
<td valign="top">

`jco.client.client`

</td>
<td valign="top">

Represents the client to be used in the ABAP system. Valid format is a 3-digit number.

</td>
</tr>
</table>

Back to [Content](target-system-configuration-ab6eac9.md#loioab6eac92978f469e9eabe3d477ca2411__content)



<a name="loioab6eac92978f469e9eabe3d477ca2411__web"/>

## WebSocket Connection

To use a direct connection over WebSocket, you must set the value for *<Proxy Type\>* to `Internet`.

**Prerequisites**

Your target system is one of the following:

-   S/4HANA Cloud system
-   SAP BTP, ABAP environment system
-   ABAP server as of S/4HANA \(on-premise\) version 1909


<table>
<tr>
<th valign="top">

Property

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`jco.client.wshost` 

</td>
<td valign="top">

Represents the WebSocket RFC server host on which the target ABAP system is running. The system must be exposed to the Internet.

</td>
</tr>
<tr>
<td valign="top">

`jco.client.wsport` 

</td>
<td valign="top">

Represents the WebSocket RFC server port on which the target ABAP system is listening.

</td>
</tr>
<tr>
<td valign="top">

`jco.client.client`

</td>
<td valign="top">

Represents the client to be used in the ABAP system. Valid format is a 3-digit number. Optional for WebSocket RFC, if not provided, the default client associated with the host will be used.

</td>
</tr>
<tr>
<td valign="top">

`jco.client.tls_trust_all` 

</td>
<td valign="top">

If set to `1`, all server certificates are considered trusted during TLS handshake. If set to `0`, either a dedicated trust store must be configured, or the JDK trust store is used as default. Default value is `0`.

> ### Note:  
> We recommend that you **do not use value `1` \("trust all"\) in productive scenarios**, but only for demo/test purposes.



</td>
</tr>
<tr>
<td valign="top">

*<Trust Store Location\>*

1.  When used in local environment
2.  When used in cloud environment



</td>
<td valign="top">

If you don't want to use the default JDK trust store \(option *Use default JDK truststore* is unchecked\), you must enter a *<Trust Store Location\>*. This field indicates the path to the JKS file which contains trusted certificates \(Certificate Authorities\) for authentication against a remote client.

1.  The relative path to the JKS file. The root path is the server's location on the file system.
2.  The name of the JKS file.



> ### Note:  
> If the *<Trust Store Location\>* is not specified, the JDK trust store is used as a default trust store for the destination.



</td>
</tr>
<tr>
<td valign="top">

*<Trust Store Password\>*

</td>
<td valign="top">

Password for the trust store file specified via *<Trust Store Location\>*. This field is mandatory if *<Trust Store Location\>* is used.

</td>
</tr>
<tr>
<td valign="top">

`jco.destination.ws_ping_period`

</td>
<td valign="top">

Optional property.

Time period of a WebSocket client connection in seconds after which a keep alive WebSocket ping packet is sent while waiting for response data during a call.

-   Switching keep alive pinging from off \[0\] to on \[greater than 10\] and vice versa will only affect new RFC connections opened afterwards.
-   Default is the value of JCo property `jco.ws.ping_period`, which is 300 seconds, if not set to a different value.
-   Valid values are 0 \[off\] and a range from 10 \[ten seconds\] to 86400 \[one day\].



</td>
</tr>
<tr>
<td valign="top">

`jco.destination.ws_pong_timeout`

</td>
<td valign="top">

Optional property.

Timeout for a WebSocket keep alive ping reply packet in seconds. If no such so-called pong packet is received from the communication partner as a reply to a previously sent WebSocket keep alive ping packet within this timeout period, the client connection is considered as broken and will be closed.

-   Switching a pong timeout from off \[0\] to on \[greater than 10\] and vice versa will only affect new RFC connections opened afterwards.
-   Default is the value of JCo property `jco.ws.pong_timeout`, which is 60 seconds, if not set to a different value.
-   Valid values are 0 \[off\] and a range from 10 \[ten seconds\] to 3600 \[one hour\].



</td>
</tr>
</table>

> ### Note:  
> You can upload trust store JKS files using the same command as for uploading destination configuration property files. You only need to specify the JKS file instead of the destination configuration file.

> ### Note:  
> Connections to remote services which require *Java Cryptography Extension \(JCE\) unlimited strength jurisdiction policy* are not supported.

See also [WebSocket RFC](https://help.sap.com/viewer/753088fc00704d0a80e7fbd6803c8adb/latest/en-US/51f1edadb2754e539f6e6335dd1eb4cc.html) \(ABAP Platform documentation\).

Back to [Content](target-system-configuration-ab6eac9.md#loioab6eac92978f469e9eabe3d477ca2411__content)

