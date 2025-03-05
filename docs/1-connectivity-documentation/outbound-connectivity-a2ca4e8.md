<!-- loioa2ca4e857ce74f26b5dcf3483e760ab7 -->

# Outbound Connectivity

The Cloud Connector supports the communication direction from the on-premises network to SAP BTP, using a database tunnel.

The database tunnel is used to connect local database tools via JDBC or ODBC to the SAP HANA DB or other databases onSAP BTP, for example, SAP Business Objects tools like Lumira, BOE or Data Services.

-   The database tunnel only allows JDBC and ODBC connections from the Cloud Connector into the cloud. A reuse for other protocols is not possible.
-   The tunnel uses the same security mechanisms as for the inbound connectivity:
    -   TLS-encryption and mutual authentication
    -   Audit logging


To use the database tunnel, two different SAP BTP users are required:

-   A platform user \(member of the SAP BTP subaccount\) establishes the database tunnel to the HANA DB.
-   A HANA DB user is needed for the ODBC/JDBC connection to the database itself. For the HANA DB user, the role and privilege management of HANA can be used to control which actions he or she can perform on the database.

**Related Information**  


[Using Service Channels](using-service-channels-16f6342.md "Configure Cloud Connector service channels to connect your on-premises network to specific services on SAP BTP or to an ABAP Cloud system.")

