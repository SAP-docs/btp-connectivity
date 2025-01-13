<!-- loio93accc4e73b44449b6926368d1103b0b -->

# Using Encryption Keys for the Destination Service

Choose between different options to encrypt your data when using the Destination service.

> ### Restriction:  
> This feature is supported only in regions providing the [*SAP Credential Store*](https://help.sap.com/docs/credential-store/sap-credential-store/what-is-sap-credential-store?version=Cloud).

When using the Destination service, there are two options to encrypt your data:

-   **Customer-specific encryption keys \(CSEK\)**:

    This option encrypts your data with individual \(customer-specific\) encryption keys. The keys, however, are still managed by SAP. This is the default setting, and you do not need to do anything to enable it.

    *Customer-specific encryption* is a prerequisite for using *customer-managed keys \(CMK\)*.

-   **Customer-managed keys \(CMK\)**: This option applies only if you want to bring your own key for encryption.

    When you choose this option, data are double-encrypted: Using the default CSEK encryption, and in addition using encryption with your own key.

    To use this option, you must provision your own key management service. For this purpose, SAP offers the *Data Custodian Key Management service*. Using this service, you can control your own keys \(grant, revoke, rotate, and delete keys\).

    For more information, see [What is Key Management Service?](https://help.sap.com/docs/sap-data-custodian/key-management-service/what-is-key-management-service-page)


When using CSEK/CMK, all destination properties \(both main and additional\) are encrypted, except for \(destination\) `Name` and `FragmentName`.

> ### Note:  
> Destination properties are encrypted regardless of their sensitivity.

> ### Restriction:  
> This service does not encrypt the following data:
> 
> -   \(Destination\) `Name` and `FragmentName`
> -   All **metadata** like creation and update dates, tools that created the destination, owner subaccount, and so on

