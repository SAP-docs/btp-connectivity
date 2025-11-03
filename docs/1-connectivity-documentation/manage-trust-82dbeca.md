<!-- loio82dbecae3454493782d16a79e30f1a6d -->

# Manage Trust

Download and configure X.509 certificates as a prerequisite for user propagation from the multi-cloud environment.

Setting up a trust scenario for user propagation \(also known as *principal propagation*\) requires the exchange of public keys and certificates between the affected systems, as well as the respective trust configuration within these systems. This enables you to use an HTTP destination with authentication type `OAuth2SAMLBearerAssertion` or `SAMLAssertion` for the communication.

> ### Note:  
> The described procedures are focused on doing them via the *Destinations* editor in the cockpit. However, they are also fully automatable via the [Destination Service REST API](destination-service-rest-api-23ccafb.md). References to the respective API endpoints are added to the relevant steps below.

A trust scenario can include user propagation from the multi-cloud environment to another SAP BTP environment, to another multi-cloud subaccount, or to a remote system outside SAP BTP, like SAP S/4HANA Cloud, SAP Sales Cloud, SAP Success Factors, and others.



## Prerequisites

You have at least the relevant `Administrator` user role \(*Destination Administrator* or *Destination Subaccount Trust Administrator*\).

For more information, see [User Roles](user-roles-b922fc8.md).



<a name="loio82dbecae3454493782d16a79e30f1a6d__setup_cert"/>

## Set Up a Certificate

Download and save locally the X.509 certificate of the subaccount in the multi-cloud environment.

1.  Log on to the cockpit and navigate to your subaccount in the multi-cloud environment.
2.  From the left-side menu, choose *Connectivity* \> *Destination Trust*.
3.  If the subaccount does not yet have a *SAML Trust* configuration for the Destination service, choose *Generate Trust*:

    ![](images/CS_Set_Up_Trust_Between_Systems_1_7faa0e0.png)

    > ### Note:  
    > Respective API endpoints:
    > 
    > -   Generate or renew the active X.509 trust certificate: `POST /saml2Metadata/certificate`.

4.  Once generated, you have an active trust certificate, and its details are visible in the UI:

    ![](images/CS_Set_Up_Trust_Between_Systems_2_b67fa4b.png)

5.  Export the public part of this certificate, which downloads a *.pem* certificate file:

    > ### Tip:  
    > We recommend that you also note down the values of *Assertion Entity ID* and *Signing Key Name* which may be required by the target system\(s\) when establishing trust.

    ![](images/CS_Set_Up_Trust_Between_Systems_3_fdb3c48.png)

    > ### Note:  
    > Respective API endpoints:
    > 
    > -   Retrieve the active X.509 trust certificate: `GET /saml2Metadata/certificate`.

6.  Configure the downloaded X.509 certificate **in the target system\(s\)** to which you want to propagate the user.



<a name="loio82dbecae3454493782d16a79e30f1a6d__renew_cert"/>

## Renew a Certificate

If the X.509 certificate validity is about to expire, you can renew the certificate and extend its validity by another 2 years.

![](images/CS_Set_Up_Trust_Between_Systems_4_6134aea.png)

