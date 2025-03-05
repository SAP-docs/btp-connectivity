<!-- loioa5667fcf42bc4148b850626884d894a9 -->

# 2017 Connectivity \(Archive\)

Archived release notes for 2017 and older.



<a name="loioa5667fcf42bc4148b850626884d894a9__section_dtk_dn3_3bb"/>

## 28 September 2017 - Connectivity


<table>
<tr>
<td valign="top">

 

</td>
<td valign="top" colspan="2">

**New**

The destination service \(Beta\) is available in the Cloud Foundry environment. See [Consuming the Destination Service](consuming-the-destination-service-7e30625.md).

</td>
</tr>
</table>



<a name="loioa5667fcf42bc4148b850626884d894a9__section_t1l_1hp_r1b"/>

## 3 August 2017 - Connectivity


<table>
<tr>
<td valign="top">

 

</td>
<td valign="top" colspan="2">

**Enhancement**

**Cloud Connector**

Release of SAP Cloud Platform Cloud Connector 2.10.1.

-   The URLs of HTTP requests can now be longer than 4096 bytes.

-   SAP Solution Manager can be integrated with one click of a button if the host agent is installed on a Cloud Connector machine. See the *Solution Management* section in [Monitoring](monitoring-6d9c937.md).

-   The limitation that only 100 subaccounts could be managed with the administration UI has been removed. See [Adding and Managing Subaccounts](adding-and-managing-subaccounts-f16df12.md).




</td>
</tr>
</table>


<table>
<tr>
<td valign="top">

 

</td>
<td valign="top" colspan="2">

**Fix**

**Cloud Connector**

-   The regression of 2.10.0 has been fixed, as principal propagation now works for RFC.

-   The cloud user store works with group names that contain a backslash \(\\\) or a slash \(/\).

-   Proxy challenges for NT LAN Manager \(NTLM\) authentication are ignored in favor of Basic authentication.

-   The back-end connection monitor works when using a JVM 7 as a runtime of Cloud Connector.




</td>
</tr>
</table>



<a name="loioa5667fcf42bc4148b850626884d894a9__section_rdq_vtw_k1b"/>

## 25 May 2017 - Connectivity


<table>
<tr>
<td valign="top">

 

</td>
<td valign="top" colspan="2">

**Enhancement**

**Cloud Connector**

Release of SAP HANA Cloud connector 2.10.0.1

-   Support of connectivity to an SAP Cloud Platform Cloud Foundry environment.

-   Support of direct connectivity with S/4HANA Cloud systems. You can open a Service Channel to an S/4HANA Cloud system in order to use Communication Scenarios requiring RFC communication to S/4HANA Cloud. See [Configure a Service Channel for RFC](configure-a-service-channel-for-rfc-18602c2.md).

-   Support of arbitrary protocols via the possibility to configure a TCP access control entry. SAP Cloud Platform Connectivity is offering a SOCKS5 proxy, with which you can address such exposed hosts. See [Using the TCP Protocol for Cloud Applications](https://help.sap.com/viewer/b865ed651e414196b39f8922db2122c7/Cloud/en-US/c2461c31761b488c828e15b71263f3fd.html "Access on-premise systems from a Neo application via TCP-based protocols, using a SOCKS5 Proxy.") :arrow_upper_right:.

-   Support for disaster recovery events of SAP Cloud Platform regions. For each subaccount you can configure a disaster recovery subaccount for a disaster region. In case of a disaster, the disaster recovery account can be switched active immediately using the exact same configuration. See [Configure a Disaster Recovery Subaccount](https://help.sap.com/viewer/b865ed651e414196b39f8922db2122c7/Cloud/en-US/39447fabeab54de6ba6bf375a6ee7299.html "Configure a subaccount as backup for disaster recovery.") :arrow_upper_right:.

-   In the access control settings you can add further constraints for RFC based communication to ABAP systems: an administrator can configure, which clients shall be exposed and can define which users should not be able to access the system via Cloud Connector. See [Configure Access Control \(RFC\)](configure-access-control-rfc-ca58689.md).

-   You can generate self-signed certificates for CA and system certificate so that you can setup demo scenarios with principal propagation without the need of using lengthy openSSL or keytool command sequences. See [Configure a CA Certificate](configure-a-ca-certificate-d0c4d56.md) and [Initial Configuration \(HTTP\)](initial-configuration-http-3f974ea.md).

-   A first set of monitoring HTTP APIs have been introduced: The state of all subaccount connections, a back-end connection monitor and a performance overview monitor. See [Monitoring APIs](monitoring-apis-f6e7a7b.md).

-   On Windows platforms, Cloud Connector 2.10 now requires Visual Studio 2013 runtime libraries.




</td>
</tr>
</table>


<table>
<tr>
<td valign="top">

 

</td>
<td valign="top" colspan="2">

**Fix**

**Cloud Connector**

-   The is no longer a bottleneck that could lengthen the processing times of requests to exposed back-end systems, after many hours under high load when using principal propagation, connection pooling, and many concurrent sessions.

-   Session management is no longer terminating early active sessions in principal propagation scenarios.

-   On Windows 10 hardware metering in virtualized environments shows hard disk and CPU data.




</td>
</tr>
</table>



<a name="loioa5667fcf42bc4148b850626884d894a9__section_enw_vpn_vz"/>

## 11 May 2017 - Connectivity


<table>
<tr>
<td valign="top">

 

</td>
<td valign="top" colspan="2">

**New**

In case the remote server supports only TLS 1.2, use this property to ensure that your scenario will work. As TLS 1.2 is more secure than TLS 1.1, the default version used by HTTP destinations, consider switching to TLS 1.2.

</td>
</tr>
</table>



<a name="loioa5667fcf42bc4148b850626884d894a9__section_rjw_1gn_jz"/>

## 30 March 2017 - Connectivity


<table>
<tr>
<td valign="top">

 

</td>
<td valign="top" colspan="2">

**Enhancement**

The release of SAP Cloud Platform Cloud Connector 2.9.1 includes the following improvements:

-   UI renovations based on collected customer feedback. The changes include rounding offs, fixes of wrong/odd behaviors, and adjustments of controls. For example, in some places tables were replaced by *sap.ui.table.Table* for better experience with many entries.

-   You can trigger the creation of a thread dump from the *Log and Trace Files* view.

-   The connection monitor graphic for idle connections was made easier to understand.




</td>
</tr>
</table>


<table>
<tr>
<td valign="top">

 

</td>
<td valign="top" colspan="2">

**Fix**

-   When configuring authentication for LDAP, the alternate host settings are no longer ignored.

-   The email configuration for alerts is processing correctly the user and password for access to the email server.

-   Some servers used to fail to process HTTP requests when using the HTTP proxy approach \([HTTP Proxy for On-Premise Connectivity](https://help.sap.com/viewer/b865ed651e414196b39f8922db2122c7/Cloud/en-US/d872cfb4801c4b54896816df4b75c75d.html "The Connectivity service provides a standard HTTP Proxy for on-premise connectivity that is accessible by any application.") :arrow_upper_right:\) on the SAP Cloud Platform side.

-   A bottleneck was removed that could lengthen the processing times of requests to exposed back-end systems under high load when using principal propagation.

-   The Cloud Connector accepts passwords that contain the '§' character when using authentication-mode password.




</td>
</tr>
</table>



<a name="loioa5667fcf42bc4148b850626884d894a9__section_cn5_gcp_fz"/>

## 16 March 2017 - Connectivity


<table>
<tr>
<td valign="top">

 

</td>
<td valign="top" colspan="2">

**Enhancement**

Update of JCo runtime for SAP Cloud Platform. See [Connectivity](connectivity-e54cc8f.md).

</td>
</tr>
</table>


<table>
<tr>
<td valign="top">

 

</td>
<td valign="top" colspan="2">

**Fix**

A`java.lang.NullPointerException` might have occurred when using a `JCoRepository` instance in roundtrip optimization mode \(will be used if the JCo property *jco.use\_repository\_roundtrip\_optimization* was set to 1 at its creation time\). The `NullPointerException` was either thrown when trying to execute a *JCoFunction* object, which has been created by such a repository instance, or even earlier when querying the meta data for a *JCoFunction*, *JCoFunctionTemplate* or a *JCoRecordMetaData* object from an AS ABAP back-end system. Only certain complex data structures and table parameter definitions were affected by this bug.

</td>
</tr>
</table>



<a name="loioa5667fcf42bc4148b850626884d894a9__archived"/>

## Older Release Notes

-   [2016](https://wiki.scn.sap.com/wiki/x/xzyKGw)

-   [2015](https://archive.sap.com/documents/docs/DOC-70320)

-   [2014](https://archive.sap.com/documents/docs/DOC-61602)

-   [2013](https://archive.sap.com/documents/docs/DOC-51895)


