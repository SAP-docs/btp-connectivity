<!-- loioa8bb87a72d094e0d981d2b1f67df7bc3 -->

# Configure Identity Propagation for HTTPS

Find step-by-step instructions to configure principal propagation to an ABAP server for HTTPS.

> ### Note:  
> The information in this section applies to both principal propagation and technical user propagation. These two types of user propagation are combined as *identity* propagation.



<a name="loioa8bb87a72d094e0d981d2b1f67df7bc3__data"/>

## Example Data

The following data are used in this example:

-   System certificate was issued by: `CN=MyCompany CA`,`O=Trust Community`,`C=DE`.
-   It has the subject: `CN=SCC`, `OU=BTP Scenarios`,`O=Trust Community`,`C=DE`.
-   The short-lived certificate has the subject `CN=P1234567890`, where `P1234567890` is the platform user.



<a name="loioa8bb87a72d094e0d981d2b1f67df7bc3__tasks"/>

## Tasks

[Prerequisites](configure-identity-propagation-for-https-a8bb87a.md#loioa8bb87a72d094e0d981d2b1f67df7bc3__prereq)

[Configure an ABAP System to Trust the Cloud Connector's System Certificate](configure-identity-propagation-for-https-a8bb87a.md#loioa8bb87a72d094e0d981d2b1f67df7bc3__abap)

[Map Short-Lived Certificates to Users](configure-identity-propagation-for-https-a8bb87a.md#loioa8bb87a72d094e0d981d2b1f67df7bc3__map)

[Access ICF Services](configure-identity-propagation-for-https-a8bb87a.md#loioa8bb87a72d094e0d981d2b1f67df7bc3__logon)



<a name="loioa8bb87a72d094e0d981d2b1f67df7bc3__prereq"/>

## Prerequisites

-   For identity propagation, mutual authentication \(mTLS\) is mandatory.

    To enable mTLS, you must configure a system certificate as described in this topic. Follow step 1 below to make sure the ABAP system trusts this certificate. You can use the connection check and the *Details* button to check if mTLS is working.

-   The access control entry \(see [Configure Access Control \(HTTP\)](configure-access-control-http-e7d4927.md)\) must have specified the respective identity type to forward the identity correctly.


To perform the following steps, you must have the corresponding authorizations in the ABAP system for the transactions mentioned below \(administrator role according to your specific authorization management\) as well as an administrator user for the Cloud Connector.

Back to [Tasks](configure-identity-propagation-for-https-a8bb87a.md#loioa8bb87a72d094e0d981d2b1f67df7bc3__tasks)

Back to [Example Data](configure-identity-propagation-for-https-a8bb87a.md#loioa8bb87a72d094e0d981d2b1f67df7bc3__data)



<a name="loioa8bb87a72d094e0d981d2b1f67df7bc3__abap"/>

## 1. Configure an ABAP System to Trust the Cloud Connector's System Certificate

This step includes two sub-steps:

[Configure the ABAP system to trust the Cloud Connector's system certificate](configure-identity-propagation-for-https-a8bb87a.md#loioa8bb87a72d094e0d981d2b1f67df7bc3__scc)

[Configure the Internet Communication Manager \(ICM\) to trust the system certificate for principal propagation](configure-identity-propagation-for-https-a8bb87a.md#loioa8bb87a72d094e0d981d2b1f67df7bc3__icm)

**Configure the ABAP system to trust the Cloud Connector's system certificate:**

1.  Open the *Trust Manager* \(transaction `STRUST`\).
2.  Double-click the *SSL-Server Standard* folder in the menu tree on the left.
3.  In the displayed screen, click the *Import certificate* button.
4.  In the dialog window, choose the certificate file representing the public key of the issuer of the system certificate, for example, in DER format. Typically, this is a CA certificate. If you decide to use a self-signed system certificate, it is the system certificate itself.
5.  The details of this certificate are shown in the section above. Using the example certificate data, you would see C`N=MyCompany CA`, `O=Trust Community`, `C=DE` as subject.
6.  If you are sure that you are importing the correct certificate, you can integrate the certificate into the certificate list by choosing the *Add to Certificate List* button.
7.  Now, the CA certificate \(`CN=MyCompany CA`, `O=Trust Community`, `C=DE`\) is part of the certificate list.

Back to [Step](configure-identity-propagation-for-https-a8bb87a.md#loioa8bb87a72d094e0d981d2b1f67df7bc3__abap)

**Configure the Internet Communication Manager \(ICM\) to trust the system certificate for identity propagation:**

1.  Open the *Profile Editor* \(transaction `RZ10`\).
2.  Select the profile you want to edit, for example, the DEFAULT profile.
3.  Select the *Extended maintenance* radio button and choose the *Change* button.
4.  Create the following parameter: `icm/trusted_reverse_proxy_<x> = SUBJECT="<subject>", ISSUER="<issuer>"`.

    -   Select a free index for `<x>`.

    -   `<subject>` is the subject of the system certificate \(example data: `CN=SCC`, `OU=BTP Scenarios`, `O=Trust Community`, `C=DE`\).

    -   `<issuer>` is the issuer of the system certificate \(example data: `CN=MyCompany CA`, `O=Trust Community`, `C=DE` \).

    -   Example: `icm/trusted_reverse_proxy_2 = SUBJECT="CN=SCC, OU=BTP Scenarios, O=Trust Community, C=DE", ISSUER="CN=MyCompany CA, O=Trust Community, C=DE"`.


    > ### Note:  
    > If your ABAP system uses kernel 7.42 or lower, see SAP note [2052899](https://me.sap.com/notes/2052899) or set the following two parameters:
    > 
    > -   `icm/HTTPS/trust_client_with_issuer`: this is the issuer of the system certificate \(example data: `CN=MyCompany CA`, `O=Trust Community`, `C=DE`\).
    > 
    > -   `icm/HTTPS/trust_client_with_subject`: this is the subject of the system certificate \(example data: `CN=SCC`, `OU=BTP Scenarios`, `O=Trust Community`, `C=DE`\).

    > ### Caution:  
    > In all kernel releases below 7.53, the ICM expects *blanks after the separating comma* for the issuer and subject elements. Even if the Cloud Connector administration UI shows a string without blanks, for example: *CN=SCC,OU=BTP Scenarios,O=Trust Community,C=DE*, you must specify in ICM: *CN=SCC, OU=BTP Scenarios, O=Trust Community, C=DE*.
    > 
    > As of kernel release 7.53, this restriction does not exist any more. For more information, see SAP note [3335949](https://me.sap.com/notes/3335949).

    > ### Caution:  
    > Make sure the parameter `icm/server_port` you are using has the attribute `VCLIENT`=1 \(request certificate\) or 2 \(require certificate\). The default value is 1.
    > 
    > If `VCLIENT` is set to 0, trust cannot be established. In this case, you may change the value to 1, but beware that this may have a negative influence on the user experience. Alternatively, create a new parameter `icm/server_port` with `VCLIENT`=1 and configure the Cloud Connector to use this parameter.

5.  Save the profile.
6.  Open the *ICM Monitor* \(transaction `SMICM`\) and restart the ICM by choosing *Administration* \> *ICM* \> *Exit Hard* \> *Global*.
7.  Verify that the two profile parameters have been taken over by ICM by choosing *Goto* \> *Parameters* \> *Display*.

> ### Note:  
> If you have an SAP Web Dispatcher installed in front of the ABAP system, trust must be added in its configuration files with the same parameters as for the ICM. Also, you must add the system certificate of the Cloud Connector to the trust list of the Web dispatcher Server PSE. For more information, see [Configure Identity Propagation via SAP Web Dispatcher](configure-identity-propagation-via-sap-web-dispatcher-9025d5f.md).

> ### Caution:  
> When using identity propagation with X.509 certificates, you cannot use the strict mode in certificate block management \(transaction code: CRCONFIG\) for the CRL checks within profile *SSL\_SERVER*.

Back to [Step](configure-identity-propagation-for-https-a8bb87a.md#loioa8bb87a72d094e0d981d2b1f67df7bc3__abap)

Back to [Tasks](configure-identity-propagation-for-https-a8bb87a.md#loioa8bb87a72d094e0d981d2b1f67df7bc3__tasks)

Back to [Example Data](configure-identity-propagation-for-https-a8bb87a.md#loioa8bb87a72d094e0d981d2b1f67df7bc3__data)



<a name="loioa8bb87a72d094e0d981d2b1f67df7bc3__map"/>

## 2. Map Short-Lived Certificates to Users

For systems later than SAP NetWeaver 7.3 EHP1 \(7.31\), you can use rule-based certificate mapping, which is the recommended way to create the required user mappings. For more information, see [Rule-Based Mapping of Certificates](rule-based-mapping-of-certificates-4f8540f.md).

In older releases \(for which this feature does not exist yet\), you can do this manually in the system as described below, or use an identity management solution generating the mapping table for a more comfortable approach.

1.  Open *Assignment of External ID to Users* \(transaction `EXTID_DN`\).
2.  Switch to the edit mode.
3.  Create a new entry. Specify the subject of the certificate as `External ID`. When using the example data, this is `CN=P1234567890`. In the *User* field, provide the appropriate ABAP user, for example `JOHNSMITH`.
4.  Choose *Activate*.
5.  Save the mapping.
6.  Repeat the previous steps for all users that should be supported for the scenario.

Back to [Tasks](configure-identity-propagation-for-https-a8bb87a.md#loioa8bb87a72d094e0d981d2b1f67df7bc3__tasks)

Back to [Example Data](configure-identity-propagation-for-https-a8bb87a.md#loioa8bb87a72d094e0d981d2b1f67df7bc3__data)



<a name="loioa8bb87a72d094e0d981d2b1f67df7bc3__logon"/>

## 3. Access ICF Services

To access the required ICF services for your scenario in the ABAP system, choose one of the following procedures:

**For Cloud Connector version 2.15 or higher:**

-   To access ICF services via **certificate logon** \(using the system certificate\), select *Allow Principal Propagation*, choose the principal type `X.509 Certificate`, and select *System Certificate for Logon* in the corresponding system mapping.

    This setting lets you use the system certificate for trust in case of principal propagation as well as for user authentication. For details, see [Configure Access Control \(HTTP\)](configure-access-control-http-e7d4927.md), step 7, 8 \(*Procedure for Cloud Connector version 2.15 and higher*\), and 9.

    Additionally, make sure that all required ICF services allow *Logon Through SSL Certificate* as logon method.

-   To access ICF services via the logon method **Basic Authentication** \(logon with user/password\) and identity propagation, select *Allow Principal Propagation*, choose the principal type `X.509 Certificate`, and do *not* select *System Certificate for Logon* in the corresponding system mapping.

    This setting lets you use the system certificate for trust, but prevents its usage for user authentication. For details, see [Configure Access Control \(HTTP\)](configure-access-control-http-e7d4927.md), step 7, 8 \(*Procedure for Cloud Connector version 2.15 and higher*\), and 9.

    Additionally, make sure that all required ICF services allow *Basic Authentication* and *Logon Through SSL Certificate* as logon method.


-   If some of the ICF services require `Basic Authentication`, while others should be accessed via system certificate logon, perform these steps:
    1.  In the Cloud Connector system mapping, select *Allow Principal Propagation*, choose the principal type `X.509 Certificate`, and select *System Certificate for Logon* in the corresponding system mapping as described above.
    2.  In the ABAP system, choose transaction code SICF and go to *Maintain Services*.
    3.  Select the service that requires `Basic Authentication` as logon method.
    4.  Double-click the service and go to tab *Logon Data*.
    5.  Switch to *Alternative Logon Procedure* and ensure that the `Basic Authentication` logon procedure is listed before `Logon Through SSL Certificate`.


**For Cloud Connector versions below 2.15:**

-   To access ICF services via certificate logon, choose the principal type `X.509 Certificate (general usage)` in the corresponding system mapping. This setting lets you use the system certificate for trust as well as for user authentication.

    For details, see [Configure Access Control \(HTTP\)](configure-access-control-http-e7d4927.md), step 8 \(*Procedure for Cloud Connector versions below 2.15*\).

    Additionally, make sure that all required ICF services allow `Logon Through SSL Certificate` as logon method.


-   To access ICF services via the logon method `Basic Authentication` \(logon with user/password\) and principal propagation, choose the principal type `X.509 Certificate (strict usage)` in the corresponding system mapping. This setting lets you use the system certificate for trust, but prevents its usage for user authentication.

    For details, see [Configure Access Control \(HTTP\)](configure-access-control-http-e7d4927.md), step 8 \(*Procedure for Cloud Connector versions below 2.15*\).

    Additionally, make sure that all required ICF services allow `Basic Authentication` and `Logon Through SSL Certificate` as logon methods.


-   If some of the ICF services require `Basic Authentication`, while others should be accessed via system certificate logon, perform these steps:
    1.  In the Cloud Connector system mapping, choose the principal type `X.509 Certificate (general usage)` as described above.
    2.  In the ABAP system, choose transaction code SICF and go to *Maintain Services*.
    3.  Select the service that requires `Basic Authentication` as logon method.
    4.  Double-click the service and go to tab *Logon Data*.
    5.  Switch to *Alternative Logon Procedure* and ensure that the `Basic Authentication` logon procedure is listed before `Logon Through SSL Certificate`.


> ### Note:  
> If you are using SAP Web Dispatcher for communication, you must configure it to forward the SSL certficate to the ABAP backend system, see [Forward SSL Certificates for X.509 Authentication](https://help.sap.com/viewer/683d6a1797a34730a6e005d1e8de6f22/201809.latest/en-US/2a6cec67c50842aab1444f7dfd0257e1.html) \(SAP Web Dispatcher documentation\).

Back to [Tasks](configure-identity-propagation-for-https-a8bb87a.md#loioa8bb87a72d094e0d981d2b1f67df7bc3__tasks)

Back to [Example Data](configure-identity-propagation-for-https-a8bb87a.md#loioa8bb87a72d094e0d981d2b1f67df7bc3__data)



<a name="loioa8bb87a72d094e0d981d2b1f67df7bc3__section_cwc_jbk_vkb"/>

## Related Information

[Configure Identity Propagation via SAP Web Dispatcher](configure-identity-propagation-via-sap-web-dispatcher-9025d5f.md)

[Rule-Based Mapping of Certificates](rule-based-mapping-of-certificates-4f8540f.md)

[Configure Subject Patterns](configure-subject-patterns-58803a2.md)

[Set Up Trust](set-up-trust-a4ee70f.md)

[Principal Propagation](principal-propagation-e2cbb48.md) \(Cloud Foundry environment\)

[Principal Propagation](https://help.sap.com/viewer/b865ed651e414196b39f8922db2122c7/Cloud/en-US/d4d3e1e9b2dd44318b49a4812cd51383.html "Forward the identity of cloud users to an on-premise system to enable single sign-on (Neo environment).") :arrow_upper_right: \(Neo environment\)

