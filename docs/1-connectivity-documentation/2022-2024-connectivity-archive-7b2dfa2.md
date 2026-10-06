<!-- loio7b2dfa22556f4cc3b268f8ed1f423a6f -->

# 2022-2024 Connectivity \(Archive\)





**2022**


<table>
<tr>
<th valign="top">

Technical Component

</th>
<th valign="top">

Environment

</th>
<th valign="top">

Title

</th>
<th valign="top">

Description

</th>
<th valign="top">

Action

</th>
<th valign="top">

Lifecycle

</th>
<th valign="top">

Type

</th>
<th valign="top">

Line of Business

</th>
<th valign="top">

Modular Business Process

</th>
<th valign="top">

Product

</th>
<th valign="top">

Latest Revision

</th>
<th valign="top">

Available as of

</th>
<th valign="top">

Version

</th>
<th valign="top">

Scope

</th>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry

-   Neo



</td>
<td valign="top">

Cloud Connector 2.17.2 - Bug Fixes

</td>
<td valign="top">

Release of Cloud Connector version 2.17.2 provides the following bug fixes:

-   The connection check for access control entries could fail even if the connection would work fine in productive usages. This was caused by a changed default value introduced in Tomcat 9.0.90. With the upgrade to Tomcat 9.0.95, the problem has been solved. This was a regression in 2.17.1.
-   When upgrading a shadow instance, the master high availability \(HA\) port got lost during the upgrade. This was a regression in 2.17.1.
-   Pressing CapsLock when entering a password into Cloud Connector's login screen deleted the password characters that were entered so far. This was caused by a regression in UI5 Core 1.108.30 that was used in 2.17.1.
-   In the connection monitor details view the active requests were not showing the user that is invoking the service, even if the user is actually known. This was a regression introduced in 2.16.0.
-   Due to a faulty consistency check, the custom regions list contained all the known regions that were in use on the Cloud Connector. This illegal state has been corrected.
-   When using a dedicated HA port and resetting the HA settings on a shadow, the shadow's UI port within the HA information was wrongly set to the HA port. As a consequence, after connecting again to a master, it was not possible to open the shadow UI using the button in the master UI in the *High Availability* screen.



</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">

2024-10-31

</td>
<td valign="top">

2024-10-31

</td>
<td valign="top">

2.17.2

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry

-   Neo



</td>
<td valign="top">

Cloud Connector 2.17.2 - Enhancements

</td>
<td valign="top">

Release of Cloud Connector version 2.17.2 provides the following enhancements:

-   Introduced a CapsLock warning on all password input fields. Previously, such a warning was only shown on the login screen.
-   Cloud Connector does no longer allow to upload UI certificates from a P12 file that include the KeyUsage certsigning. Such certificates are not accepted by all browsers for identifying a server.
-   The connection check for access control entries is now allowed for all authenticated users.
-   When opening TCP connections successfully, an audit log entry is written that access to the system has been allowed.



</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">

2024-10-31

</td>
<td valign="top">

2024-10-31

</td>
<td valign="top">

2.17.2

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry



</td>
<td valign="top">

Cloud Connector - New Regions

</td>
<td valign="top">

Additional regions were added to SAP BTP:

-   ap30: Australia \(Sydney\) - Google Cloud
-   br20: Brazil \(São Paulo\) - Azure
-   sa30: KSA \(Dammam\) - Google Cloud

