<!-- loiodaca64dacc6148fcb5c70ed86082ef91 -->

# What Is SAP BTP Connectivity?

Use SAP BTP Connectivity for your application in the multi-cloud foundation: available services, connectivity scenarios, user roles.

> ### Note:  
> You can use SAP BTP Connectivity for the multi-cloud foundation and for the Neo environment. This documentation refers to SAP BTP, multi-cloud foundation. If you are looking for information about the Neo environment, see [Connectivity for the Neo Environment](https://help.sap.com/viewer/b865ed651e414196b39f8922db2122c7/Cloud/en-US/5ceb84290d5644638f73d40fde3af5d0.html).

SAP BTP Connectivity lets you connect your SAP BTP applications to other Internet resources, or to your on-premise systems running in isolated networks. It provides an extensive set of features to choose different connection types and authentication methods. Using its configuration options, you can tailor access exactly to your needs.

> ### Note:  
> The on-premise use cases described in this guide are also applicable to virtual private cloud \(VPC\) environments.



<a name="loiodaca64dacc6148fcb5c70ed86082ef91__content"/>

## Content

Hover over the elements for a description. Click an element for more information.

![](images/Image_Map_Cloud_Foundry_TOPIC_fa57f92.png)



<a name="loiodaca64dacc6148fcb5c70ed86082ef91__services"/>

## Features

SAP BTP Connectivity provides two services for the multi-cloud foundation, the Connectivity service and the Destination service.

The Destination service and the Connectivity service together provide virtually the same functionality that is included in the Connectivity service of the Neo environment.

In the multi-cloud foundation however, this functionality is split into two separate services:

-   The **Connectivity** service provides a connectivity proxy that you can use to access on-premise resources.
-   Using the **Destination** service, you can retrieve and store the technical information about the target resource \(destination\) that you need to connect your application to a remote service or system.

You can use both services together as well as separately, depending on the needs of your specific scenario.

Back to [Content](what-is-sap-btp-connectivity-daca64d.md#loiodaca64dacc6148fcb5c70ed86082ef91__content)



<a name="loiodaca64dacc6148fcb5c70ed86082ef91__cases"/>

## Use Cases

-   Use the **Connectivity** service to connect your application or an SAP HANA database to *on-premise systems*:
    -   Set up on-premise communication via HTTP or RFC for your cloud application.

    -   Use a service channel to connect to an SAP HANA database on SAP BTP from your on-premise system, see [Configure a Service Channel for an SAP HANA Database](https://help.sap.com/viewer/b865ed651e414196b39f8922db2122c7/Cloud/en-US/3dc28b456bb64fad89084d2d10af602c.html "Using Cloud Connector service channels, you can establish a connection to an SAP HANA database in SAP BTP that is not directly exposed to external access.") :arrow_upper_right:.

-   Use the **Destination** service:
    -   To retrieve technical information about destinations that are required to consume the Connectivity service \(optional\), *or*
    -   To provide destination information for connecting your cloud application to any other *Web application* \(remote service\). This scenario does not require the Connectivity service.


Back to [Content](what-is-sap-btp-connectivity-daca64d.md#loiodaca64dacc6148fcb5c70ed86082ef91__content)



<a name="loiodaca64dacc6148fcb5c70ed86082ef91__roles"/>

## User Roles

> ### Note:  
> This section refers to SAP BTP, Cloud Foundry environment. For information on role assignment in the Kyma environment, see [Assign Roles in the Kyma Environment](https://help.sap.com/docs/btp/sap-business-technology-platform/assign-roles-in-kyma-environment).

In this document, we refer to different types of user roles – *responsibility roles* and *technical roles*. Responsibility roles describe the required user groups and their general tasks in the end-to-end setup process. Configuring technical roles, you can control access to the dedicated cloud management tools by assigning specific permissions to users.

[Responsibility Roles](what-is-sap-btp-connectivity-daca64d.md#loiodaca64dacc6148fcb5c70ed86082ef91__responsibility)

[Technical Roles](what-is-sap-btp-connectivity-daca64d.md#loiodaca64dacc6148fcb5c70ed86082ef91__technical)

**Responsibility Roles**

The end-to-end use of the Connectivity service and the Destination service requires these **user groups**:

-   *Application operators* - are responsible for productive deployment and operation of an application on SAP BTP. Application operators are also responsible for configuring the remote connections \(destination and trust management\) that an application might need, see [Administration](administration-78198e8.md).
-   *Application developers* - develop a connectivity-enabled SAP BTP application by consuming the Connectivity service and/or the Destination service, see [Developing Applications](developing-applications-2cd45a1.md).
-   *IT administrators* - set up the connectivity to SAP BTP in your on-premise network, using the [Cloud Connector](cloud-connector-e6c7616.md).

Some procedures on the SAP BTP can be done by developers as well as by application operators. Others may include a mix of development and operation tasks. These procedures are labeled using icons for the respective task type.


<table>
<tr>
<th valign="top" colspan="3">

Task Types

</th>
</tr>
<tr>
<td valign="top">

![](images/CS_TASK_Admin_219b363.png) Operator

</td>
<td valign="top">

![](images/CS_TASK_Dev_a4c82d5.png) Developer

</td>
<td valign="top">

![](images/CS_TASK_Admin_Dev_7c2c6d8.png) Operator and/or Developer

</td>
</tr>
</table>

**Technical Roles**

To perform connectivity tasks in the Cloud Foundry environment, the following **technical roles** apply:

The Cloud Foundry environment provides **dedicated roles** for specific operations. They can be assigned to **custom role collections**, but some of them are also available in **default role collections**.

[Technical Connectivity Roles and Operations](what-is-sap-btp-connectivity-daca64d.md#loiodaca64dacc6148fcb5c70ed86082ef91__table_tech_roles_setB)

[Default Role Collections](what-is-sap-btp-connectivity-daca64d.md#loiodaca64dacc6148fcb5c70ed86082ef91__table_default_role_collections_setB)

> ### Note:  
> To see the Destination editor on subaccount level, you must have at least the *Destination Viewer* role, or both the *Destination Configuration Viewer* and the *Destination Certificate Viewer* roles.
> 
> For the Destination editor on service instance level, the corresponding roles apply: You need at least the *Destination Viewer Instance* role, or both the *Destination Configuration Instance Viewer* and the *Destination Certificate Instance Viewer* roles.

**Technical Connectivity Roles and Operations**


<table>
<tr>
<th valign="top">

Level

</th>
<th valign="top">

Operation \(SAP BTP Cockpit or Cloud Connector\)

</th>
<th valign="top">

Role

</th>
</tr>
<tr>
<td valign="top" rowspan="7">

**Subaccount**

</td>
<td valign="top">

**Connect a Cloud Connector** to a subaccount \(Cloud Connector\)

</td>
<td valign="top">

Cloud Connector Administrator

</td>
</tr>
<tr>
<td valign="top">

**Manage destinations** \(all CRUD operations\) on subaccount level \(cockpit\)

> ### Note:  
> CRUD \(*Create, Read, Update, Delete*\) operations include actions like create destinations, display \(view\) destinations, edit destinations, and delete destinations.
> 
> For more information, see [Managing Destinations](managing-destinations-84e45e0.md).



</td>
<td valign="top">

One of these roles:

-   Destination Administrator
-   Destination Configuration Administrator



</td>
</tr>
<tr>
<td valign="top">

**View destinations** \(read operations\) on subaccount level \(cockpit\)

</td>
<td valign="top">

One of these roles:

-   Destination Viewer
-   Destination Configuration Viewer



</td>
</tr>
<tr>
<td valign="top">

**Manage certificates** \(all CRUD operations\) on subaccount level \(cockpit\)

> ### Note:  
> CRUD \(*Create, Read, Update, Delete*\) operations include actions like create destinations, display \(view\) destinations, edit destinations, and delete destinations.
> 
> For more information, see [Managing Destinations](managing-destinations-84e45e0.md).



</td>
<td valign="top">

One of these roles:

-   Destination Administrator
-   Destination Certificate Administrator



</td>
</tr>
<tr>
<td valign="top">

**View certificates** \(read operations\) on subaccount level \(cockpit\)

</td>
<td valign="top">

One of these roles:

-   Destination Viewer
-   Destination Certificate Viewer



</td>
</tr>
<tr>
<td valign="top">

**Generate or renew the subaccount key pair** for trust management \(cockpit\)

</td>
<td valign="top">

One of these roles:

-   Destination Administrator
-   Destination Subaccount Trust Administrator



</td>
</tr>
<tr>
<td valign="top">

**Download the subaccount key pair** for trust management \(cockpit\)

</td>
<td valign="top">

One of these roles:

-   Destination Viewer
-   Destination Subaccount Trust Viewer



</td>
</tr>
<tr>
<td valign="top">

**Subaccount**

</td>
<td valign="top">

**View Cloud Connectors** connected to a subaccount \(cockpit\)

</td>
<td valign="top">

A role containing the permission `readSCCTunnels`, for example, the predefined role `Cloud Connector Administrator`.

</td>
</tr>
<tr>
<td valign="top" rowspan="4">

**Service instance**

</td>
<td valign="top">

**Manage destinations** \(all CRUD operations\) on service instance level \(cockpit\)

> ### Note:  
> CRUD \(*Create, Read, Update, Delete*\) operations include actions like create destinations, display \(view\) destinations, edit destinations, and delete destinations.
> 
> For more information, see [Managing Destinations](managing-destinations-84e45e0.md).



</td>
<td valign="top">

One of these roles:

-   Destination Administrator
-   Destination Configuration Administrator
-   Destination Administrator Instance
-   Destination Configuration Instance Administrator

***plus*** one of these roles:

-   *Org Manager*
-   *Space Manager*
-   *Space Developer* 

See [User and Member Management](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/cc1c676b43904066abb2a4838cbd0c37.html "On SAP BTP, user management takes place at all levels from global account to environment. There are different types of users, such as depending on their roles in the company.") :arrow_upper_right:.

</td>
</tr>
<tr>
<td valign="top">

**View destinations** \(read operations\) on service instance level \(cockpit\)

</td>
<td valign="top">

One of these roles:

-   Destination Viewer
-   Destination Configuration Viewer
-   Destination Viewer Instance
-   Destination Configuration Instance Viewer

***plus*** one of these roles:

-   *Org Manager*
-   *Space Manager*
-   *Space Developer* 

See [User and Member Management](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/cc1c676b43904066abb2a4838cbd0c37.html "On SAP BTP, user management takes place at all levels from global account to environment. There are different types of users, such as depending on their roles in the company.") :arrow_upper_right:.

</td>
</tr>
<tr>
<td valign="top">

**Manage certificates** \(all CRUD operations\) on service instance level \(cockpit\)

> ### Note:  
> CRUD \(*Create, Read, Update, Delete*\) operations include actions like create destinations, display \(view\) destinations, edit destinations, and delete destinations.
> 
> For more information, see [Managing Destinations](managing-destinations-84e45e0.md).



</td>
<td valign="top">

One of these roles:

-   Destination Administrator
-   Destination Certificate Administrator
-   Destination Administrator Instance
-   Destination Certificate Instance Administrator

***plus*** one of these roles:

-   *Org Manager*
-   *Space Manager*
-   *Space Developer* 

See [User and Member Management](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/cc1c676b43904066abb2a4838cbd0c37.html "On SAP BTP, user management takes place at all levels from global account to environment. There are different types of users, such as depending on their roles in the company.") :arrow_upper_right:.

</td>
</tr>
<tr>
<td valign="top">

**View certificates** \(read operations\) on service instance level \(cockpit\)

</td>
<td valign="top">

One of these roles:

-   Destination Viewer
-   Destination Certificate Viewer
-   Destination Viewer Instance
-   Destination Certificate Instance Viewer

***plus*** one of these roles:

-   *Org Manager*
-   *Space Manager*
-   *Space Developer* 

See [User and Member Management](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/cc1c676b43904066abb2a4838cbd0c37.html "On SAP BTP, user management takes place at all levels from global account to environment. There are different types of users, such as depending on their roles in the company.") :arrow_upper_right:.

</td>
</tr>
</table>

**Default Role Collections**


<table>
<tr>
<th valign="top">

Default Role Collection

</th>
<th valign="top">

Connectivity Roles Included

</th>
</tr>
<tr>
<td valign="top">

Subaccount Administrator

</td>
<td valign="top">

-   Cloud Connector Administrator
-   Destination Administrator



</td>
</tr>
<tr>
<td valign="top">

Subaccount Viewer

</td>
<td valign="top">

-   Cloud Connector Auditor
-   Destination Viewer



</td>
</tr>
<tr>
<td valign="top">

Cloud Connector Administrator

</td>
<td valign="top">

Cloud Connector Administrator

</td>
</tr>
<tr>
<td valign="top">

Destination Administrator

</td>
<td valign="top">

Destination Administrator

</td>
</tr>
<tr>
<td valign="top">

Connectivity and Destination Administrator

</td>
<td valign="top">

-   Cloud Connector Administrator
-   Destination Administrator



</td>
</tr>
</table>

> ### Note:  
> You can access subaccount-level destinations in two ways:
> 
> -   Via the cockpit \(as described above\)
> -   Via the Destination service [REST API](https://api.sap.com/api/SAP_CP_CF_Connectivity_Destination/resource)
> 
> If a user has access to the Destination service REST API \(via service instance binding credentials or a service key\), he has full access to the destination and certificate configurations managed by that instance of the Destination service.
> 
> For more information, see [About Roles in the Cloud Foundry Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/09076385086b4da3bd1808d5ef572862.html) and check the activity *Instantiate and bind services to apps* in the linked Cloud Foundry documentation \(*docs.cloudfoundry.org*\).
> 
> Additionally, applications have access to the REST API of the Destination service instance they are bound to.

Back to [Technical Roles](what-is-sap-btp-connectivity-daca64d.md#loiodaca64dacc6148fcb5c70ed86082ef91__technical)

Back to [User Roles](what-is-sap-btp-connectivity-daca64d.md#loiodaca64dacc6148fcb5c70ed86082ef91__roles)

Back to [Content](what-is-sap-btp-connectivity-daca64d.md#loiodaca64dacc6148fcb5c70ed86082ef91__content)

**Related Information**  


[What's New for Connectivity](what-s-new-for-connectivity-7882854.md "Find the latest features, enhancements and bug fixes for SAP BTP Connectivity .")

[Administration](administration-78198e8.md "Manage destinations and authentication for SAP BTP applications.")

[Developing Applications](developing-applications-2cd45a1.md "Consume the Connectivity service and the Destination service from an application.")

[Security](security-7b60f4c.md "Find an overview of recommended security measures for SAP BTP Connectivity.")

[Monitoring and Troubleshooting](monitoring-and-troubleshooting-27ab9fa.md "Find information on monitoring and troubleshooting for SAP BTP Connectivity.")

[Security Administration: Managing Authentication and Authorization](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/1ff47b2d980e43a6b2ce294352333708.html "This section describes the tasks of administrators of SAP BTP. Administrators ensure user authentication and assign authorization information to users and user groups.") :arrow_upper_right:

