<!-- loio9b3cc683cca944bd98346bef3181630e -->

# Create RFC Destinations

How to create RFC destinations in the *Destinations* editor \(SAP BTP cockpit\).



## Prerequisites

You have logged into the cockpit and opened the *Destinations* editor.

> ### Note:  
> The on-premise use cases described in this guide are also applicable to virtual private cloud \(VPC\) environments.



<a name="loio9b3cc683cca944bd98346bef3181630e__steps_j4g_jfb_pn"/>

## Procedure

1.  Choose *Create Destination*.

    > ### Note:  
    > In section **Destination Configuration**, do not change the default tab *Blank Template*. Tab *Service Instance* only applies for HTTP destinations.

2.  Enter a destination name.

3.  From the *<Type\>* dropdown menu, choose `RFC`.

4.  The *<Description\>* field is optional.

5.  From the *<Proxy Type\>* dropdown box, select `Internet` or `OnPremise`, depending on the connection you need to provide for your application.

    > ### Note:  
    > Using *<Proxy Type\>* `Internet` , you can connect your application to any target service that is exposed to the Internet. *<Proxy Type\>* `OnPremise` requires the Cloud Connector to access resources within your on-premise network.

6.  Enter credentials for *<User\>* and *<Password\>*.

7.  \(Optional\) Enter an *<Alias User\>* name. See also [User Logon Properties](user-logon-properties-8b1e1c3.md).

8.  \(Optional\) Enter credentials for *<Repository User\>* and *<Repository Password\>*, if you want to use a different user for repository lookups. See also [Repository Configuration](repository-configuration-4c4b83b.md).

9.  \(Optional\) If you are using more than one Cloud Connector for your subaccount, you must enter the *<Location ID\>* of the target Cloud Connector.

    See also [Adding and Managing Subaccounts](adding-and-managing-subaccounts-f16df12.md) \(section **Procedure**, step 4\).

10. Depending on the proxy type of your RFC destination, specify at least the following JCo properties in section *Additional Properties*.

    1.  In the *Additional Properties* panel, choose *New Property*.

    2.  Add each required property from the dropdown menu and specify its value:



    <table>
    <tr>
    <th valign="top">

    Proxy Type
    
    </th>
    <th valign="top">

    Property
    
    </th>
    <th valign="top">

    Description
    
    </th>
    </tr>
    <tr>
    <td valign="top" rowspan="9">
    
    **OnPremise**
    
    </td>
    <td valign="top" colspan="2">
    
    **Load Balancing Connections**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `jco.client.r3name`
    
    </td>
    <td valign="top">
    
    Three-letter system ID of your backend ABAP system \(as configured in the Cloud Connector\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `jco.client.mshost`
    
    </td>
    <td valign="top">
    
    Message server host \(as configured in the Cloud Connector\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `jco.client.group`
    
    </td>
    <td valign="top">
    
    \(Optional\) The group of application servers that is used \(logon group\). If not specified, the group `PUBLIC` is used.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `jco.client.client`
    
    </td>
    <td valign="top">
    
    Three-digit ABAP client number \(defines the client of the target ABAP system\).
    
    </td>
    </tr>
    <tr>
    <td valign="top" colspan="2">
    
    **Direct Connections**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `jco.client.ashost`
    
    </td>
    <td valign="top">
    
    Application server name of your target ABAP system \(as configured in the Cloud Connector\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `jco.client.sysnr`
    
    </td>
    <td valign="top">
    
    Instance number of the application server \(as configured in the Cloud Connector\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `jco.client.client`
    
    </td>
    <td valign="top">
    
    Three-digit ABAP client number \(defines the client of the target ABAP system\).
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="3">
    
    **Internet**
    
    </td>
    <td valign="top">
    
    `jco.client.wshost`
    
    </td>
    <td valign="top">
    
    WebSocket RFC server host on which the target ABAP system is running. The system must be exposed to the Internet.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `jco.client.wsport`
    
    </td>
    <td valign="top">
    
    WebSocket RFC server port on which the target ABAP system is listening.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `jco.client.client`
    
    </td>
    <td valign="top">
    
    Three-digit ABAP client number \(defines the client of the target ABAP system\).
    
    </td>
    </tr>
    </table>
    
    For a detailed description of RFC-specific properties \(JCo properties\), see [RFC Destinations](rfc-destinations-238d027.md).

11. Press *Save*.


**Related Information**  


[Edit and Delete Destinations](edit-and-delete-destinations-372dee2.md "How to edit and delete destinations in the Destinations editor (SAP BTP cockpit).")

[Destination Examples](destination-examples-3a2d575.md "Find configuration examples for HTTP and RFC destinations in SAP BTP, using different authentication types.")

[Cloud Connector](cloud-connector-e6c7616.md "Learn more about the Cloud Connector: features, scenarios and setup.")