For more information, see [Cloud Connector: Prerequisites](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/prerequisites?version=Cloud#loioe23f776e4d594fdbaeeb1196d47bbcc0__cf).

In case of questions please contact [SAP Support](https://support.sap.com/en/contact-us.html?anchorId=section_411324132).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Announcement

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">

2024-10-28

</td>
<td valign="top">

2024-10-28

</td>
<td valign="top">

2410b

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry



</td>
<td valign="top">

Destination Service - REST API

</td>
<td valign="top">

The "Get All Destinations" endpoint of the service's REST API now supports suffix-based \(`endsWith`\) filtering on the `Name` property.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">

2024-10-28

</td>
<td valign="top">

2024-10-31

</td>
<td valign="top">

2410b

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry
-   Kyma



</td>
<td valign="top">

Connectivity Proxy for Kubernetes - New Features

</td>
<td valign="top">

Connectivity Proxy version 2.13.0 provides the following new features:

-   The Connectivity Proxy now exposes various JVM and component-specific *Prometheus* metrics.
-   \[Helm\] You can now configure the topology key for the pod anti-affinity of each pod related to the Connectivity Proxy. This gives you more control over pod scheduling.
-   \[Helm\] You can now configure the request and limit resource constraints for the *Region Configuration Controller* micro-service of the Connectivity Proxy.
-   Support for custom PKI \(public key infrastructure\): The Connectivity Proxy now provides a list of certificate authorities which it should trust in addition to the default ones when performing outbound HTTPS calls is now supported.



</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Announcement

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">

2024-10-17

</td>
<td valign="top">

2024-10-17

</td>
<td valign="top">

2.13.0

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry
-   Kyma



</td>
<td valign="top">

Connectivity Proxy for Kubernetes - Security Fixes

</td>
<td valign="top">

Connectivity Proxy version 2.13.0 provides the following security fixes:

-   Multiple OS vulnerabilities by removing or upgrading packages on the image were fixed.

-   Multiple Java vulnerabilities by upgrading dependencies to a newer version were fixed.




</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">

2024-10-17

</td>
<td valign="top">

2024-10-17

</td>
<td valign="top">

2.13.0

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry



</td>
<td valign="top">

Cloud Connector - IP Addresses

</td>
<td valign="top">

Additional IP addresses will be added to all SAP BTP regions running on Amazon Web Services \(AWS\) and Microsoft Azure.

**Action:**

If you restrict system access by *allowlisting IPs* in firewall rules, **make sure you update your configuration** as soon as possible. **The additional IP addresses will be used after January 19, 2025**.

> ### Note:  
> Current IP addresses will continue to function \(and therefore must not be removed\) for some time after that date. A follow-up announcement will be provided once the old IPs can be removed safely.

For more information, see [Cloud Connector: Prerequisites](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/prerequisites?version=Cloud#loioe23f776e4d594fdbaeeb1196d47bbcc0__cf).

In case of questions please contact [SAP Support](https://support.sap.com/en/contact-us.html?anchorId=section_411324132).

</td>
<td valign="top">

Required

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Announcement

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">

2024-10-14

</td>
<td valign="top">

2024-10-14

</td>
<td valign="top">

2410a

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry
-   Kyma



</td>
<td valign="top">

Transparent Proxy for Kubernetes - New Features

</td>
<td valign="top">

Transparent Proxy version 1.6.0 provides the following new features:

-   You can now define a dedicated port on which a destination is consumable inside a Kubernetes cluster.

    For more information, see [Destination Custom Resource](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/destination-custom-resource).

-   Use the *Transparent Proxy Operator* in regular Kubernetes clusters with a single-file installation. The *Transparent Proxy Operator* provides enhanced monitoring of the Transparent Proxy, ensuring it runs optimally according to the provided configuration.

    For more information, see [Installation with Operator](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/installation-with-operator).

-   Seamless consumption of systems defined as LDAP destinations. Work with systems through the LDAP protocol, leveraging the features provided by the Transparent Proxy.

    For more information, see [LDAP Destinations](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/ldap-destinations).

-   Seamless consumption of systems defined as MAIL destinations. Work with systems through the SMTP, POP3, and IMAP protocols, leveraging the features provided by the Transparent Proxy.

    For more information, see [MAIL Destinations](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/mail-destinations).




</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">

2024-09-05

</td>
<td valign="top">

2024-09-05

</td>
<td valign="top">

1.6.0

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry
-   Kyma



</td>
<td valign="top">

Transparent Proxy for Kubernetes - Enhancements

</td>
<td valign="top">

Transparent Proxy version 1.6.0 provides the following enhancements:

-   The Transparent Proxy now responds to Connectivity Proxy updates, providing enhanced synchronization between components.

-   Improved user experience in the Kyma environment by setting the initially created Destination service instance as the default. This eliminates the need for manual configuration and reduces the complexity of setting up the Transparent Proxy.

    For more information, see [Destination Service Integration](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/destination-service-integration).

-   Improved user experience in the Kyma environment by creating a "gateway" destination custom resource by default, allowing you to start using destinations immediately without additional configuration in the Kyma instance.

    For more information, see [Destination Gateway](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/dynamic-lookup-of-destinations).

-   Added extensions to the Kyma dashboard for configuration management. You can now create, update, and delete destination custom resources or update the Transparent Proxy configuration using the new user interface views.

-   Destinations can now be consumed directly from the destination custom resource namespace without specifying the Transparent Proxy namespace in the URL.

    For more information, see [Using the Transparent Proxy](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/using-transparent-proxy).




</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">

2024-09-05

</td>
<td valign="top">

2024-09-05

</td>
<td valign="top">

1.6.0

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry
-   Kyma



</td>
<td valign="top">

Transparent Proxy for Kubernetes - Bug Fixes

</td>
<td valign="top">

Transparent Proxy version 1.6.0 provides the following bug fixes:

-   Fixed an issue with incorrectly parsed dots in the *Address* field of SAP BTP destinations of type TCP. You can now define addresses without any character limitation.

    For more information, see [TCP Destinations](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/tcp-destinations).

-   Fixed multiple *Golang* vulnerabilities by upgrading dependencies to a newer version.




</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">

2024-09-05

</td>
<td valign="top">

2024-09-05

</td>
<td valign="top">

1.6.0

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry

-   Neo



</td>
<td valign="top">

Cloud Connector 2.18.0 - OS Versions

</td>
<td valign="top">

With the next planned feature release of the Cloud Connector \(2.18.0\), we will discontinue support of the following OS versions:

-   Windows 7, 8.1
-   Windows Server 2012, 2012 R2
-   SUSE Linux Enterprise Server 12
-   Red Hat Enterprise Linux 7
-   macOS 10.14,10.15, 11 \(x86\_64\)

The following OS versions do no longer work for existing releases already:

-   SUSE Linux Enterprise Server 11
-   Red Hat Enterprise Linux 6
-   macOS 10.7-10.13 \(x86\_64\)



</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Announcement

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">

2024-08-08

</td>
<td valign="top">

2024-08-08

</td>
<td valign="top">

2.18.0

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry

-   Neo



</td>
<td valign="top">

Cloud Connector 2.17.1 - Bug Fixes

</td>
<td valign="top">

Release of Cloud Connector version 2.17.1 provides the following bug fixes:

-   The subaccount authentication data expiration was not calculated correctly and reported as expired, even if still valid.


Regressions in 2.17.0:

-   LDAP secure host flags \(*Secure Host* and *Secure Alternate Host*\) were neither stored in the LDAP draft configuration nor in the final configuration when pressing the *Save Draft* or *Activate* button.

-   On the subaccount overview page, the region host could have been shown as not reachable with message *Proxy could not be reached*, even though the subaccount is shown as connected and there is no proxy in use. Productive connections were not affected.

-   Adding a subaccount was not possible, if BTP is reached only via a proxy and the proxy returns an unexpected status code on check.

-   CPIC trace files were neither shown nor downloadable from the UI.

-   The *Open Shadow* button at the top of the *High Availability* screen did not result in any action.

-   If adding an RFC SNC access control entry without load balancing logon, the virtual port had an additional 's' at the end. Such an entry could not be used from the cloud side.


These issues have been fixed.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">

2024-08-08

</td>
<td valign="top">

2024-08-08

</td>
<td valign="top">

2.17.1

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry

-   Neo



</td>
<td valign="top">

Cloud Connector 2.17.1 - Enhancements

</td>
<td valign="top">

Release of Cloud Connector version 2.17.1 provides the following enhancement:

-   Additional filters were added in the access control table in which the mappings of virtual to internal systems are listed.



</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">

2024-08-08

</td>
<td valign="top">

2024-08-08

</td>
<td valign="top">

2.17.1

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry

-   Neo



</td>
<td valign="top">

Java Connector 3.1.10.0 - Bug Fixes

</td>
<td valign="top">

Release of Java Connector \(JCo\) version 3.1.10.0 provides the following bug fixes:

-   If a remote-enabled function module \(RFM\) has multiple `TABLES` parameters, the content of one or more received `JCoTable` objects could have been incorrect, all rows of affected tables being only partly filled.

    In this case, each row was populated with data only up to a certain column and following fields were empty or contained their type-specific initial value. The full content of the first `TABLES` parameter was always correct.

    This program error occurred under special complex preconditions, for which the affected `TABLES` parameters needed to have a certain layout structure of field types, while the affected table content was being transferred in compressed row-based serialization format.

    > ### Note:  
    > This was a regression bug which had been introduced with JCo 3.1.9.0

-   Changed values of property `jco.destination.repository_destination`, which were returned from the currently active `DestinationDataProvider` instance for a given destination name, were not processed correctly by the JCo runtime, and already existing `JCoDestination` instances for that destination name were not updated with the new value.

    Such existing `JCoDestination` instances still returned the old `JCoRepository` instance, although a different one might be associated with the newly configured repository destination.


These issues have been fixed.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">

2024-07-11

</td>
<td valign="top">

2024-07-11

</td>
<td valign="top">

3.1.10.0

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry



</td>
<td valign="top">

Cloud Connector - SAP BTP Cockpit - Download Authentication Data

</td>
<td valign="top">

You can now download an authentication data file from your subaccount in the SAP BTP cockpit \(*Connectivity* \> *Cloud Connectors* \> *Download Authentication Data*\) to simplify subaccount configuration in the Cloud Connector administration UI.

For more information, see also [Set up Connection Parameters and HTTPS Proxy](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/cloud-connector-initial-configuration?version=Cloud#set-up-connection-parameters-and-https-proxy) \(steps 2 + 4: file-based subaccount configuration\).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">

2024-06-27

</td>
<td valign="top">

2024-06-27

</td>
<td valign="top">

2406a

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry
-   Kyma



</td>
<td valign="top">

Transparent Proxy for Kubernetes - Hotfix

</td>
<td valign="top">

Transparent Proxy version 1.5.2 provides the following hotfix:

-   Fixed an issue that could potentially increase CPU usage for Transparent Proxy pods beyond the threshold, possibly resulting in failed requests.
-   Fixed an issue in the automated Istio integration which could previously prevent the Transparent Proxy from starting.



</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">

2024-05-29

</td>
<td valign="top">

2024-05-29

</td>
<td valign="top">

1.5.2

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry



</td>
<td valign="top">

Java Connector 3.1.9.0 - Bug Fixes

</td>
<td valign="top">

Release of Java Connector \(JCo\) version 3.1.9.0 provides the following bug fixes:

-   Setting numeric string values into fields of type BCD with method `JCoRecord.setValue([name|index], String)` resulted in a `ConversionException` if the numeric string used scientific notation with an exponent. The same `ConversionException` occurred when deserializing such strings for field type BCD from JSON input data via method `JCoRecord.fromJSON([Reader|String])`.
-   Setting decimal number values into fields of type BCD with method `JCoRecord.setValue([name|index], BigDecimal)` did not throw a `ConversionException` if the fraction part of the provided `java.math.BigDecima`l value had too many digits to fully fit into the BCD field. The `BigDecimal` value was rounded and stored in the BCD field nevertheless. Thus, the provided value's precision was lost unnoticed.

-   If a `JCoFunction` uses a `TABLES` parameter with compatibly-extended metadata having appended additional columns compared to the parameter metadata used on RFC communication partner side, the first additional field of each transferred row could contain NULL-bytes and/or garbage characters. The occurrence of this program error depended on the table row's field structure and whether alignment bytes are required for internally organizing the table content data or not.


These issues have been fixed.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">

2024-05-30

</td>
<td valign="top">

2024-05-30

</td>
<td valign="top">

3.1.9.0

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry



</td>
<td valign="top">

Java Connector 3.1.9.0 - Enhancements

</td>
<td valign="top">

Release of Java Connector \(JCo\) version 3.1.9.0 provides the following enhancements:

-   JCo 3.1.9.0 now supports SapMachine 21.

-   WebSocket RFC client communication has been improved by adding a ping/pong packet exchange mechanism for keeping WebSocket RFC connections alive while waiting for an RFC response from the communication partner. Hence, an underlying TCP/IP network connection should not get closed anymore by firewalls or other network devices due to a potential network traffic idle timeout while waiting for long running requests being processed on the WebSocket RFC communication partner server side.

    Corresponding ping periods and pong timeouts are configurable.

    Find more details about the new properties `jco.destination.ws_ping_period` and `jco.destination.ws_pong_timeout` in [Target System Configuration \(Cloud Foundry environment\)](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/target-system-configuration?version=Cloud#websocket-connection).




</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">

2024-05-30

</td>
<td valign="top">

2024-05-30

</td>
<td valign="top">

3.1.9.0

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Neo



</td>
<td valign="top">

Java Connector 3.1.9.0 - Bug Fixes

</td>
<td valign="top">

Release of Java Connector \(JCo\) version 3.1.9.0 provides the following bug fixes:

-   Setting numeric string values into fields of type BCD with method `JCoRecord.setValue([name|index], String)` resulted in a `ConversionException` if the numeric string used scientific notation with an exponent. The same `ConversionException` occurred when deserializing such strings for field type BCD from JSON input data via method `JCoRecord.fromJSON([Reader|String])`.
-   Setting decimal number values into fields of type BCD with method `JCoRecord.setValue([name|index], BigDecimal)` did not throw a `ConversionException` if the fraction part of the provided `java.math.BigDecima`l value had too many digits to fully fit into the BCD field. The `BigDecimal` value was rounded and stored in the BCD field nevertheless. Thus, the provided value's precision was lost unnoticed.

-   If a `JCoFunction` uses a `TABLES` parameter with compatibly-extended metadata having appended additional columns compared to the parameter metadata used on RFC communication partner side, the first additional field of each transferred row could contain NULL-bytes and/or garbage characters. The occurrence of this program error depended on the table row's field structure and whether alignment bytes are required for internally organizing the table content data or not.


These issues have been fixed.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">

2024-05-16

</td>
<td valign="top">

2024-05-16

</td>
<td valign="top">

3.1.9.0

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Neo



</td>
<td valign="top">

Java Connector 3.1.9.0 - Enhancements

</td>
<td valign="top">

Release of Java Connector \(JCo\) version 3.1.9.0 provides the following enhancements:

-   JCo 3.1.9.0 now requires the Microsoft Visual Studio 2015-2022 C/C++ runtime libraries to be installed on the system. This is relevant when using the SAP BTP SDK for the Neo environment on Windows operating systems.
-   JCo 3.1.9.0 now supports SapMachine 21.

-   WebSocket RFC client communication has been improved by adding a ping/pong packet exchange mechanism for keeping WebSocket RFC connections alive while waiting for an RFC response from the communication partner. Hence, an underlying TCP/IP network connection should not get closed anymore by firewalls or other network devices due to a potential network traffic idle timeout while waiting for long running requests being processed on the WebSocket RFC communication partner server side.

    Corresponding ping periods and pong timeouts are configurable.

    Find more details about the new properties `jco.destination.ws_ping_period` and `jco.destination.ws_pong_timeout` in [Target System Configuration \(Neo environment\)](https://help.sap.com/docs/connectivity/sap-btp-connectivity-neo/target-system-configuration?version=Cloud).




</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">

2024-05-16

</td>
<td valign="top">

2024-05-16

</td>
<td valign="top">

3.1.9.0

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry

-   Neo



</td>
<td valign="top">

Cloud Connector - Direct Upgrades

</td>
<td valign="top">

**Important information**:

Direct Cloud Connector upgrades require a start release of at least 2.13. For versions before 2.13, a two-step upgrade via 2.16 must be done.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Announcement

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">

2024-05-02

</td>
<td valign="top">

2024-05-02

</td>
<td valign="top">

2.17.0

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry

-   Neo



</td>
<td valign="top">

Cloud Connector 2.17.0 - Bug Fixes

</td>
<td valign="top">

Release of Cloud Connector version 2.17.0 provides the following bug fixes:

-   A PATCH operation for */api/v1/configuration/connector/ui/uiCertificate* is no longer disallowed on the shadow instance.
-   The shadow high availability \(HA\) state is now also stored when disconnecting, so that inconsistent states in the HA setup can be avoided.



</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">

2024-05-02

</td>
<td valign="top">

2024-05-02

</td>
<td valign="top">

2.17.0

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry

-   Neo



</td>
<td valign="top">

Cloud Connector 2.17.0 - Enhancements

</td>
<td valign="top">

Release of Cloud Connector version 2.17.0 provides the following enhancements:

-   Cloud Connector 2.17 is based on a different runtime container. So far, it was based on the JavaWeb 3.x runtime on Tomcat 8.5, now it switched to JavaWeb 4.x, which is based on Tomcat 9.
-   The Cloud Connector can now use SAPMachine 21 as Java runtime.

    For more information, see [Prerequisites](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/prerequisites?version=Cloud#jdks).

-   Cloud Connector 2.17 supports up to 3 LDAP servers for authentication. This allows to support setups in which the user base is not completely available in a single LDAP user store, or if there are multiple user bases in a single LDAP user store.

    For more information, see [Use LDAP for User Administration](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/use-ldap-for-authentication?version=Cloud).

-   You can configure a separate port for the high availability \(HA\)- related communication between the two instances \(master and shadow\). This lets you use HA together with certificate-based authentication.

    For more information, see [Install a Failover Instance for High Availability](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/install-failover-instance-for-high-availability?version=Cloud).

-   Additional hardware monitoring REST APIs for disk and CPU status have been provided.

    For more information, see [Monitoring APIs](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/monitoring-apis?version=Cloud#available-apis).

-   You can now use the hardware monitor on the shadow instance as well.

    For more information, see [Hardware Metrics](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/hardware-metrics?version=Cloud).

-   A description for subject patterns was introduced.

    For more information, see [Configure Subject Patterns for Principal Propagation](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/configure-subject-patterns-for-principal-propagation?version=Cloud).

-   Access control data now contains the creation timestamp.

    For more information, see [Configure Access Control](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/configure-access-control?version=Cloud#copy-access-control-settings).

-   You can now add a subaccount using an authentication data file downloaded from SAP BTP.

    For more information, see [Set up Connection Parameters and HTTPS Proxy](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/cloud-connector-initial-configuration?version=Cloud#set-up-connection-parameters-and-https-proxy) \(steps 2 + 4: file-based subaccount configuration\).

-   The Cloud Connector UI now provides a session expiration progress bar in the top right corner of each screen, indicating how long your current session is still valid until you need to login again before proceeding.

    For more information, see [Initial Configuration](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/cloud-connector-initial-configuration?version=Cloud#initial-setup).

-   You can now run the new script `resetCiphers` from the `scc` folder in the Cloud Connector installation directory to reset the ciphers if UI access is blocked due to wrong cipher settings.

    For more information on cipher suites, see [Encryption Ciphers](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/recommendations-for-secure-setup?version=Cloud#encryption-ciphers).




</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">

2024-05-02

</td>
<td valign="top">

2024-05-02

</td>
<td valign="top">

2.17.0

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry
-   Kyma



</td>
<td valign="top">

Transparent Proxy for Kubernetes - New Features

</td>
<td valign="top">

Transparent Proxy version 1.5.0 provides the following new features:

-   The Transparent Proxy module in Kyma now automatically detects and integrates with the Connectivity Proxy module, reducing the need for manual configuration.

    For more information, see [Transparent Proxy in the Kyma Environment](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/transparent-proxy-in-kyma-environment?version=Cloud).

-   Transparent Proxy supports the *Destination Fragment* feature, allowing for the extension of a destination with a fragment. The destination fragments themselves enable more flexible technical connection configuration management for the solution administrators. Now, using the Transparent Proxy, you can easily consume target systems defined as destination-fragment pairs.

    For more information, see [Extending Destinations with Fragments](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/extending-destinations-with-fragments?version=Cloud) and [Destination Fragments](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/destination-fragments-783d44d73212468fbe414495dc32a721?version=Cloud).

-   Transparent Proxy now supports a new integration with Connectivity Proxy in the so-called multi-region setup. This allows you to link the multi-region related configuration between the two components, resulting in simplified consumption at runtime.

    For more information, see [Connectivity Proxy Integration](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/connectivity-proxy-integration?version=Cloud).




</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2024-04-18

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry
-   Kyma



</td>
<td valign="top">

Transparent Proxy for Kubernetes - Enhancements

</td>
<td valign="top">

Transparent Proxy version 1.5.0 provides the following enhancements:

-   Enhanced Integration with Connectivity Proxy in Kubernetes Clusters. This update allows for simpler integration with the Connectivity Proxy outside of the Kyma environment. Users can now link the two components by simply pointing to the Connectivity Proxy service name.

    For more information, see [Connectivity Proxy Integration](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/connectivity-proxy-integration?version=Cloud).

-   Optimized reconciliation process in Transparent Proxy. This optimization allows for quicker synchronization with the SAP Destination service.




</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2024-04-18

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry
-   Kyma



</td>
<td valign="top">

Transparent Proxy for Kubernetes - Bug Fixes

</td>
<td valign="top">

Transparent Proxy version 1.5.0 provides the following bug fixes:

-   Fixed multiple OS vulnerabilities by removing or upgrading packages on the image.
-   Fixed multiple Golang vulnerabilities by upgrading dependencies to a newer version.



</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2024-04-18

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry



</td>
<td valign="top">

Destination Service - Enhancement

</td>
<td valign="top">

The automatic token retrieval functionality of the "find destination" API now supports MAIL destinations with authentication `BasicAuthentication` and all available types of OAuth authentication.

For more information, see [Create Mail Destinations](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/create-mail-destinations?version=Cloud).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2024-03-21

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry



</td>
<td valign="top">

Destination Service - New Feature

</td>
<td valign="top">

A new entity called *destination fragment* has been introduced. Each fragment is a key:value pair and is used to extend and override the properties of a destination at runtime.

This lets you avoid configuration duplication by keeping common properties within a destination and extracting various specific properties into dedicated fragments. At runtime the application can decide which fragment to apply to the base destination, based on the particular scenario.

You can use destination fragments through the Destination service REST API.

For more information, see [Destination Fragments](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/destination-fragments?version=Cloud).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2024-03-12

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry
-   Kyma



</td>
<td valign="top">

Connectivity Proxy for Kubernetes - Kyma Integration

</td>
<td valign="top">

As previously announced \(February 26, 2024\), on-premise connectivity in the Kyma environment will be handled by a Kyma module called *connectivity-proxy*.

This module is now available and can be activated by customers. The result is backward-compatible to the previous built-in solution, but the activation involves a short migration downtime \(see previous announcement\).

> ### Note:  
> Keep in mind that all remaining users using the previous solution will be migrated centrally on March 16 within the announced maintenance window.

For more information, see [On-Premise Connectivity in the Kyma Environment](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/on-premise-connectivity-in-kyma-environment?version=Cloud).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Announcement

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2024-03-12

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry
-   Kyma



</td>
<td valign="top">

Connectivity Proxy for Kubernetes 2.12.1 - Enhancements

</td>
<td valign="top">

Release of Connectivity Proxy version 2.12.1 provides the following enhancement:

You can now configure a `nodeSelector` section for each pod related to the Connectivity Proxy. As an operator, this lets you control on which worker nodes these pods will be scheduled.

For more information, see [Configuration Guide](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/connectivity-proxy-configuration-guide?version=Cloud).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2024-03-21

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry
-   Kyma



</td>
<td valign="top">

Connectivity Proxy for Kubernetes 2.12.1 - Bug Fixes

</td>
<td valign="top">

Release of Connectivity Proxy version 2.12.1 provides the following bug fixes:

-   \[Helm\] Changes in the port of the business data tunnel were not properly taken into account, resulting in inconsistent configurations.
-   \[Helm\] Changes in the Istio gateway selector were not properly taken into account, resulting in inconsistent configurations.
-   Multiple OS vulnerabilities by removing or upgrading packages on the image were detected.
-   Multiple Java vulnerabilities by upgrading dependencies to a newer version were detected.

These issues haave been fixed.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2024-03-21

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry
-   Kyma



</td>
<td valign="top">

Connectivity Proxy for Kubernetes - Announcement

</td>
<td valign="top">

The Connectivity Proxy in the Kyma runtime will be **converted to a standard Kyma third party module**.

All existing instances of the Connectivity Proxy must be converted to the new module-based solution. The **migration is automated** and happens upon enabling the Connectivity Proxy module. After the migration, the Connectivity Proxy will be consumable in the same way as before.

The migration has two stages.

-   As of **March 2, 2024**, the module will be available via the 'fast' channel. **All customers can then enable it** and make the switch \(it will also be available for new installations\).
-   Then, on **March 16, 2024**, during a maintenance window, **all remaining connectivity proxies provisioned via the old approach will automatically be migrated** to the module by SAP.

While the migration results in a backward-compatible deployment of the Connectivity Proxy, the process involves **a downtime of around 2 minutes** \(depending on cluster load and other factors\).

In case of questions or issues, please raise a support ticket on the BC-CP-CON-K8S-PROXY component.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2024-02-26

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry



</td>
<td valign="top">

Cloud Connector - IP Addresses

</td>
<td valign="top">

> ### Note:  
> This release note refers to the same note from November 16, 2023, now including a concrete time limit \(date\) for updating your firewall rules.

Additional IP addresses were added to SAP BTP regions running on Amazon Web Services \(AWS\). The following regions are affected by this change:

-   br10 – Brazil \(São Paulo\)

-   jp10 – Japan \(Tokyo\)

-   ap10 – Australia \(Sydney\)

-   ap11 – Asia Pacific \(Singapore\)

-   ap12 – Asia Pacific \(Seoul\)

-   ca10 – Canada \(Montreal\)

-   eu10 – Europe \(Frankfurt\)

-   eu11 – Europe \(Frankfurt\)

-   us10 – US East \(VA\)


**Action:**

If you restrict system access by *allowlisting IPs* in firewall rules, **make sure you update your configuration** as soon as possible. **The additional IP addresses will be used after March 31, 2024**.

For more information, see [Cloud Connector: Prerequisites](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/prerequisites?version=Cloud#loioe23f776e4d594fdbaeeb1196d47bbcc0__cf).

In case of questions please contact [SAP Support](https://support.sap.com/en/contact-us.html?anchorId=section_411324132).

</td>
<td valign="top">

Required

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2024-02-22

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry

-   Neo



</td>
<td valign="top">

Cloud Connector 2.16.2 - Bug Fixes

</td>
<td valign="top">

Release of Cloud Connector version 2.16.2 provides the following bug fixes:

-   Multiple issues were fixed for configuring certificate-based authentication:
    -   Authentication was no longer working after an upgrade from 2.16.0 to 2.16.1, because the configuration was modified wrongly during the upgrade.
    -   Authentication was no longer working after changing LDAP settings, because the configuration was modified wrongly when persisting the LDAP changes.
    -   The list of trusted certificates could not be adjusted anymore after activating certificate-based authentication.

-   Compatibility mode in bgRFC for sending units to old SAP NetWeaver 7.01 systems contains dummy RFC\_PING invocations to reflect some constraints in such a scenario. The Cloud Connector, however, required RFC\_PING to be part of the access control list and hence did not automatically allow it, like it should be for such infrastructure-related, remote-enabled functions.

    This issue could occur in IBP integration scenarios.

-   The proxy check could wrongly indicate that the HTTPS proxy is not reachable.
-   A vulnerability could occur in the Cloud Connector due to improper checking of certificates.

    For more information, see SAP security note [3424610](https://me.sap.com/notes/3424610).


These issues have been fixed.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2024-02-08

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry

-   Neo



</td>
<td valign="top">

Cloud Connector 2.16.2 - Enhancements

</td>
<td valign="top">

Release of Cloud Connector version 2.16.2 provides the following enhancements:

-   The Cloud Connector now supports clients that use a SAProuter string in their configuration in order to connect to an SNC-protected service channel to an ABAP Cloud system.
-   The Cloud Connector now provides a `changeRole` script that allows to switch the high availability role from master to shadow and vice versa.



</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2024-02-08

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry
-   Kyma



</td>
<td valign="top">

Transparent Proxy for Kubernetes - Hotfix

</td>
<td valign="top">

Transparent Proxy version 1.4.3 provides the following hotfix:

An issue was fixed that could potentially cause misconfiguration of the Transparent Proxy upon restart, and could result in failing requests.

**We strongly recommend that you pull the new version and upgrade as soon as possible.**

</td>
<td valign="top">

Recommended

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2024-02-08

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry

-   Neo



</td>
<td valign="top">

Cloud Connector - Reindexing of Security Recommendations

</td>
<td valign="top">

In the *SAP BTP Security Recommendations*, the index name for the Cloud Connector has been changed from **BTP-CLC-xxxx** to **BTP-SCC-xxxx** to comply with current naming conventions.

No other changes were made to these recommendations.

For more information, see [SAP BTP Security Recommendations](https://help.sap.com/docs/btp/sap-btp-security-recommendations-c8a9bb59fe624f0981efa0eff2497d7d/sap-btp-security-recommendations?version=Cloud).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2024-01-25

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry
-   Kyma



</td>
<td valign="top">

Transparent Proxy for Kubernetes - Changes

</td>
<td valign="top">

Transparent Proxy version 1.4.0 provides the following changes:

-   Enhanced performance on request processing for faster, more efficient target system consumption.

-   Enhanced request troubleshooting, providing detailed error information and source identification.

-   Improved summary of destination custom resources for Kubernetes administrators, providing detailed status without the need for descriptions.




</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2024-01-11

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry
-   Kyma



</td>
<td valign="top">

Transparent Proxy for Kubernetes - New Features

</td>
<td valign="top">

A new version of the Transparent Proxy for Kubernetes \(1.4.0\) has been released.

Transparent Proxy version 1.4.0 provides the following new features:

-   Multitenancy support for seamless consumption of target systems defined as TCP destinations in the different tenants and exposed locally on the level of TCP protocol. The actual communication protocol may be any TCP-based protocol, for example, ODBC/JDBC, SMTP, etc.

    For more information, see [Multitenancy](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/multitenancy?version=Cloud).

-   Simple arbitrary access to destinations. Dynamically access the target systems via a single destination custom resource, instead of creating such for every locally exposed destination.

    For more information, see [Dynamic Lookup of Destinations](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/dynamic-lookup-of-destinations).

-   Native integration with Istio. Easily, via single configuration, add the target systems or service endpoints exposed via Transparent Proxy to the Istio service mesh.

    For more information, see [Configuration Guide](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/transparent-proxy-configuration-guide?version=Cloud).

-   Native integration with the Connectivity Proxy in multi-tenant trusted mode. You can now easily consume target systems without sending identity tokens to the Connectivity Proxy.
-   Automated update of service keys, in use by Transparent Proxy, upon Kubernetes secrets change.
-   The Transparent Proxy module in Kyma now auto-detects and loads all Destination service instance bindings within its namespace, reducing the need for manual configuration. For more information, see [Transparent Proxy in the Kyma Environment](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/transparent-proxy-in-kyma-environment?version=Cloud).
-   The Transparent Proxy module in Kyma now, by default, creates a Destination service instance and binding upon enabling the module, significantly simplifying the initial setup.

    For more information, see [Transparent Proxy in the Kyma Environment](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/transparent-proxy-in-kyma-environment?version=Cloud).




</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2024-01-11

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry



</td>
<td valign="top">

Connectivity Proxy for Kubernetes 2.11.0 - Enhancements

</td>
<td valign="top">

Release of Connectivity Proxy version 2.11.0 \(2.10 intentionally skipped\) provides the following enhancements:

-   You can now use a multi-region setup for a single Connectivity Proxy installation. This setup lets you use one proxy installation with several SAP BTP regions \(or with different subaccounts within the same region\).

    For more information, see [Installing the Connectivity Proxy in Multi-Region Mode](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/installing-connectivity-proxy-in-multi-region-mode).

-   The *DigiCert G5 Root CA* was added to the trust store of the Connectivity Proxy.



</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2023-12-14

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry



</td>
<td valign="top">

Connectivity Proxy for Kubernetes 2.11.0 - Changes

</td>
<td valign="top">

Release of Connectivity Proxy version 2.11.0 \(2.10 intentionally skipped\) provides the following changes:

-   The "utility docker images", used by Helm for execution of pre- and post-deploy jobs can now be configured, allowing the use of private repositories.
-   The configured images in the helm chart can now be configured with a digest instead of tag in order to be more specific in referencing the desired image. Tag is still the default.
-   The Connectivity Proxy is now running on SAP Machine 17, instead of the previously used SAP Machine 11.
-   There is now automatic periodic checking in the Connectivity Proxy components for new CAs, used by the Connectivity service to issue Cloud Connector certificates. As a result, you no longer need to periodically perform a helm upgrade to refresh the list of trusted CAs.



</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2023-12-14

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry



</td>
<td valign="top">

Connectivity Proxy for Kubernetes 2.11.0 - Security

</td>
<td valign="top">

Release of Connectivity Proxy version 2.11.0 \(2.10 intentionally skipped\) provides the following security updates:

-   Multiple open-source components have been upgraded.
-   This release contains several version bumps of dependency libraries, including various security fixes. **We recommend that you upgrade the Connectivity Proxy to the latest version**.



</td>
<td valign="top">

Recommended

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2023-12-14

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry



</td>
<td valign="top">

Connectivity Proxy for Kubernetes 2.11.0 - Bug Fixes

</td>
<td valign="top">

Release of Connectivity Proxy version 2.11.0 \(2.10 intentionally skipped\) provides the following bug fix:

The pod limit configurations of one of the operators of the Connectivity Proxy were adjusted in order to prevent potential startup issues.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2023-12-14

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry



</td>
<td valign="top">

Cloud Connector - IP Addresses

</td>
<td valign="top">

Additional IP addresses were added to SAP BTP regions running on Amazon Web Services \(AWS\). The following regions are affected by this change:

-   br10 – Brazil \(São Paulo\)

-   jp10 – Japan \(Tokyo\)

-   ap10 – Australia \(Sydney\)

-   ap11 – Asia Pacific \(Singapore\)

-   ap12 – Asia Pacific \(Seoul\)

-   ca10 – Canada \(Montreal\)

-   eu10 – Europe \(Frankfurt\)

-   eu11 – Europe \(Frankfurt\)

-   us10 – US East \(VA\)


**Action:**

If you restrict system access by *allowlisting IPs* in firewall rules, **make sure you update your configuration** as soon as possible. The new IP addresses *may be used as of late Q1, 2024*.

For more information, see [Cloud Connector: Prerequisites](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/prerequisites?version=Cloud#loioe23f776e4d594fdbaeeb1196d47bbcc0__cf).

In case of questions please contact [SAP Support](https://support.sap.com/en/contact-us.html?anchorId=section_411324132).

</td>
<td valign="top">

Required

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2023-11-16

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry

-   Neo



</td>
<td valign="top">

Cloud Connector 2.16.1 - Bug Fixes

</td>
<td valign="top">

Release of Cloud Connector version 2.16.1 provides the following bug fixes:

-   LDAP role names were wrongly displayed in the administration UI. Actually, the position was shifted by one.

    > ### Note:  
    > The runtime was not affected.

    This was a regression in version 2.16.0.

    The issue has been fixed.

-   Passwords with leading or trailing spaces did not work neither in the logon screen nor in the LDAP test UI.

    When creating a backup in the administration UI with a password containing special characters, it could not be restored. This was a regression introduced with version 2.15.1.

    The issue has been fixed.

    > ### Note:  
    > Creating backups with the REST API was not affected.

-   Selecting a subaccount in the administration UI might have failed.

    This happened if there are more than 100 subaccounts hosted on the Cloud Connector instance and when filtering the subaccount list.

    In this case, a completely different one was selected when choosing the subaccount. This was a regression in version 2.16.0.

    The issue has been fixed.

-   During an upgrade via RPM it could happen that the UI after the initial login screen was not loading.

    In the traces of the Cloud Connector, you could see many messages telling that a JAR file could not be found that was existing only before the upgrade. This could be resolved by a restart of the daemon only. The issue was caused by another issue in upgrade processing, which has been improved to avoid the erroneous situation.

-   Avoid a *NullPointerException* when receiving a *close* request in RFC protocol processing. This could lead to wrong values for the connection monitor for RFC connections. The call stack of the exception started with *java.lang.NullPointerException: while trying to invoke the method com.sap.core.connectivity.spi.processing.TargetHost.connectionProtocol\(\) of a null object loaded from local variable 'target'* 

    at

    *com.sap.scc.metering.backend.BackendCallStatisticsCollector.updateNonRequestBased\(BackendCallStatisticsCollector.java:109\)* 

    at

    *com.sap.scc.metering.backend.BackendCallStatisticsCollector.reportCloseConnection\(BackendCallStatisticsCollector.java:96*\)

-   Corrupted subaccounts could not be loaded properly. As a consequence, it was impossible to delete them from the administration UI.

    In some cases, they even did not appear in the list of subaccounts, but were existing, so trying to add such a subaccount would fail.

    This issue has been fixed.


-   Self-signed system certificates containing SANs need to have all CA attributes, which is not desired for the system certificate, and hence it does not have them.

    As a consequence, such a certificate cannot be added to the trust store of a server, which is needed to establish trust.

    By not allowing to add SAN elements to self-signed system certificates, this problem can no longer occur.


-   A denial of service vulnerability in the Cloud Connector was fixed.

    For more information, see security note [https://me.sap.com/notes/3362463](https://me.sap.com/notes/3362463).




</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2023-11-16

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry

-   Neo



</td>
<td valign="top">

Cloud Connector 2.16.1 - Enhancements

</td>
<td valign="top">

Release of Cloud Connector version 2.16.1 provides the following enhancement:

The subaccount dashboard now allows to sort the entries based on the display name.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2023-11-16

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry
-   Kyma



</td>
<td valign="top">

Transparent Proxy for Kubernetes - Kyma Environment

</td>
<td valign="top">

The Transparent Proxy is now part of the Kyma environment as a module.

You can benefit from the SAP managed product lifecycle and enhanced support for the Transparent Proxy in your Kyma runtime.

For more information, see [Transparent Proxy in the Kyma Environment](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/transparent-proxy-in-kyma-environment?version=Cloud).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2023-10-05

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry
-   Kyma



</td>
<td valign="top">

Transparent Proxy for Kubernetes - Bug Fix

</td>
<td valign="top">

Release of Transparent Proxy for Kubernetes 1.3.1 provides the following bug fix:

An issue originating from Istio 1.18.1 \(respectively Kyma 2.17\) could cause the Transparent Proxy to fail upon startup.

This issue has been fixed.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2023-08-24

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry

-   Neo



</td>
<td valign="top">

Java Connector 3.1.8.0 - Bug Fixes

</td>
<td valign="top">

Release of Java Connector \(JCo\) version 3.1.8.0 provides the following bug fixes:

-   Calls to RFMs \(RFC-enabled function modules\) did not work, if the respective RFM was defined with *Interface Contract* "Fast serialization required", although fast serialization was configured for the used `JCoDestination` via logon property `jco.client.serialization_format=columnBased`.

    In this case, a system dump with runtime error RFC\_NOTSUPPORTED\_SERIALIZATION occurred at ABAP system side and a corresponding `JCoException` with error group JCO\_ERROR\_SYSTEM\_FAILURE was thrown at JCo side.

-   When the JCo application was running in certain time zones, setting a `String` or `char[]` object value into a type TIME field or parameter resulted in a `ConversionException`, although the specified time value string was valid. For example, when running in time zone America/Mazatlan, then invoking `JCoRecord.setValue([index|name], "18:30:00")` caused an exception similar to the following one:

    *com.sap.conn.jco.ConversionException: \(122\) JCO\_ERROR\_CONVERSION: Cannot convert the value'18:30:00' from type java.lang.String to type TIME field <name\> in record <recordName\>*

-   When getting a `java.util.Date` object from a `JCoRecord` field of type `CHAR`, whose content represents a date or time value in ISO format \(YYYY-MM-DD for dates or HH:MM:SS for times\), a `ConversionException` was thrown, although such a type conversion is possible and allowed.

    > ### Note:  
    > This was a regression bug which had been introduced with JCo 3.1.7.0.

-   `JCoDestination` instances with authentication type `PrincipalPropagation` were unnecessarily used by a `JCoRepository` for querying RFC metadata, which might have ended up in a `JCoException` with error group JCO\_ERROR\_CONFIGURATION, if currently no logged-on user identity was available.



</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2023-08-24

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry



</td>
<td valign="top">

Destination Service - Alert Notifications

</td>
<td valign="top">

An event will be produced in the Alert Notification service when the subaccount trust certificate of the Destination service \(used for SAML-based scenarios\) is close to expiring, allowing administrators to react accordingly ahead of time.

For more information, see [Notifications and Alerts](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/notifications-and-alerts?version=Cloud).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2023-08-10

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry

-   Neo



</td>
<td valign="top">

Cloud Connector 2.16.0 - Removed Feature

</td>
<td valign="top">

Release of Cloud Connector version 2.16.0 no longer provides the following feature:

Due to the discontinuation of the *Enhanced Disaster Recovery Service*, the related functionality in the Cloud Connector has been dropped.

For more information, see the corresponding [Enhanced Disaster Recovery Service release note](https://help.sap.com/whats-new/cf0cb2cb149647329b5d02aa96303f56?Component=Enhanced%2520Disaster%2520Recovery%2520Service&locale=en-US&version=Cloud).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2023-07-27

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry

-   Neo



</td>
<td valign="top">

Cloud Connector 2.16.0 - Bug Fix

</td>
<td valign="top">

Release of Cloud Connector version 2.16.0 provides the following bug fix:

The usage monitor data is no longer lost when doing a master-shadow switch.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2023-07-27

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry

-   Neo



</td>
<td valign="top">

Cloud Connector 2.16.0 - Enhancements

</td>
<td valign="top">

Release of Cloud Connector version 2.16.0 provides the following enhancements:

-   The Cloud Connector now supports Oracle Linux 9 as additional OS version.

    For more information, see [Product Availability Matrix](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/prerequisites?version=Cloud#loioe23f776e4d594fdbaeeb1196d47bbcc0__matrix).

-   macOS on aarch64 is added as a supported platform for the Cloud Connector.

    For more information, see [Product Availability Matrix](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/prerequisites?version=Cloud#loioe23f776e4d594fdbaeeb1196d47bbcc0__matrix).

-   Service channels for RFC that are exposing classic RFC endpoints to ABAP cloud systems, such as S/4HANA Cloud, IBP, or SAP BTP ABAP environment, can now be protected with SNC.

    For more information, see [Configure a Service Channel for RFC](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/configure-service-channel-for-rfc?version=Cloud).

-   The Cloud Connector now allows the logon to the UI and the REST APIs with a client certificate.

    For more information, see [Logon to the Cloud Connector via Client Certificate](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/logon-to-cloud-connector-via-client-certificate?version=Cloud).

-   The connection monitor and the usage monitor now also support access control entries for the TCP protocol.

    For more information, see [Backend Connections](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/monitoring-cloud-to-on-premise?version=Cloud#backend-connections) and [Usage Statistics](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/monitoring-cloud-to-on-premise?version=Cloud#usage-statistics).

-   The hardware monitor information of the last 24 hours is now surviving a restart.

    For more information, see [Hardware Metrics](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/hardware-metrics?version=Cloud).

-   You can now export the selected audit log entries to a csv file for external analysis.

    For more information, see [Manage Audit Logs](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/manage-audit-logs?version=Cloud).




</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2023-07-27

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry
-   Kyma



</td>
<td valign="top">

Transparent Proxy for Kubernetes - New Version

</td>
<td valign="top">

A new version of the Transparent Proxy for Kubernetes \(1.3.0\) has been released.

Changed features:

-   TCP connectivity is now allowed by default in Istio mesh.

For more information, see [Transparent Proxy for Kubernetes](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/transparent-proxy-for-kubernetes?version=Cloud).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2023-07-13

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry
-   Kyma



</td>
<td valign="top">

Transparent Proxy for Kubernetes - New Version

</td>
<td valign="top">

A new version of the Transparent Proxy for Kubernetes \(1.3.0\) has been released.

New features:

-   Multitenancy support for seamless consumption of HTTP target systems defined as destinations in different tenants​.

    For more information, see [Multitenancy](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/multitenancy?version=Cloud).

-   You can now work with multiple Destination service instances, even if located on a different BTP region​.

    For more information, see [Lifecycle Management](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/transparent-proxy-lifecycle-management?version=Cloud).

-   Transparent handling of client assertion authentication flow for the respective destination authentication types. See also the corresponding [Destination service release note](https://help.sap.com/whats-new/cf0cb2cb149647329b5d02aa96303f56?Component=Connectivity&locale=en-US&Valid_as_Of=2023-05-04%3A2023-05-04).

    For more information, see [HTTP Authentication](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/http-authentication?version=Cloud).

-   Lifecycle management via [Landscaper](https://github.com/gardener/landscaper/)​ is now supported.

    For more information, see [Lifecycle Management](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/transparent-proxy-lifecycle-management?version=Cloud).

-   You can now remove obsolete Helm configurations.​

    For more information, see [Lifecycle Management](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/transparent-proxy-lifecycle-management?version=Cloud).




</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2023-07-13

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry



</td>
<td valign="top">

Destination Service - Changes

</td>
<td valign="top">

-   You can now use the API for returning only the public part of a stored certificate also for password-protected keystores, as long as the password is known to the Destination service \(that is, generated via the service\).
-   Using the query parameter of the "Find" API for skipping token retrieval on OAuth destinations with mTLS now includes the certificate for the token service as part of the API response body.



</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2023-07-13

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry



</td>
<td valign="top">

Destination Service - Service Instance Transformation

</td>
<td valign="top">

Service instance transformation for the Document Management service and SAP Build Process Automation is now supported.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2023-07-13

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry



</td>
<td valign="top">

Destination Service - Alert Notifications

</td>
<td valign="top">

The Destination service is now integrated with the Alert Notification service \(ANS\). Currently, you can get notifications for expiring certificate entities which are not enabled for automatic renewal.

For more information, see [Notifications and Alerts](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/notifications-and-alerts?version=Cloud).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2023-05-18

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry



</td>
<td valign="top">

Connectivity Proxy for Kubernetes 2.9 - Bug Fixes

</td>
<td valign="top">

Release of Connectivity Proxy version 2.9 provides the following bug fixes:

-   The Helm chart templates were not compatible with the latest Istio versions.
-   Multiple OS vulnerabilities were caused by removing or upgrading packages on the image.
-   Multiple Java vulnerabilities were caused by upgrading dependencies to a newer version.

These issues have been fixed.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2023-05-03

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry



</td>
<td valign="top">

Connectivity Proxy for Kubernetes 2.9 - Enhancements

</td>
<td valign="top">

Release of Connectivity Proxy version 2.9 provides the following enhancements:

-   You can now disable the "service channels" feature to install multiple connectivity proxies on the same cluster.
-   Host OS versions, containing *cgroup v2*, are now available.
-   You can now install the Transparent Proxy together with the Connectivity Proxy via Helm chart.
-   You can now use embedded corporate JWTs \(JSON web tokens\) for principal propagation.

For more information, see [Connectivity Proxy for Kubernetes](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/connectivity-proxy-for-kubernetes?version=Cloud).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2023-05-03

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry

-   Neo



</td>
<td valign="top">

Cloud Connector - OS Versions

</td>
<td valign="top">

The Cloud Connector supports Oracle Linux 8 as additional OS version.

For more information, see [Product Availability Matrix](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/prerequisites?version=Cloud#loioe23f776e4d594fdbaeeb1196d47bbcc0__matrix).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2023-04-28

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry

-   Neo



</td>
<td valign="top">

Cloud Connector 2.15.2 - Bug Fixes

</td>
<td valign="top">

Release of Cloud Connector version 2.15.2 provides the following bug fixes:

-   The connection check for LDAPS access control entries was always failing.

    This issue has been fixed.

    > ### Note:  
    > The actual runtime was not affected.

-   Subject patterns could not be modified. Only deleting and adding was possible.

    This was a regression in 2.15.1 only.

-   High availability master/shadow configuration synchronization could be permanently disrupted if an administrator triggered a role switch.

    On shadow side, the trace was showing reoccurring *NullPointerExceptions* at method *com.sap.scc.info.SupportInfo.getSccVersion\(\)*.

    This issue has been fixed.

-   Disabling trusted OAuth servers is no longer ignored when verifying JSON web tokens \(JWTs\) for principal propagation.



</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2023-04-20

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry

-   Neo



</td>
<td valign="top">

Cloud Connector 2.15.2 - Enhancement

</td>
<td valign="top">

Release of Cloud Connector version 2.15.2 provides the following enhancement:

The lists for *Most Recent Requests* and *Top Time Consumers* in the monitor now contain a *User* column.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2023-04-20

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry



</td>
<td valign="top">

Destination Service - Client Assertions

</td>
<td valign="top">

You can now use client assertions that are automatically fetched by the Destination service, as an OAuth client authentication method.

This extends the existing method for caller-provided assertions via HTTP header when calling the "Find Destination" API.

For more information, see [Using Client Assertion with OAuth Flows](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/using-client-assertion-with-oauth-flows).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2023-05-04

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry
-   Kyma



</td>
<td valign="top">

Transparent Proxy for Kubernetes - Changes

</td>
<td valign="top">

Transparent Proxy version 1.2.0 includes the following changes:

-   Improved handling for the streaming of large payloads, ensuring efficient data transfer between client and server.
-   Applied several performance improvements.
-   Fixed OSS vulnerabilities by removing or upgrading related packages on the image.



</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2023-03-23

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry
-   Kyma



</td>
<td valign="top">

Transparent Proxy for Kubernetes - Enhancements

</td>
<td valign="top">

Transparent Proxy version 1.2.0 introduces the following features:

-   Support and transparent handling of the *OAuth2TechnicalUserPropagation* authentication type.
-   Added an option for declarative control over the access \(scope of visibility\) to the exposed destinations in the Kubernetes cluster.
    -   If default scope is set to “clusterWide” - every workload from every namespace can access the exposed destination.
    -   If default scope is set to “namespaced” – the Transparent Proxy limits the access \(scope of visibility\) to destination CRs only to workloads hosted in the same namespace where the destination CRs are managed.

-   Enables administrators to configure internal handling of secure communication between Transparent Proxy's internal micro-components by encrypting their connections using mutual TLS \(mTLS\).
-   Enables horizontal autoscaling of the Transparent Proxy's components based on their load.
-   Enables vertical autoscaling of the Transparent Proxy's components based on their load.
-   Added support for manual deployment in SAP Kyma runtime, enabling the Transparent Proxy to be configured and run seamlessly.

For more information, see [Transparent Proxy for Kubernetes](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/transparent-proxy-for-kubernetes?version=Cloud).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2023-03-23

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry



</td>
<td valign="top">

Connectivity Service - Authentication

</td>
<td valign="top">

As new option for principal propagation, you can now use an embedded corporate IdP token for scenarios where the user token sent to the Connectivity service has an embedded JWT \(JSON Web token\) from the original corporate IdP.

This token will be sent to the Cloud Connector and will be used to issue the short-lived certificate.

For more information, see [Configure Principal Propagation via Corporate IdP Embedded Token](https://help.sap.com/docs/CP_CONNECTIVITY/cca91383641e40ffbe03bdc78f00f681/dfecfb4be336426bb31cd2843baeb8d4.html?version=Cloud).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2023-03-09

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry



</td>
<td valign="top">

Destination Service - Certificates

</td>
<td valign="top">

You can now use a *CSR* \(certificate signing request\) to generate certificates that are signed by the *SAP Cloud Root CA*, in addition to the already supported method of providing just parameters for the generation.

This new option lets you use your own local private key.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2023-02-09

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry

-   Neo



</td>
<td valign="top">

Java Connector 3.1.7.0 - Bug Fixes

</td>
<td valign="top">

Release of Java Connector \(JCo\) version 3.1.7.0 provides the following bug fixes:

-   basXML deserialization:

    When calling an RFC-enabled function module and using basXML serialization, an exception at deserializing the RFC response data might have occurred if skipping some unneeded basXML content was required. The exception was similar to:

    *BasXMLParser.parse threw exception while parsing parameter <paramName\> when processingfield <fieldName\> com.sap.conn.jco.XMLParserException: \(130\) JCO\_ERROR\_XML\_PARSER:Unexpected token while discarding <fieldName\> in content of parameter <paramName\> of the currentBXML document: '<?\>' at position <\#\#\#\#\#\>* 

    *at com.sap.conn.jco.rt.BasXMLParser.parse\(BasXMLParser.java:536\)* 

    *at com.sap.conn.jco.rt.BasXMLParser.setCompressedBytes\(BasXMLParser.java:1588\)* 

    *at com.sap.conn.rfc.engine.RfcImp.receiveBasXMLCompressedData\(RfcImp.java:377\)* 

    *at com.sap.conn.rfc.engine.RfcGet.ab\_rfcget\(RfcGet.java:425\)* 

    *at com.sap.conn.rfc.engine.RfcRcv.ab\_rfcreceive\(RfcRcv.java:41\)* 

    *at com.sap.conn.rfc.engine.RfcIoOpenCntl.RfcReceive\(RfcIoOpenCntl.java:2078\)* 

    ...

-   Type TIME field value conversions from/to `java.util.Date` objects:

    When getting or setting a `java.util.Date` object from or to a `JCoRecord` field of type TIME, a `ConversionException` might have been thrown depending on the clock time value and the time zone, in which the JCo application was running. For example, when running in time zone America/Mazatlan, invoking `JCoRecord.getTime(...)` could have caused an exception similar to the following one:

    *com.sap.conn.jco.ConversionException: Unparseable date: "000000" in record <name\> at field <name\>*

-   Type `UTCLONG` field value conversions from/to `java.util.Date` objects:

    When getting or setting a `java.util.Date` object from or to a `JCoRecord` field of type `UTCLONG`, the converted timestamp value was wrong because the default time zone was used for the conversion instead of the UTC time zone.




</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2023-01-26

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry

-   Neo



</td>
<td valign="top">

Java Connector 3.1.7.0 - Enhancements

</td>
<td valign="top">

Release of Java Connector \(JCo\) version 3.1.7.0 introduces the following enhancements:

-   `JCoRepository`:

    A new API method `JCoRepository.removeOutdatedMetaDataFromCache()` has been introduced to identify and remove outdated metadata from the local cache.

    Moreover, a new destination property `jco.destination.repository.check_interval` has been added to execute this new cache removal feature in regular time intervals. It allows a more convenient usage of JCo in development environments, where ABAP remote function interfaces, structures, and tables change frequently, so that it is not necessary to clear the whole `JCoRepository` cache manually anymore, or to restart a centrally running JCo webserver application each time after dynamically retrieved RFC metadata has been modified in the origin SAP backend system.

    For more informaton, see the API documentation.

-   `JCoRecord`:

    New API methods have been introduced to the `JCoRecord` interface: `JCoRecord.setValue([index|name]`, `java.util.Date)` and `JCoRecord.setValue([index|name], java.math.BigInteger)`.

    These new API methods serve as type-safe and more performant replacement of method `JCoRecord.setValue([index|name], java.lang.Object)` for setting field values from `java.util.Date` and `java.math.BigInteger` objects.

-   `JCoRequest`:

    The `JCoRequest` interface has been enhanced with additional `execute(...)` methods to support also tRFC and qRFC executions when using the request/response programming model.

    For more informaton about the additional methods, see the JavaDoc of interface `JCoRequest`.




</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2023-01-26

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry



</td>
<td valign="top">

Destination Service - Certificates

</td>
<td valign="top">

You can now use a REST API to manage *active* and *passive* subaccount certificates, and switch their roles. This lets you perform a non-disruptive rotation of the signing certificate \(for example, when the active certificate is close to the expiry date\).

For more information, see [Rotate Certificates](https://help.sap.com/docs/CP_CONNECTIVITY/cca91383641e40ffbe03bdc78f00f681/82dbecae3454493782d16a79e30f1a6d.html?version=Cloud#rotate-certificates).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2023-01-26

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry

-   Neo



</td>
<td valign="top">

Cloud Connector 2.15.1 - Bug Fixes

</td>
<td valign="top">

Release of Cloud Connector version 2.15.1 provides the following bug fixes:

-   Principal propagation scenarios could fail producing a trace entry that contains the message "*SSO token validation failed: com.sap.core.connectivity.tunnel.client.sso.InvalidSSOTokenException: No principal is extracted, as the principal type UNKNOWN is invalid.*"

    This issue has been fixed.

-   In the context of *high availability*, a master instance could permanently show a shadow instance as *connected since January 1, 1970*, even if the shadow was disconnected.

    This issue has been fixed.

-   It was not possible to edit Kubernetes cluster service channels in the administration UI.

    This wrong behavior has been fixed.

-   When performing an [upgrade avoiding downtime](https://help.sap.com/docs/CP_CONNECTIVITY/cca91383641e40ffbe03bdc78f00f681/7a7cc373019b4b6eaab39b5ab7082b09.html#avoid-connectivity-downtime), the subject pattern for principal propagation was reset to the default value.

    This issue has been fixed.

-   Java 17 support was incomplete so that certain operations were failing. For example, when synchronizing trusted identity providers, an HTTP 500 error was shown in the administration UI.

    This issue has been fixed.

-   The *regression garbage collection history* file of SAP JVM 8 was no longer created when using the Windows portable version.

    This issue has been fixed.




</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2022-12-15

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry



</td>
<td valign="top">

Connectivity Service - Bug Fix

</td>
<td valign="top">

When making `HTTP HEAD` requests in certain error cases \(like a path not being allowed in the Cloud Connector\), the response contained a body.

This issue has been fixed.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2022-12-15

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry
-   Kyma



</td>
<td valign="top">

Transparent Proxy for Kubernetes - New Version

</td>
<td valign="top">

Transparent Proxy for Kubernetes version 1.1.1 is now available.

**New**

-   Added support and transparent handling of:
    -   *OAuth Refresh Token* and *OAuth Authorization Code* authentication types

    -   Custom headers and query parameters configured in a destination

    -   HTTP timeout configurations configured in a destination



-   Support for the mTLS-based service instance key for technical access to the Destination service
-   Improved error handling

**Security** 

-   Fixed OSS vulnerabilities by removing or upgrading related packages on the image

For more information, see [Transparent Proxy for Kubernetes](https://help.sap.com/docs/CP_CONNECTIVITY/cca91383641e40ffbe03bdc78f00f681/acc64ada71e34f98867f16fbcc471b5e.html).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2022-11-17

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry



</td>
<td valign="top">

Destination Service - New Features

</td>
<td valign="top">

-   You can now configure timeouts towards the token service for automatic token retrieval \(via destination properties\).

    For more information, see [HTTP Destinations](https://help.sap.com/docs/CP_CONNECTIVITY/cca91383641e40ffbe03bdc78f00f681/42a0e6b966924f2e902090bdf435e1b2.html).

-   A new authentication type for *technical user propagation* is now available \(only for on-premise connections via the Connectivity service\).

    For more information, see [Authentication to the On-Premise System](https://help.sap.com/docs/CP_CONNECTIVITY/cca91383641e40ffbe03bdc78f00f681/67b0b94f09f2446598787eea0855e56b.html?#authentication-types).

-   A new API endpoint for retrieving only the public part of a certificate configuration is now available.



</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2022-11-09

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Neo



</td>
<td valign="top">

Cloud Connector - New IP Addresses for the Neo Environment

</td>
<td valign="top">

> ### Caution:  
> The planned IP changes of the Connectivity service \(Neo environment\) for the Cloud Connector in Q4 2022 \(see related note from September 19, 2022\) particularly affect Cloud Connector versions prior to 2.12.2.
> 
> **Required Action:** 
> 
> *If you use IP-based firewall rules and one of these Cloud Connector versions*, make sure you include **both** the old and new IP addresses for each connected region that shows an **OLD** and **NEW** IP address \(Cloud Connector documentation\) *as soon as possible*, to avoid outages. Otherwise, a restart of the Cloud Connector will be required after the IP changes are effective.
> 
> For more information, see [Prerequisites](https://help.sap.com/docs/CP_CONNECTIVITY/b865ed651e414196b39f8922db2122c7/e23f776e4d594fdbaeeb1196d47bbcc0.html#loioe23f776e4d594fdbaeeb1196d47bbcc0__neo).



</td>
<td valign="top">

Required

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Announcement

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2022-10-20

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry



</td>
<td valign="top">

Connectivity Proxy for Kubernetes - New Version

</td>
<td valign="top">

Version \(2.8.0\) is now available for the Connectivity Proxy for Kubernetes.

**New**

-   You can now configure the allowed cypher suites for the *Ingress* endpoint of the Connectivity Proxy via the Helm chart.
-   Added support for granular access control for service mapping resources \(for the on-premise to cloud scenario\), based on the Cloud Connector location ID.

**Bug Fixes**

-   Fixed an issue where custom values for the proxy ports were not fully taken into account.
-   Fixed an issue where updating a service mapping resource would result in orphaned entries in the Connectivity Proxy.
-   Fixed an issue where updating some of the configurations of the Connectivity Proxy could result in the inability to create new service mapping resources.
-   Fixed an issue where the uninstallation of the Connectivity Proxy while still having service mapping resources would only result in a partial uninstallation. Now the uninstall would fail without removing anything in such cases.
-   Fixed an issue where service channels of type *ABAP Cloud System* could not be established via Cloud Connector 2.15 towards service mappings of type *RFC*.

**Security Fixes**

-   Fixed multiple OS vulnerabilities by removing or upgrading packages on the image.
-   Fixed multiple Java vulnerabilities by upgrading dependencies to a newer version.

For more information, see [Connectivity Proxy for Kubernetes](https://help.sap.com/docs/CP_CONNECTIVITY/cca91383641e40ffbe03bdc78f00f681/e661713ef7d14373b57e3e26b0b03b86.html).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Announcement

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2022-10-20

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry

-   Neo



</td>
<td valign="top">

Cloud Connector 2.15.0 - Bug Fixes

</td>
<td valign="top">

Release of Cloud Connector version 2.15.0 provides the following bug fixes:

-   Login info content is now included in the backup.
-   Solution Manager integration via the host agent failed, when using non-ASCII characters in descriptions of access control entries \(for example, an *umlaut* like "ä"\), as the LMDB xml was generated using the wrong encoding.

    This issue has been fixed.

-   Principal propagation for RFC is now working even when not providing a dummy SNC `partnername` for load balancing connections.



</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2022-10-06

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry

-   Neo



</td>
<td valign="top">

Cloud Connector 2.15.0 - Enhancements

</td>
<td valign="top">

Release of Cloud Connector version 2.15.0 provides the following enhancements:

-   The Cloud Connector can now use SAPMachine 17 as Java runtime.

    For more information, see [JDKs](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/e23f776e4d594fdbaeeb1196d47bbcc0.html#loioe23f776e4d594fdbaeeb1196d47bbcc0__jdk).

-   The Cloud Connector supports Windows 11 and Red Hat Enterprise Linux 9 as additional OS versions.

    For more information, see [Product Availability Matrix](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/e23f776e4d594fdbaeeb1196d47bbcc0.html#loioe23f776e4d594fdbaeeb1196d47bbcc0__matrix).

-   The Cloud Connector provides a new type of *service channel* for service endpoints within Kubernetes clusters that include a deployment of the Connectivity Proxy for Kubernetes.

    For more information, see [Configure a Service Channel for a Kubernetes Cluster](https://help.sap.com/docs/CP_CONNECTIVITY/cca91383641e40ffbe03bdc78f00f681/d6d395e759374be89e0aebab83ad5a7b.html).

-   You can now forward not only business user identities, but also technical users identified by OAuth client credential tokens. On the Cloud Connector side, you can do this via enhanced configuration of the subject patterns for principal propagation.

    For more information, see [Configure a Subject Pattern for Principal Propagation](https://help.sap.com/docs/CP_CONNECTIVITY/cca91383641e40ffbe03bdc78f00f681/58803a25e5894d759e0df1c5513b41ed.html).

-   Certificate signing requests for UI certificates let you choose between 2 different key sizes: 2048 or 4096.

    For more information, see [Exchange UI Certificates in the Administration UI](https://help.sap.com/docs/CP_CONNECTIVITY/cca91383641e40ffbe03bdc78f00f681/b70bf164a6e6498b8bf1f459554609f5.html).

-   Enhanced trust store configuration capabilities allow to switch the trust store mode if needed. The default property of an empty trust store has been changed to *do not trust any certificate*.

    For more information, see [Configure Trust](https://help.sap.com/docs/CP_CONNECTIVITY/cca91383641e40ffbe03bdc78f00f681/13bfb28fd5bc4c71a82af698ee8d876f.html#loio13bfb28fd5bc4c71a82af698ee8d876f__section_TrustStore).

-   Support for SLS protocol version 3.0 when using a remote CA for principal propagation.

    For more information, see [Configure a CA Certificate for Principal Propagation](https://help.sap.com/docs/CP_CONNECTIVITY/cca91383641e40ffbe03bdc78f00f681/d0c4d5675d4f4bc78a5b7a7b8687c841.html).

-   Improved configuration for the principal type for HTTP access control entries to provide more clarity about overall impact on credential processing.

    For more information, see [Initial Configuration \(HTTP\)](https://help.sap.com/docs/CP_CONNECTIVITY/cca91383641e40ffbe03bdc78f00f681/3f974eae3cba4dafa274ec59f69daba6.html#procedure).

-   Additional administration REST APIs for ciphers and trust store are now available.

    For more information, see [Authentication and UI Settings](https://help.sap.com/docs/CP_CONNECTIVITY/cca91383641e40ffbe03bdc78f00f681/44bff8d8094e480d819c968cf527a491.html) and [Truststore CA Certificates](https://help.sap.com/docs/CP_CONNECTIVITY/cca91383641e40ffbe03bdc78f00f681/e8f309f6f28b45a9afe342a6e515f3fc.html).

-   An additional monitoring API for open connections via *service channels* is now available.

    For more information, see [Monitoring APIs](https://help.sap.com/docs/CP_CONNECTIVITY/cca91383641e40ffbe03bdc78f00f681/f6e7a7bc6af345d2a334c2427a31d294.html).

-   An additional monitoring API is available, that checks if the addressed instance has the master role. This API does not require authentication.

    For more information, see [Monitoring APIs](https://help.sap.com/docs/CP_CONNECTIVITY/cca91383641e40ffbe03bdc78f00f681/f6e7a7bc6af345d2a334c2427a31d294.html#available-apis).

-   Enhanced cipher configuration with better filtering capabilities is now available.

    For more information, see [Recommendations for Secure Setup](https://help.sap.com/docs/CP_CONNECTIVITY/cca91383641e40ffbe03bdc78f00f681/e7ea82a4bb571014a4ceb61cb7e3d31f.html#encryption-ciphers).




</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2022-10-06

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry



</td>
<td valign="top">

Destination Service - Authentication Types

</td>
<td valign="top">

For the Destination service, the new authentication type *OAuth Authorization Code* is now available.

For more information, see [OAuth Authorization Code Authentication](https://help.sap.com/docs/CP_CONNECTIVITY/cca91383641e40ffbe03bdc78f00f681/9f634f6c9cd148b7a32c4ac2b56a24c0.html).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2022-10-06

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Neo



</td>
<td valign="top">

Cloud Connector - New IP Addresses for the Neo Environment

</td>
<td valign="top">

> ### Caution:  
> Due to a planned network update, the IP addresses of the Connectivity service for the Cloud Connector will change for many regions \(Neo environment\) by **end of September 2022**.
> 
> **Required Action:** 
> 
> *If you use IP-based firewall rules*, make sure you include **both** the old and new IP addresses for each connected region that shows an **OLD** and **NEW** IP address \(Cloud Connector documentation\).
> 
> For more information, see [Prerequisites](https://help.sap.com/docs/CP_CONNECTIVITY/b865ed651e414196b39f8922db2122c7/e23f776e4d594fdbaeeb1196d47bbcc0.html#loioe23f776e4d594fdbaeeb1196d47bbcc0__neo).



</td>
<td valign="top">

Required

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Announcement

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2022-09-19

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry
-   Kyma



</td>
<td valign="top">

Transparent Proxy for Kubernetes

</td>
<td valign="top">

The Transparent Proxy for Kubernetes is now available.

The Transparent Proxy lightens the way your Kubernetes workloads connect to Internet and on-premise systems, modeled as destination configurations. It automates technical client authentication, Connectivity Proxy handshake, facilitates and significantly simplifies principal propagation, as well as general access to the target systems.

For more information, see [Transparent Proxy for Kubernetes](https://help.sap.com/docs/CP_CONNECTIVITY/cca91383641e40ffbe03bdc78f00f681/acc64ada71e34f98867f16fbcc471b5e.html).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2022-09-27

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry



</td>
<td valign="top">

Java Connector - X.509 Secrets

</td>
<td valign="top">

JCo supports the usage of X.509 secrets for communication with the Destination and Connectivity services.

For more information, see [Binding Parameters of SAP Authorization and Trust Management Service](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/3240307e513e4bceaa75e4134d337fab.html).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2022-09-08

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry



</td>
<td valign="top">

Kubernetes Connectivity Proxy - New Version

</td>
<td valign="top">

A new version \(2.7.0\) has been released for the Kubernetes Connectivity Proxy.

**New** 

-   Out-of-the-box support in the Helm chart for Istio ingress gateway as an alternative to the Nginx ingress controller.

-   Support for TCP and JDBC service mapping types - requires a not yet released version of the Cloud Connector \(2.15\).

-   The Connectivity Proxy can now be used with official support on non-Gardener clusters.


**Changed** 

-   The timeout period for which the Connectivity Proxy waits for a client to read data from its proxy endpoints is now configurable.

**Security** 

-   Fixed multiple OS vulnerabilities by removing or upgrading packages on the image

-   Fixed multiple Java vulnerabilities by upgrading dependencies to a newer version.




</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Announcement

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2022-07-28

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry

-   Neo



</td>
<td valign="top">

Java Connector 3.1.6.0 - Bug Fixes

</td>
<td valign="top">

Release of Java Connector \(JCo\) version 3.1.6.0 provides the following bug fixes:

-   When setting numeric values into fields of type `NUM` with methods `JCoRecord.setValue([name|index], char)` or `JCoRecord.setValue([name|index], char[])`, the resulting content was wrong. The field was not a correctly formatted numeric field afterwards as the passed value was left aligned instead of right aligned and hence, also no leading zero digits were added.

    > ### Note:  
    > Method `JCoRecord.setValue([name|index], String)` was not affected by this bug.

-   A `JCoRepository` metadata query might have failed when looping over multiple destinations for trying to obtain the requested RFC metadata, if a destination configuration got corrupted. Now, JCo correctly ignores such a failure and uses the next working destination for the query.
-   If a function module containing a parameter with a name starting with XML was executed, a shortdump occurred in ABAP indicated by a `JCoException` with a text similar to *\(104\) JCO\_ERROR\_SYSTEM\_FAILURE: Internal error: Unexpected status in the ABAP runtime environment. \(Remote shortdump: RUNT\_INTERNAL\_ERROR in system \[ABC|abcashost.corp|42\]\)*. The same is true if there is a structure or table parameter containing a field with such a name. This happened due to a missing special escape sequence that should be used as the standard recommends to reserve this prefix for later standard extensions.
-   When using `jco.client.serialization_format=columnBased` together with `jco.client.network=LAN` mode, it could happen that the response was not compressed by the backend, although the data size was large enough. This happened due to an invalid initialization of the RFC communication.



</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2022-07-28

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry

-   Neo



</td>
<td valign="top">

Java Connector 3.1.6.0 - Enhancements

</td>
<td valign="top">

Release of Java Connector \(JCo\) version 3.1.6.0 introduces the following enhancements:

-   `JCo.queryMetaDataSet()` was enhanced to only request the metadata from the backend for those function modules and data types that are not yet cached in the `JCoRepository`, for which the query is performed.
-   JCo was enhanced to interpret also strings consisting only of blanks as an initial value for fields of type `NUM`.



</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2022-07-28

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry



</td>
<td valign="top">

Destination Service

</td>
<td valign="top">

-   You can now skip the `user_attributes.` prefix when adding additional IdP attributes to the generated SAML assertion XMLs.

    For more information, see [User Propagation via SAML 2.0 Bearer Assertion Flow](https://help.sap.com/docs/CP_CONNECTIVITY/cca91383641e40ffbe03bdc78f00f681/3cb7b81115c44cf594e0e3631291af94.html#loio3cb7b81115c44cf594e0e3631291af94__attributes).

-   Added support for automatic token retrieval for the OAuth2 refresh token authentication type.

    For more information, see [OAuth Refresh Token Authentication](https://help.sap.com/docs/CP_CONNECTIVITY/cca91383641e40ffbe03bdc78f00f681/bff0136772d944348d982b2b427befb9.html).




</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2022-07-14

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry



</td>
<td valign="top">

Destination Service

</td>
<td valign="top">

Additional user attributes are now fetched even if the user token is sent to the Destination service via the `X-User-Token` header in the OAuth SAML Bearer and SAML Assertion flows.

For more information, see [User Propagation via SAML 2.0 Bearer Assertion Flow](https://help.sap.com/docs/CP_CONNECTIVITY/cca91383641e40ffbe03bdc78f00f681/3cb7b81115c44cf594e0e3631291af94.html#loio3cb7b81115c44cf594e0e3631291af94__attributes).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2022-07-14

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry



</td>
<td valign="top">

Destination Service

</td>
<td valign="top">

Destination Java APIs now use the login context to determine from which tenant to retrieve a destination.

For more information, see [Destination Java APIs](https://help.sap.com/docs/CP_CONNECTIVITY/cca91383641e40ffbe03bdc78f00f681/60f00ec5724e4875b51a2cadfb2364b2.html?version=Cloud).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2022-06-16

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry



</td>
<td valign="top">

Destination Service

</td>
<td valign="top">

You can update certificates with new content via the REST API.

Up to now, the only way to update a certificate was to delete it first and then create it again with the same name and the new content.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2022-06-02

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry

-   Neo



</td>
<td valign="top">

Feature Scope Description

</td>
<td valign="top">

The feature scope description for Connectivity has been integrated into the central feature scope description for SAP BTP.

For more information, see [Connectivity product page](https://help.sap.com/docs/CP_CONNECTIVITY?version=Cloud).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2022-06-02

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry

-   Neo



</td>
<td valign="top">

Cloud Connector 2.14.2 - Bug Fixes

</td>
<td valign="top">

Release of Cloud Connector version 2.14.2 provides the following bug fixes:

-   Server certificates without a subject are now accepted as valid in TLS backend communication, if a fitting *Subject Alternate Name* entry is available.
-   The Cloud Connector view in the cloud cockpit is updated with shadow instance information when intentionally switching roles from the Cloud Connector UI's high availability screen.
-   Starting a freshly extracted portable installation also works properly on Windows, if the path to the portable installation contains a space character.



</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2022-06-02

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry



</td>
<td valign="top">

Kubernetes Connectivity Proxy

</td>
<td valign="top">

Version 2.6.1 has been released for the Kubernetes Connectivity Proxy.

**New** 

You can now use the on-premise-to-cloud connectivity scenario, a.k.a. service channels. It enables RFC-based connections from the customer premise through the Cloud Connector, towards a private cloud endpoint \(not exposed to the Internet\) that serves RFC.

**Fixed** 

-   An issue with the `allowRemoteConnections` configuration property was fixed.
-   The `Upgrade` HTTP header value was not handled correctly when it was "WebSocket" instead of "websocket". This issue has been fixed.

**Security** 

-   Fixed multiple OS vulnerabilities by removing or upgrading packages on the image.
-   Fixed multiple Java vulnerabilities by upgrading dependencies to a newer version.



</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Announcement

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2022-05-19

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry



</td>
<td valign="top">

Destination Service - Certificates

</td>
<td valign="top">

-   You can create destinations using the MTA descriptor when the service key has an X.509 binding.

    For more information, see: [Create Destinations Using the MTA Descriptor](https://help.sap.com/docs/CP_CONNECTIVITY/cca91383641e40ffbe03bdc78f00f681/8aeea65eb9d64267b554f64a3db8a349.html).

-   You can update certificates in case of conflict \(already existing certificate with the same name\) when creating entities via a `config.json` during instance creation / update.

    For more information, see: [Use a Config.JSON to Create or Update a Destination Service Instance](https://help.sap.com/docs/CP_CONNECTIVITY/cca91383641e40ffbe03bdc78f00f681/6816d3caeb464f8d8b0d1b5ad0da5869.html).




</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2022-05-19

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry



</td>
<td valign="top">

Destination Service - IdP Metadata

</td>
<td valign="top">

Destination service-generated IdP metadata now include `entityID` by default.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2022-05-19

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry



</td>
<td valign="top">

Connectivity Proxy for Kubernetes \(Cloud Foundry Environment\) - Version 2.5.0

</td>
<td valign="top">

Connectivity Proxy version 2.5.0 includes the following features:

-   automatic detection of changes in configurations and secret without the need for manual restarts.
-   scalable thread pool sizes for the proxy and business data tunnel servers, both automatic and via explicit values.
-   changed the `minAvailable` configuration for the `PodDisruptionBudget` is changed from 90% to 50%.
-   multiple open source software components reported as vulnerable has been replaced.



</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Announcement

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2022-03-24

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry



</td>
<td valign="top">

Destination Service - Automatic Certificate Renewal

</td>
<td valign="top">

You can now choose automatic renewal for certificates, generated via the Destination service \(requires opt-in during generation\).

The service then gets a new certificate with the same subject as soon as the current one is about to expire. Once renewed, any subsequent attempt to fetch the certificate will result in returning the new certificate.

For more information, see [Use Destination Certificates](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/df1bb55a526942b9bee78fea2ebb3162.html).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2022-03-10

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry

-   Neo



</td>
<td valign="top">

Cloud Connector 2.14.1 - Bug Fixes

</td>
<td valign="top">

Release of Cloud Connector version 2.14.1 provides the following bug fixes:

-   If a Cloud Connector needed more than one minute to load its configuration, it failed to start the administration UI and raised exception `java.util.concurrent.ExecutionException: org.apache.catalina.LifecycleException: Failed to start component [StandardEngine[Catalina].StandardHost[localhost].StandardContext[]]` which is eventually caused by an exception `com.sap.scc.servlets.CriticalSccException: Could not get initialized configuration` - locked by another thread at `com.sap.scc.config.SccConfig.getInstance(SccConfig.java:240)` 

    This issue has been fixed.

-   When upgrading high-availability \(HA\) installations, initialization could fail after restart of one of the instances with a `NullPointerException`, resulting in a failed start of the administration UI, because older Cloud Connector masters overwrote the shadow setting with the empty value.

    The exception call stack would contain a `java.lang.NullPointerException`: while trying to invoke the method `java.io.File.equals(java.lang.Object)` of a `null` object returned from `java.io.File.getParentFile()` 

    `at com.sap.scc.util.SecTools.getValidFile(SecTools.java:131)` 

    `at com.sap.scc.util.SecTools.getValidFile(SecTools.java:114)` 

    `at com.sap.scc.audit.file.FileSystemAuditLogger.<init>(FileSystemAuditLogger.java:87)` 

    This issue has been fixed.

-   Avoid 100% CPU in one thread when using SAP JVM 8 to prevent issues that may occur due to a missing bug fix in the currently available SAP JVM 8 patch levels.
-   After a master-shadow switch, usage statistics were showing `0` for the exchanged bytes instead of the correct value.

    This issue has been fixed.

-   Under certain conditions, the master-master checker job was not started when starting the Cloud Connector. As a consequence, this situation was not recognized and not corrected.

    This issue has been fixed.




</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2022-03-10

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry

-   Neo



</td>
<td valign="top">

Cloud Connector 2.14.1 - Enhancements

</td>
<td valign="top">

Release of Cloud Connector version 2.14.1 introduces the following enhancements:

-   Systemd behavior of the daemon with regard to automatic restart and configuration of maximal threads has been improved.

-   SNC configuration with SAP Cryptographic Library is simplified by scripts included in the delivery.

    For more information, see [Initial Configuration \(RFC\)](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/f09eefe71d1e4d4484e1dd4b121585fb.html).




</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2022-03-10

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry



</td>
<td valign="top">

Destination Service - Destination Properties

</td>
<td valign="top">

You can now explicitly set the assertion recipient via a destination property for `OAuth2SAMLBearerAssertion` and `SAMLAssertion` authentication types.

For more information, see [HTTP Destinations](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/42a0e6b966924f2e902090bdf435e1b2.html).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2022-02-24

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry



</td>
<td valign="top">

Destination Service - OAuth Parameters

</td>
<td valign="top">

-   The Destination service now supports the definition of custom body parameters for the token request in OAuth flows.

-   You can send client credentials in the token request body for OAuth flows \(configurable via destination property\).

For more information, see [HTTP Destinations](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/42a0e6b966924f2e902090bdf435e1b2.html).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2022-02-10

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry

-   Neo



</td>
<td valign="top">

Java Connector 3.1.5.2 - Bug Fixes

</td>
<td valign="top">

Release of Java Connector \(JCo\) version 3.1.5.2 provides the following bug fixes:

-   Created `JCoCustomDestination` instances programmatically ignored existing `UserData` values and used a `SPACE` string \(" "\) for each modified value, which resulted in destination configuration errors, RFC logon failures, and other undesired behavior because of missing or wrong RFC logon parameters, for example, usage of the wrong logon language.

    This issue has been fixed.

    > ### Note:  
    > This was a regression bug, introduced with JCo 3.1.5.1.

-   When clearing a previously initialized nested `IMPORT/EXPORT/CHANGING` table before executing a function module, a `NullPointerException` was thrown showing a call stack similar to

    *java.lang.NullPointerException: Cannot invoke "com.sap.conn.jco.rt.DefaultTable.getRecordMetaData\(\)" because "table" is null* 

    *at com.sap.conn.jco.rt.ComplexParameter.estimateNumBytes\(ComplexParameter.java:73\)* 

    *at com.sap.conn.jco.rt.ComplexParameter.<init\>\(ComplexParameter.java:31\)* 

    *at com.sap.conn.jco.rt.ComplexTableParameter.<init\>\(ComplexTableParameter.java:15\)* 

    due to a missing null check.

    This issue has been fixed.

    > ### Note:  
    > This was a regression bug, introduced with JCo 3.1.5.1




</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2022-02-10

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry

-   Neo



</td>
<td valign="top">

Java Connector 3.1.5.1 - Enhancements

</td>
<td valign="top">

Release of Java Connector \(JCo\) version 3.1.5.1 introduces the following improvement:

-   When using `jco.client.serialization_format=columnBased` and `jco.client.network=LAN`, and the data amount to be sent is smaller than 8 KB, compression is turned off to avoid the initialization time of the LZ4 compression engine.



</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2022-01-13

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Connectivity

</td>
<td valign="top">

-   Cloud Foundry

-   Neo



</td>
<td valign="top">

Java Connector 3.1.5.1 - Bug Fixes

</td>
<td valign="top">

Release of Java Connector \(JCo\) version 3.1.5.1 provides the following bug fixes:

-   When running an application for a longer period of time, JCo could run out of connection handles, indicated by a `JCoException`, which was thrown on connect showing a call stack similar to `com.sap.conn.jco.JCoException: (106) JCO_ERROR_RESOURCE: Maximum number of RFC connections reached [32768] (remote system is [])`.

    This issue has been fixed.

-   If setting a large primitive Java double value into a parameter, a table or a structure field of type BCD, the automatically converted value was wrong due to an overflow in the JCo internal datatype conversion routines.

    This issue has been fixed.

-   When using `jco.client.serialization_format=columnBased` with parameters containing nested structures with nested tables, the communication failed with various errors at backend side in the deserializer of the fast serialization.

    This issue has been fixed.

-   When using `jco.client.pcs=2 and jco.client.serialization_format=columnBased` in a destination configuration, a `NullPointerException` was thrown on connect, due to a wrong internal initialization.

    This issue has been fixed.




</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

2022-01-13

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
</table>

