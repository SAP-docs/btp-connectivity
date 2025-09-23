<!-- loioe5580c5dbb5710149e53c6013301a9f2 -->

# Connectivity Support

Support information for SAP BTP Connectivity and the Cloud Connector.



<a name="loioe5580c5dbb5710149e53c6013301a9f2__section_A6E2DDDEE3E04506AEE72DF688FB76E7"/>

## Troubleshooting

Locate the problem or error you have encountered and follow the recommended steps:

-   [Frequently Asked Questions](frequently-asked-questions-f8d6f9a.md) \(Cloud Connector\)
-   [Administration](administration-dfec06d.md) \(Cloud Connector\)
-   [Getting Support](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/5dd739823b824b539eee47b7860a00be.html "To get help, use the available support channels provided by SAP for Me.") :arrow_upper_right: \(SAP Support Portal, SAP BTP community\)



<a name="loioe5580c5dbb5710149e53c6013301a9f2__section_D1E0F3AC7BB04D73B0DFC221E152ED12"/>

## SAPSupport Information

If you cannot find a solution to your issue, collect and provide the following specific, issue-relevant information to SAP Support:

-   The Java EE code that throws an error \(if any\)
-   A screenshot of the error message for the failed operation or the error message from the `HttpResponse` body
-   Access credentials for your cloud or on-premise location

You can submit this information by creating a customer ticket in the SAP CSS system using the following components:


<table>
<tr>
<th valign="top">

Component

</th>
<th valign="top">

Purpose

</th>
</tr>
<tr>
<td valign="top" colspan="2">

**Connectivity Service**

</td>
</tr>
<tr>
<td valign="top">

BC-CP-CON

</td>
<td valign="top">

For *cloud-side* issues with **cloud to on-premise** connectivity, where:

-   The **environment is unknown** or
-   The issue is **not related** to a **specific environment**



</td>
</tr>
<tr>
<td valign="top">

BC-CP-CON-CF

</td>
<td valign="top">

For *cloud-side* issues with **cloud to on-premise** connectivity in the SAP BTP **Cloud Foundry environment**.

</td>
</tr>
<tr>
<td valign="top">

BC-CP-CON-S4HC

</td>
<td valign="top">

For *cloud-side* issues with **cloud to on-premise** connectivity in an **S/4HANA Cloud** system.

</td>
</tr>
<tr>
<td valign="top">

BC-CP-CON-K8S-PROXY

</td>
<td valign="top">

For cloud-side issues with **cloud to on-premise** connectivity in a Kubernetes cluster \(or Kubernetes-based product\), using the connectivity proxy software component.

</td>
</tr>
<tr>
<td valign="top">

BC-CP-CON-ABAP

</td>
<td valign="top">

For *cloud-side* issues with **cloud to on-premise** connectivity in the SAP BTP **ABAP environment**.

</td>
</tr>
<tr>
<td valign="top">

BC-NEO-CON

</td>
<td valign="top">

For *cloud-side* issues with **cloud to on-premise** connectivity in the SAP BTP **Neo environment**.

</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Destinations**

</td>
</tr>
<tr>
<td valign="top">

BC-CP-DEST

</td>
<td valign="top">

For issues with **destination configurations**, where:

-   The **environment is unknown** or
-   The issue is **not related** to a **specific environment**



</td>
</tr>
<tr>
<td valign="top">

BC-CP-DEST-CF

</td>
<td valign="top">

For **general issues** with the Destination service in the SAP BTP **Cloud Foundry environment**, like:

-   REST API
-   Instance creation, etc.



</td>
</tr>
<tr>
<td valign="top">

BC-CP-DEST-CF-CLIBS

</td>
<td valign="top">

For **client library issues** with the Destination service in the SAP BTP **Cloud Foundry environment**.

</td>
</tr>
<tr>
<td valign="top">

BC-CP-DEST-CF-TOOLS

</td>
<td valign="top">

For issues with the management of **destination configurations via tools** like the SAP BTP cockpit \(**Cloud Foundry environment**\).

</td>
</tr>
<tr>
<td valign="top">

BC-CP-DEST-NEO

</td>
<td valign="top">

For issues with **destination configurations** or:

-   Management tools
-   Client libraries, etc.

related to destinations in the SAP BTP **Neo environment**.

</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Cloud Connector**

</td>
</tr>
<tr>
<td valign="top">

BC-MID-SCC

</td>
<td valign="top">

For connectivity issues related to installing and configuring the **Cloud Connector**, configuring tunnels, connections, and so on.

</td>
</tr>
</table>

If you experience a more serious issue that cannot be resolved using only traces and logs, SAP Support may request access to the Cloud Connector. Follow the instructions in these SAP notes:

-   To provide access to the Administration UI via a browser, see [592085](https://me.sap.com/notes/592085).
-   To provide SSH access to the operating system of the Linux machine on which the connector is installed, see [1275351](https://me.sap.com/notes/1275351).

**Related Information**  


[Release and Maintenance Strategy](release-and-maintenance-strategy-7c3b531.md "Find information about SAP BTP Connectivity releases, versioning and upgrades.")

