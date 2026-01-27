<!-- loio82ca377549c5421a8199013ea5f0facc -->

# Access the Destinations Editor

Access the Destinations editor in the SAP BTP cockpit to create and manage destinations.

You can edit destinations at three different levels:

-   Subaccount level

-   Service instance level
-   Subscription level

On *subaccount* level, you can specify a destination for the entire subaccount, defining the used communication protocol and more properties, like authentication method, proxy type and URL.

On *service instance* level, you can reuse this destination for a specific space and adjust the URL if required. You can also create a new destination only on service instance level that is specific to the selected service instance and its assigned applications.

On *subscription* level, you specify a destination only for an SaaS application you are subscribed to \(if the SaaS application has allowed this\).



<a name="loio82ca377549c5421a8199013ea5f0facc__section_t2p_cf5_j2b"/>

## Prerequisites

-   You are logged into the SAP BTP cockpit.
-   You have the required authorizations. See [User Roles](user-roles-b922fc8.md).



<a name="loio82ca377549c5421a8199013ea5f0facc__section_fwj_2f5_j2b"/>

## Procedure

**Access on Subaccount Level**

1.  In the cockpit, select your *Global Account* and your subaccount name from the *Subaccount* menu in the breadcrumbs.
2.  From the left-side panel, choose *Connectivity* \> *Destinations*.
3.  The Destinations editor will load. The right panel lets you select the *Context Level* in which to work. The *Subaccount Level* is the default selection.

**Access on Service Instance Level**

> ### Note:  
> To perform these steps, you must have a created destination service instance.
> 
> For more information, see [Create and Bind a Destination Service Instance](create-and-bind-a-destination-service-instance-9fdad3c.md).

1.  In the cockpit, choose your *Global Account* from the *Region Overview* and select a *Subaccount*.

    > ### Caution:  
    > The *Cloud Foundry Organization* must be enabled.

2.  From the left-side menu, choose *Spaces* and select a space name.
3.  From the left-side menu, choose *Services* \> *Service Instances*.
4.  Select a service instance and choose *Destinations* from the left-side panel.

**Access on Subscription Level**

1.  In the cockpit, select your global account and your subaccount name from the subaccount menu in the breadcrumbs.
2.  From the left-side panel, choose *Connectivity* \> *Destinations*.
3.  The Destinations editor will load. The right panel lets you select the *Context Level* in which to work. Under *Subscriptions* you will see all SaaS applications that support consumer management of destinations and the permissions your user has.

    > ### Note:  
    > The needed permissions for each subscription level are defined by the respective SaaS application.


> ### Note:  
> If you are developing an SaaS application and want to support consumer management of destinations, see [Accessing and Managing Destination Service Configurations on Subscription Level](accessing-and-managing-destination-service-configurations-on-subscription-level-e23c8de.md).

**Related Information**  


[Create Destinations from Scratch](create-destinations-from-scratch-5eba623.md "Use the Destinations editor in the SAP BTP cockpit to configure destinations from scratch.")

[Create Destinations from a Template](create-destinations-from-a-template-ef56ea0.md "Use a template to configure destinations with scenario-specific input data in the SAP BTP cockpit.")

[Check the Availability of a Destination](check-the-availability-of-a-destination-71ea3cc.md "How to check the availability of a destination in the Destinations editor (SAP BTP cockpit).")

[Duplicate Destinations](duplicate-destinations-b80786e.md "How to duplicate destinations in the Destinations editor (SAP BTP cockpit).")

[Edit and Delete Destinations](edit-and-delete-destinations-372dee2.md "How to edit and delete destinations in the Destinations editor (SAP BTP cockpit).")

[Manage Destination Certificates](manage-destination-certificates-df1bb55.md "To use certificate-based authentication methods for a specific destination, you can maintain the corresponding certificates (X.509 client certificates, trusted certificates, CA certificates, trust store and key store certificates) in the Destination Certificates UI (SAP BTP cockpit).")

[Import Destinations](import-destinations-91ee9db.md "How to import destinations in the Destinations editor (SAP BTP cockpit).")

[Export Destinations](export-destinations-707b49e.md "Export destinations from the Destinations editor in the SAP BTP cockpit to backup or reuse a destination configuration.")

