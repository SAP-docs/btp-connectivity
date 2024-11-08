<!-- loio707b49e752df4741bf678bc27523af7a -->

# Export Destinations

Export destinations from the *Destinations* editor in the SAP BTP cockpit to backup or reuse a destination configuration.



## Prerequisites

You have created a destination in the ** editor.



## Procedure

1.  Log into the cockpit and open the *Destinations* editor.

2.  Select a destination and choose the ![](images/Export_destination_cockpit_dbc9e9f.png) button.

3.  Browse to the location on your local file system where you want to save the new destination.

    -   If the destination does not contain client certificate authentication, it is saved as a single configuration file.
    -   If the destination provides client certificate data, it is saved as an archive. The content of this archive contains the main configuration file and a single or multiple PEM files. The actual number of PEM files depends on the amount of aliases inside the client certificate. Each PEM file will be named after an alias and will contain the public data associated with that alias.


**Related Information**  


[Edit and Delete Destinations](edit-and-delete-destinations-372dee2.md "How to edit and delete destinations in the Destinations editor (SAP BTP cockpit).")

[Destination Examples](destination-examples-3a2d575.md "Find configuration examples for HTTP and RFC destinations in SAP BTP, using different authentication types.")

