<!-- loio071708a655de4486b498cf5b16fb8ea8 -->

# Update the Certificate for a Subaccount

Certificates used by the Cloud Connector are issued with a limited validity period. To prevent a downtime while refreshing the certificate, you can update it for your subaccount directly from the administration UI.



<a name="loio071708a655de4486b498cf5b16fb8ea8__section_f1x_j5y_vmb"/>

## Prerequisites

You must have the required subaccount authorizations on SAP BTP to update certificates for your subaccount.

See:

-   [Connectivity: Technical Roles](what-is-sap-btp-connectivity-daca64d.md#loiodaca64dacc6148fcb5c70ed86082ef91__technical) \(**Cloud Foundry** environment\)



<a name="loio071708a655de4486b498cf5b16fb8ea8__section_lrc_k5y_vmb"/>

## Procedure

> ### Tip:  
> You can use this procedure even if the certificate has already expired.

Proceed as follows to update your subaccount certificate:

1.  From the main menu, choose your subaccount, and navigate to subaccount overview.

    > ### Note:  
    > To check the certificate's validity, click on the *<Subaccount Certificate\>* in section *Subaccount Overview*.

2.  Press the *Certificate* button. Depending on the cloud environment, you can refresh using authentication data from a file or manually by providing user name and password, or only the latter. The respective dialog or wizard is shown.

    > ### Tip:  
    > You can download an authentication data file from the *Cloud Connectors* view in your subaccount. Choose *Connectivity* \> *Cloud Connectors* \> *Download Authentication Data* from your subaccount menu. This feature is available for subaccounts in multi-cloud foundation, feature set B only.

3.  Enter *<User Name\>* and *<Password\>* \(or use the file with authentication data if the option is offered\) and choose *Refresh* \(or *Finish*\). The certificate assigned to your subaccount is refreshed.

    > ### Note:  
    > In the **Cloud Foundry** environment, you must provide your `Login E-mail` instead of a user ID as *<User Name\>*.



    > ### Tip:  
    > When using SAP Cloud Identity Services - Identity Authentication \(IAS\) as platform identity provider with two-factor authentication \(2FA / MFA\) for your subaccount, you can simply append the required token to the regular password. For example, if your password is "eX7?6rUm" and the one-time passcode is "123456", you must enter "eX7?6rUm123456" into the *<Password\>* field.
    > 
    > **Appending the two-factor authentication** \(2FA / MFA\) token to the regular password **is not required** when updating the Cloud Connector subaccount certificate in the **Neo environment**.


