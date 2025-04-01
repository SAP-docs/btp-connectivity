<!-- loiofa4adc9bd40e45dbac573fd616695446 -->

# Invoking ABAP Function Modules via RFC

Call a remote-enabled function module in an on-premise or cloud ABAP server from your application, using the RFC protocol.

Find the tasks and prerequisites that are required to consume an ABAP function module via RFC, using the Java Connector \(JCo\) API as a built-in feature of SAP BTP.



<a name="loiofa4adc9bd40e45dbac573fd616695446__tasks_rfc"/>

## Tasks


<table>
<tr>
<th valign="top">

Task Type

</th>
<th valign="top">

Task

</th>
</tr>
<tr>
<td valign="top">

![](images/CS_TASK_Admin_219b363.png)

Operator

</td>
<td valign="top">

[Prerequisites](invoking-abap-function-modules-via-rfc-fa4adc9.md#loiofa4adc9bd40e45dbac573fd616695446__config)

</td>
</tr>
<tr>
<td valign="top" rowspan="4">

![](images/CS_TASK_Admin_Dev_7c2c6d8.png)

Operator and/or Developer

</td>
<td valign="top">

[About JCo](invoking-abap-function-modules-via-rfc-fa4adc9.md#loiofa4adc9bd40e45dbac573fd616695446__jco)

</td>
</tr>
<tr>
<td valign="top">

[Installation Prerequisites for JCo Applications](invoking-abap-function-modules-via-rfc-fa4adc9.md#loiofa4adc9bd40e45dbac573fd616695446__install)

</td>
</tr>
<tr>
<td valign="top">

[Consume Connectivity via RFC](invoking-abap-function-modules-via-rfc-fa4adc9.md#loiofa4adc9bd40e45dbac573fd616695446__consume)

</td>
</tr>
<tr>
<td valign="top">

[Restrictions](invoking-abap-function-modules-via-rfc-fa4adc9.md#loiofa4adc9bd40e45dbac573fd616695446__restrict)

</td>
</tr>
</table>



<a name="loiofa4adc9bd40e45dbac573fd616695446__config"/>

## Prerequisites

![](images/CS_TASK_Admin_219b363.png)

Before you can use RFC communication for an SAP BTP application, you must configure:

-   A destination on SAP BTP to use RFC.

    For more information, see [RFC Destinations](rfc-destinations-238d027.md).

-   \(Only for on-premise backend systems\) RFC connectivity between a backend system and the application. To do this, you must install the [Cloud Connector](cloud-connector-e6c7616.md) in your internal network and configure it to expose a remote-enabled function module in an ABAP system.

    For more information, see [Initial Configuration \(RFC\)](initial-configuration-rfc-f09eefe.md) and [Configure Access Control \(RFC\)](configure-access-control-rfc-ca58689.md).


Back to [Tasks](invoking-abap-function-modules-via-rfc-fa4adc9.md#loiofa4adc9bd40e45dbac573fd616695446__tasks_rfc)



<a name="loiofa4adc9bd40e45dbac573fd616695446__jco"/>

## About JCo

![](images/CS_TASK_Admin_Dev_7c2c6d8.png)

To learn in detail about the SAP JCo API, see the JCo 3.0 documentation on[SAP Support Portal](https://support.sap.com/en/product/connectors/jco.html#section_1355144687).

> ### Note:  
> Some sections of this documentation are not applicable to SAP BTP:
> 
> -   **Architecture**: CPIC is only used in the last mile from your Cloud Connector to an *on-premise* ABAP backend. From SAP BTP to the Cloud Connector, TLS-protected communication is used.
> -   **Installation**: SAP BTP runtimes already include all required artifacts.
> -   **Customizing and Integration**: On SAP BTP, the integration is already done by the runtime. You can concentrate on your business application logic.
> -   **Server Programming**: The programming model of JCo on SAP BTP does not include server-side RFC communication.
> -   **IDoc Support for External Java Applications**: Currently, there is no IDocLibrary for JCo available on SAP BTP

Back to [Tasks](invoking-abap-function-modules-via-rfc-fa4adc9.md#loiofa4adc9bd40e45dbac573fd616695446__tasks_rfc)



<a name="loiofa4adc9bd40e45dbac573fd616695446__install"/>

## Installation Prerequisites for JCo Applications

![](images/CS_TASK_Admin_Dev_7c2c6d8.png)

-   For connections to an *on-premise* ABAP backend, you have downloaded the Cloud Connector installation archive from [SAP Development Tools for Eclipse](https://tools.hana.ondemand.com/#cloud) and connected the Cloud Connector to your subaccount.
-   You have downloaded and set up your Eclipse IDE and the [Eclipse Tools for Cloud Foundry](https://projects.eclipse.org/projects/ecd.cft).
-   You have downloaded the Cloud Foundry CLI, see [Tools](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/abcae5b568c94e5391a74d15f5db9213.html "SAP BTP includes many tools to help you develop and manage applications, and connect them to your on-premise systems.") :arrow_upper_right:.

Back to [Tasks](invoking-abap-function-modules-via-rfc-fa4adc9.md#loiofa4adc9bd40e45dbac573fd616695446__tasks_rfc)



<a name="loiofa4adc9bd40e45dbac573fd616695446__consume"/>

## Consuming Connectivity via RFC

![](images/CS_TASK_Admin_Dev_7c2c6d8.png)

You can call a service from a fenced customer network using an application that consumes a remote-enabled function module.

Invoking function modules via RFC is enabled by a JCo API that is comparable to the one available in SAP NetWeaver Application Server Java \(version 7.10\), and in JCo standalone 3.0. If you are an experienced JCo developer, you can easily develop a Web application using JCo: you simply consume the APIs like you do in other Java environments. Restrictions that apply in the cloud environment are mentioned in the **Restrictions** section below.

Find a sample Web application in [Invoke ABAP Function Modules in On-Premise ABAP Systems](invoke-abap-function-modules-in-on-premise-abap-systems-bfcb54c.md). 

Back to [Tasks](invoking-abap-function-modules-via-rfc-fa4adc9.md#loiofa4adc9bd40e45dbac573fd616695446__tasks_rfc)



<a name="loiofa4adc9bd40e45dbac573fd616695446__restrict"/>

## Restrictions

![](images/CS_TASK_Admin_Dev_7c2c6d8.png)

-   The supported **runtime environment** is SAP Java Buildpack as of version 1.8.0.

    > ### Note:  
    > You must use the Tomcat or TomEE runtime offered by the build pack to make JCo work correctly. You cannot bring a container of your own.

-   Your application must not bundle the JCo 3.1 standalone Java archives nor the native library. JCo is already embedded properly in the build pack.
-   **JCoServer** functionality cannot be used within SAP BTP.
-   **Environment embedding**, such as offered by JCo standalone 3.1, is not possible. This is, however, similar to SAP NetWeaver AS Java.
-   A **stateful sequence of function module invocations** must be done in a single HTTP request/response cycle.
-   **Logon authentication** only supports user/password credentials \(basic authentication\) and principal propagation. See [Authentication to the On-Premise System](authentication-to-the-on-premise-system-67b0b94.md).

-   The supported set of **configuration properties** is restricted. For details, see [RFC Destinations](rfc-destinations-238d027.md).

Back to [Tasks](invoking-abap-function-modules-via-rfc-fa4adc9.md#loiofa4adc9bd40e45dbac573fd616695446__tasks_rfc)



<a name="loiofa4adc9bd40e45dbac573fd616695446__section_xpc_xgv_wqb"/>

## Related Information

-   [Use Cases](use-cases-effd6be.md)
-   [Developing Java in the Cloud Foundry Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/a3f90069d6cd41da82f34a6123d82ce6.html "Find selected information for Java development on SAP BTP, Cloud Foundry and references to more detailed sources.") :arrow_upper_right:
-   [SAP Java Connector](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/3cee866c27ec4492b789b10c5d52d94b.html "You can use the SAP Java Connector through the SAP Java buildpacks.") :arrow_upper_right:

