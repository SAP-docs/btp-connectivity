<!-- loioab6eac92978f469e9eabe3d477ca2411 -->

# Target System Configuration

Learn about the JCo properties you can use to configure the target sytem information in an RFC destination.

> ### Note:  
> This documentation refers to SAP BTP, multi-cloud foundation. If you are looking for information about the Neo environment, see [Target System Configuration](https://help.sap.com/viewer/b865ed651e414196b39f8922db2122c7/Cloud/en-US/f8fac995b0144a0b8ec0801b8f7bab3e.html "Learn about the JCo properties you can use to configure the target sytem information in an RFC destination (Neo environment).") :arrow_upper_right: \(Neo environment\).



<a name="loioab6eac92978f469e9eabe3d477ca2411__content"/>

## Content

[Overview](target-system-configuration-ab6eac9.md#loioab6eac92978f469e9eabe3d477ca2411__overview)

[Direct Connection](target-system-configuration-ab6eac9.md#loioab6eac92978f469e9eabe3d477ca2411__direct)

[Load Balancing Connection](target-system-configuration-ab6eac9.md#loioab6eac92978f469e9eabe3d477ca2411__load)

[WebSocket Connection](target-system-configuration-ab6eac9.md#loioab6eac92978f469e9eabe3d477ca2411__web)



<a name="loioab6eac92978f469e9eabe3d477ca2411__overview"/>

## Overview

You can use the following configuration types alternatively:

-   Direct connection to an ABAP application server via Cloud Connector.
-   Load balancing connection to a group of ABAP application servers via a message server via Cloud Connector.
-   WebSocket connection to an ABAP application server \(RFC over Internet\)

    > ### Note:  
    > When using a WebSocket connection, the target ABAP system must be exposed to the Internet.


Depending on the configuration you use, different properties are mandatory or optional.

The set of available options depends on the *Proxy Type* chosen while editing the destination. In the *Destinations* editor in the cockpit, the configuration must be provided in the *Target System Configuration* panel.

Back to [Content](target-system-configuration-ab6eac9.md#loioab6eac92978f469e9eabe3d477ca2411__content)



<a name="loioab6eac92978f469e9eabe3d477ca2411__direct"/>

## Direct Connection

To use a direct connection \(connection without load balancing\) to an application server over the Cloud Connector, you must set the value for *Proxy Type* to `OnPremise`. In addition, you must uncheck the checkbox *Use Load Balancing Connection*.


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

Virtual Application Server Host

</td>
<td valign="top">

`jco.client.ashost`

</td>
<td valign="top">

Represents the application server host to be used. For configurations on SAP BTP, the property must match a virtual host entry in the Cloud Connector *Access Control* configuration. The property indicates that a direct connection is established.

</td>
</tr>
<tr>
<td valign="top">

System Number

</td>
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

Client

</td>
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

To use load balancing to a system over Cloud Connector, you must set the value for *Proxy Type* to `OnPremise`. In addition, you must check the checkbox *Use Load Balancing Connection*.


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

Virtual Message Server Host

</td>
<td valign="top">

`jco.client.mshost`

</td>
<td valign="top">

Represents the message server host to be used. For configurations on SAP BTP, the property must match a virtual host entry in the Cloud Connector *Access Control* configuration. The property indicates that load balancing is used for establishing a connection.

</td>
</tr>
<tr>
<td valign="top">

Logon Group

</td>
<td valign="top">

`jco.client.group`

</td>
<td valign="top">

Optional property. Identifies the group of application servers that is used, the so-called "logon group". If the property is not specified, the group `PUBLIC` is used.

</td>
</tr>
<tr>
<td valign="top">

System ID

</td>
<td valign="top">

`jco.client.r3name`

</td>
<td valign="top">

Represents the three-character system ID of the ABAP system to be addressed. For configurations on SAP BTP, the property must match a virtual port entry in the Cloud Connector *Access Control* configuration.

> ### Note:  
> The virtual port in the above access control entry must be named `sapms<###>`, where *<\#\#\#\>* is the value of `r3name`.

> ### Note:  
> In the *Destinations* editor, the check box *Use Message Server Port instead of System ID Connection* must be unchecked.



</td>
</tr>
<tr>
<td valign="top">

Virtual Message Server Port

</td>
<td valign="top">

`jco.client.msserv`

</td>
<td valign="top">

Represents the port on which the message server is listening for incoming requests. you can use this property as an alternative to `jco.client.r3name`. One of these two must be present. For configurations on SAP BTP, the property must match a virtual port entry in the Cloud Connector *Access Control* configuration. You can therefore avoid lookups in the `/etc/services` file \(`<Install_Drive>\Windows\System32\drivers\etc\services`\) on the Cloud Connector host if you want to use the same value for virtual and internal port..

> ### Note:  
> In the *Destinations* editor, the check box *Use Message Server Port instead of System ID Connection* must be unchecked.



</td>
</tr>
<tr>
<td valign="top">

Client

</td>
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

> ### Note:  
> For WebSocket destinations, the connection check is not yet available.

To use a direct connection over WebSocket, you must set the value for *Proxy Type* to `Internet`.

**Prerequisites**

Your target system is one of the following:

-   SAP S/4HANA Cloud system
-   SAP BTP, ABAP environment system
-   ABAP server as of SAP S/4HANA \(on-premise\) version 1909 \(must be exposed to the Internet\)

The trust-related configuration must be provided in the *Client Trust Store* configuration panel.


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

WebSocket RFC Server Host

</td>
<td valign="top">

`jco.client.wshost` 

</td>
<td valign="top">

Represents the WebSocket RFC server host on which the target ABAP system is running. The system must be exposed to the Internet.

</td>
</tr>
<tr>
<td valign="top">

WebSocket RFC Server Port

</td>
<td valign="top">

`jco.client.wsport` 

</td>
<td valign="top">

Represents the WebSocket RFC server port on which the target ABAP system is listening.

</td>
</tr>
<tr>
<td valign="top">

Client

</td>
<td valign="top">

`jco.client.client`

</td>
<td valign="top">

Represents the client to be used in the ABAP system. Valid format is a 3-digit number. Optional for WebSocket RFC, if not provided, the default client associated with the host will be used.

</td>
</tr>
<tr>
<td valign="top">

WebSocket RFC Ping Period

</td>
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

WebSocket RFC Pong Timeout

</td>
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
<tr>
<td valign="top">

Trust All

</td>
<td valign="top">

`jco.client.tls_trust_all` 

</td>
<td valign="top">

The checkbox *Use default client trust store* must be unchecked.

-   If the checkbox *Trust All* is checked, all server certificates are considered trusted during a TLS handshake.
-   If the checkbox *Trust All* is unchecked, either a dedicated trust store must be configured or the default client trust store will be used as default.

In an imported configuration file, the respective values are 1 and 0.

> ### Note:  
> We recommend that you **do not use value `1` \("trust all"\) in productive scenarios**, but only for demo/test purposes.



</td>
</tr>
<tr>
<td valign="top">

TrustStoreLocation

</td>
<td valign="top">

*<Trust Store Location\>*

</td>
<td valign="top">

You can choose a <Trust Store Location\>. This field indicates the name of the trust store on the *Destination Certificates* page which contains trusted certificates \(Certificate Authorities\) for authentication against a remote client.



> ### Note:  
> You can only configure a trust store location, if both the checkboxes *Use default client trust store* and *Trust All* are unchecked.



</td>
</tr>
<tr>
<td valign="top">

TrustStorePassword

</td>
<td valign="top">

*<Trust Store Password\>*

</td>
<td valign="top">

Password for the trust store file specified via *<Trust Store Location\>*.

</td>
</tr>
</table>

> ### Note:  
> You can upload trust store files using the same command as for uploading destination configuration property files. You only need to specify the trust store file instead of the destination configuration file.

> ### Note:  
> Connections to remote services which require *Java Cryptography Extension \(JCE\) unlimited strength jurisdiction policy* are not supported.

For more information on WebSocket RFC, see also [WebSocket RFC](https://help.sap.com/viewer/753088fc00704d0a80e7fbd6803c8adb/latest/en-US/51f1edadb2754e539f6e6335dd1eb4cc.html) \(ABAP Platform documentation\).

Back to [Content](target-system-configuration-ab6eac9.md#loioab6eac92978f469e9eabe3d477ca2411__content)