1.  Log on to the cockpit and navigate to your subaccount in the multi-cloud environment.
2.  From the left-side menu, choose *Connectivity* \> *Destination Trust*.
3.  Choose *Renew* for the certificate you want to update:

    > ### Caution:  
    > It is not recommended to renew an active certificate directly. Consider using the [Rotate Certificates](manage-trust-82dbeca.md#loio82dbecae3454493782d16a79e30f1a6d__rotate) feature below if you want a zero-downtime procedure.

    ![](images/CS_Set_Up_Trust_Between_Systems_5_07ccaab.png)

    > ### Note:  
    > Respective API endpoints:
    > 
    > -   Generate or renew the active X.509 trust certificate: `POST /saml2Metadata/certificate`.
    > 
    > -   Generate or renew the passive X.509 trust certificate: `POST /saml2Metadata/certificate/passive`.

4.  Confirm the renewal:

    ![](images/CS_Set_Up_Trust_Between_Systems_6_e029009.png)

5.  You will now see that the warnings are gone, and the certificate details reflect the new dates:

    ![](images/CS_Set_Up_Trust_Between_Systems_7_b818ee0.png)

6.  Get the required details to establish trust in the target system\(s\) based on the new certificate, by performing an *Export* of the certificate:

    ![](images/CS_Set_Up_Trust_Between_Systems_8_ad1ba5b.png)

    > ### Note:  
    > Respective API endpoints:
    > 
    > -   Retrieve the active X.509 trust certificate: `GET /saml2Metadata/certificate`.
    > 
    > -   Retrieve the passive X.509 trust certificate: `GET /saml2Metadata/certificate/passive`.

7.  Configure the renewed X.509 certificate **in the target system\(s\)** to which you want to propagate the user.



<a name="loio82dbecae3454493782d16a79e30f1a6d__rotate"/>

## Rotate Certificates

If you renew an active certificate, the Destination service will immediately start signing new SAML assertions with the new one. While this is fast and suitable for development scenarios, for productive scenarios you will have a downtime until you manage to re-establish the trust in all target systems. Therefore, we recommend that you perform the *rotate* procedure described in this section instead.

Rotation is done by creating a passive X.509 certificate for the subaccount, configuring it in the target system\(s\) to which you want to propagate the user, and rotating it with the active one. After rotation is performed, the active X.509 certificate becomes passive and the passive one active.

> ### Note:  
> You should execute this procedure *before* the expiration date of the currently active certificate.

**Procedure**

1.  Generate or renew the passive X.509 certificate:

    ![](images/CS_Set_Up_Trust_Between_Systems_9_32f70df.png)

    > ### Note:  
    > Respective API endpoints:
    > 
    > -   Generate or renew the passive X.509 certificate: `POST /saml2Metadata/certificate/passive`.

2.  Download and save locally the passive X.509 certificate:

    ![](images/CS_Set_Up_Trust_Between_Systems_10_9d2590b.png)

    > ### Note:  
    > Respective API endpoints:
    > 
    > -   Retrieve the passive X.509 certificate: `GET /saml2Metadata/certificate/passive`.

3.  Configure the downloaded X.509 passive certificate **in the target system\(s\)** you want to propagate the user to.
4.  Rotate the active certificate, making the active one passive and the passive one active:

    ![](images/CS_Set_Up_Trust_Between_Systems_11_e32544e.png)

    > ### Note:  
    > Respective API endpoints:
    > 
    > -   Switch the roles of the active and passive certificates: `POST /saml2Metadata/rotateCertificate`.

5.  Confirm the action:

    ![](images/CS_Set_Up_Trust_Between_Systems_12_8e346d7.png)

6.  Check if the two certificates have now switched places. Your scenarios should continue working with no disruption.

    ![](images/CS_Set_Up_Trust_Between_Systems_13_8fa2c8b.png)

7.  \(Optional\): Delete the passive X.509 certificate, which used to be active before rotation.

    > ### Note:  
    > Respective API endpoints:
    > 
    > -   Delete the passive X.509 certificate: `DELETE /saml2Metadata/certificate/passive`.

8.  \(Optional\): Delete the passive X.509 certificate, which used to be active before rotation, from the target system\(s\).

**Related Information**  


[Principal Propagation](principal-propagation-e2cbb48.md "Enable single sign-on (SSO) by forwarding the identity of cloud users to a remote system or service.")

[SAP BTP Destination Service Expiring Certificate Notification](https://help.sap.com/viewer/5967a369d4b74f7a9c2b91f5df8e6ab6/Cloud/en-US/92e3840b38824ea28f8c9be692ca5f83.html "This event is triggered for expiring certificates with no automatic renewal. It is triggered a few times for each expiring certificate - 14 days before certificate expiration, 7 days before certificate expiration and 3 days before certificate expiration.") :arrow_upper_right:

