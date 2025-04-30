<!-- loio565fdb3dd19d4cda80864341dc5a0451 -->

# Using the Destinations Editor in the Cockpit

Use the *Destinations* editor in the SAP BTP cockpit to configure HTTP, RFC or mail destinations.

The *Destinations* editor lets you manage destinations on subaccount or service instance level.

You can use a destination to:

-   Connect your application to the **Internet** \(via HTTP\), as well as to an **on-premise system** \(via HTTP or RFC\).
-   Send and retrieve e-mails, configuring a mail destination.
-   Create a destination for subscription-based scenarios, pointing to your service instance. For more information, see [Destinations Pointing to Service Instances](destinations-pointing-to-service-instances-685f383.md).



<a name="loio565fdb3dd19d4cda80864341dc5a0451__section_N10039_N10011_N10001"/>

## Prerequisites

1.  You are logged into the SAP BTP cockpit.
2.  You have the required authorizations. See [User Roles](getting-started-daca64d.md#loiodaca64dacc6148fcb5c70ed86082ef91__roles).
3.  Make sure the following is fulfilled:

    -   Service instance level – you must have created a Destination service instance, see [Create and Bind a Destination Service Instance](create-and-bind-a-destination-service-instance-9fdad3c.md).
    -   Subaccount level – no specific prerequisites.

    For more information, see [Access the Destinations Editor](access-the-destinations-editor-82ca377.md).




<a name="loio565fdb3dd19d4cda80864341dc5a0451__section_kw2_whr_jkb"/>

## Restrictions

-   A destination name must be unique for the current application. It must contain only alphanumeric characters, underscores, and dashes. The maximum length is 200 characters.
-   The currently supported destination types are **HTTP**, **RFC** and **MAIL**.

    -   [HTTP Destinations](http-destinations-42a0e6b.md) - provide data communication via the HTTP protocol and are used for both Internet and on-premise connections.
    -   [RFC Destinations](rfc-destinations-238d027.md) - make connections to ABAP on-premise systems via RFC protocol using the Java Connector \(JCo\) as API.
    -   Mail destinations - specify an e-mail provider for sending and retrieving e-mails.




<a name="loio565fdb3dd19d4cda80864341dc5a0451__section_gzw_md1_g4b"/>

## Tasks

-   [Create Destinations from Scratch](create-destinations-from-scratch-5eba623.md)
-   [Create Destinations from a Template](create-destinations-from-a-template-ef56ea0.md)
-   [Check the Availability of a Destination](check-the-availability-of-a-destination-71ea3cc.md)
-   [Clone Destinations](clone-destinations-b80786e.md)
-   [Edit and Delete Destinations](edit-and-delete-destinations-372dee2.md)
-   [Manage Destination Certificates](manage-destination-certificates-df1bb55.md)
-   [Import Destinations](import-destinations-91ee9db.md)
-   [Export Destinations](export-destinations-707b49e.md)

**Related Information**  


[Destination Examples](destination-examples-3a2d575.md "Find configuration examples for HTTP and RFC destinations in SAP BTP, using different authentication types.")

