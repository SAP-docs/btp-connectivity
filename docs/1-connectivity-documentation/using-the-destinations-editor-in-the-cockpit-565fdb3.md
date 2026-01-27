<!-- loio565fdb3dd19d4cda80864341dc5a0451 -->

# Using the Destinations Editor in the Cockpit

Use the *Destinations* editor in the SAP BTP cockpit to configure HTTP, RFC, LDAP, TCP, or MAIL destinations.

The *Destinations* editor lets you manage destinations on subaccount or service instance level.

You can use a destination to:

-   Connect your application to the **Internet**, to an **on-premise system**, or using a **PrivateLink** connection.
-   Send and retrieve e-mails, configuring a mail destination.
-   Create a destination for subscription-based scenarios, pointing to your service instance. For more information, see [Destinations Pointing to Service Instances](destinations-pointing-to-service-instances-685f383.md).



<a name="loio565fdb3dd19d4cda80864341dc5a0451__section_N10039_N10011_N10001"/>

## Prerequisites

1.  You are logged into the SAP BTP cockpit.
2.  You have the required authorizations. See [User Roles](user-roles-b922fc8.md).
3.  Make sure the following is fulfilled:

    -   Subscription level: the SaaS application has allowed users \(of the subscribed consumer\) to manage destinations and you have the roles defined by the SaaS application to perform the desired operation.
    -   Service instance level: you must have created a Destination service instance, see [Create and Bind a Destination Service Instance](create-and-bind-a-destination-service-instance-9fdad3c.md).
    -   Subaccount level: no specific prerequisites.

    For more information, see [Access the Destinations Editor](access-the-destinations-editor-82ca377.md).




<a name="loio565fdb3dd19d4cda80864341dc5a0451__section_kw2_whr_jkb"/>

## Restrictions

-   A destination name must be unique for the current application. It must contain only alphanumeric characters, underscores, and dashes. The maximum length is 200 characters.
-   The currently supported destination types are **HTTP**, **RFC**, **LDAP**, **TCP**, and **MAIL**.

    -   [HTTP Destinations](http-destinations-42a0e6b.md): provide data communication via the HTTP protocol and are used for both Internet and on-premise connections.
    -   [RFC Destinations](rfc-destinations-238d027.md): make connections to ABAP on-premise systems via RFC protocol using the Java Connector \(JCo\) as API.
    -   [LDAP Destinations](ldap-destinations-8cb290f.md): connect to to a local LDAP server for user management.
    -   [TCP Destinations](tcp-destinations-f6d753f.md): use the TCP protocol for communication.
    -   [MAIL Destinations](mail-destinations-e3de817.md): specify an e-mail provider for sending and retrieving e-mails.




<a name="loio565fdb3dd19d4cda80864341dc5a0451__section_gzw_md1_g4b"/>

## Tasks

-   [Create Destinations from Scratch](create-destinations-from-scratch-5eba623.md)
-   [Create Destinations from a Template](create-destinations-from-a-template-ef56ea0.md)
-   [Check the Availability of a Destination](check-the-availability-of-a-destination-71ea3cc.md)
-   [Duplicate Destinations](duplicate-destinations-b80786e.md)
-   [Edit and Delete Destinations](edit-and-delete-destinations-372dee2.md)
-   [Manage Destination Certificates](manage-destination-certificates-df1bb55.md)
-   [Export Destinations](export-destinations-707b49e.md)

**Related Information**  


[Destination Examples](destination-examples-3a2d575.md "Find configuration examples for HTTP and RFC destinations in SAP BTP, using different authentication types.")

