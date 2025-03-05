<!-- loio9025d5f808d14fef9bad1de88d93f3a3 -->

# Configure Identity Propagation via SAP Web Dispatcher

Set up a trust chain to use identity propagation to an ABAP System for HTTPS via SAP Web Dispatcher.

> ### Note:  
> The information in this section applies to both principal propagation and technical user propagation. These two types of user propagation are combined as *identity* propagation.



<a name="loio9025d5f808d14fef9bad1de88d93f3a3__concept"/>

## Concept

If you are using an intermediate SAP Web Dispatcher to connect to your ABAP backend system, you must set up a trust chain between the involved components Cloud Connector, SAP Web Dispatcher, and ABAP backend system.

Before configuring the ABAP system \(see [Configure Identity Propagation for HTTPS](configure-identity-propagation-for-https-a8bb87a.md)\), in a first step you must configure SAP Web Dispatcher to accept and forward user principals propagated from a cloud account to an ABAP backend.

To do this, follow the step-by-step instructions below.



<a name="loio9025d5f808d14fef9bad1de88d93f3a3__data"/>

## Example Data

The following data and setup is used for this scenario:

-   System certificate was issued by `CN=MyCompany CA, O=Trust Community, C=DE`
-   It has the subject `CN=SCC, OU=BTP Scenarios, O=Trust Community, C=DE`



<a name="loio9025d5f808d14fef9bad1de88d93f3a3__tasks"/>

## Tasks

-   [Prerequisites](configure-identity-propagation-via-sap-web-dispatcher-9025d5f.md#loio9025d5f808d14fef9bad1de88d93f3a3__prereq)
-   [Configure the SAP Web Dispatcher to Trust the Cloud Connector's System Certificate](configure-identity-propagation-via-sap-web-dispatcher-9025d5f.md#loio9025d5f808d14fef9bad1de88d93f3a3__web)
-   [Next Steps](configure-identity-propagation-via-sap-web-dispatcher-9025d5f.md#loio9025d5f808d14fef9bad1de88d93f3a3__next)



<a name="loio9025d5f808d14fef9bad1de88d93f3a3__prereq"/>

## Prerequisites

-   Your SAP Web Dispatcher version is 7.53 or higher. See SAP note [908097](https://me.sap.com/notes/908097) for information on recommended SAP Web Dispatcher versions.
-   We recommend that you use a standalone Web Dispatcher deployment. To learn about deployment options, see SAP note [3115889](https://me.sap.com/notes/3115889).
-   Make sure your SAP Web Dispatcher supports SSL. See [Configure SAP Web Dispatcher to Support SSL](https://help.sap.com/viewer/683d6a1797a34730a6e005d1e8de6f22/latest/en-US/493db10a19341067e10000000a42189c.html).
-   Ensure that TLS client certificates can be used for authentication in the backend system. See [How to Configure SAP Web Dispatcher to Forward SSL Certificates for X.509 Authentication](https://wiki.scn.sap.com/wiki/display/SI/How+to+Configure+SAP+Web+Dispatcher+to+Forward+SSL+Certificates+for+X.509+Authentication) for step-by-step instructions.

> ### Caution:  
> In case of identity propagation, make sure you do not use a *Web Application Firewall*\(WAF\) or a *Reverse Proxy* between the Cloud Connector and the SAP Web Dispatcher. This would terminate TLS, and disables functions like E2E trust and MITM attack prevention.

Back to [Tasks](configure-identity-propagation-via-sap-web-dispatcher-9025d5f.md#loio9025d5f808d14fef9bad1de88d93f3a3__tasks)

Back to [Concept](configure-identity-propagation-via-sap-web-dispatcher-9025d5f.md#loio9025d5f808d14fef9bad1de88d93f3a3__concept)



<a name="loio9025d5f808d14fef9bad1de88d93f3a3__web"/>

## Configure SAP Web Dispatcher to Trust the Cloud Connector's System Certificate

To allow Cloud Connector client certificates for authentication in the backend system, perform the following two steps:

1.  **Configure SAP Web Dispatcher to trust the Cloud Connector's system certificate:**
    1.  To import the system certificate to SAP Web Dispatcher, open the SAP Web Dispatcher administration interface in your browser.

        > ### Note:  
        > The interface is usually configured on `/sap/wdisp/admin`.

    2.  In the menu, navigate to *SSL and Trust Configuration* and select *PSE Management*.
    3.  In the **Manage PSE** section, select `SAPSSLS.pse` from the drop-down list. By default, SAPSSLS.pse contains the server certificate and the list of trusted clients that SAP Web Dispatcher trusts as a server.
    4.  In the **Trusted Certificates** section, choose *Import Certificate*.
    5.  Enter the certificate as *base64-encoded* into the text box. The procedure to export your certificate in such a format is described in [Forward SSL Certificates for X.509 Authentication](https://help.sap.com/viewer/683d6a1797a34730a6e005d1e8de6f22/latest/en-US/2a6cec67c50842aab1444f7dfd0257e1.html), step 1.

        > ### Note:  
        > Typically, this is a CA certificate. If you are using a self-signed system certificate, it's the system certificate itself.

    6.  Choose *Import*.
    7.  The certificate details are now shown in section **Trusted Certificates**.

2.  **Configure SAP Web Dispatcher to trust the Cloud Connector's system certificate for identity propagation:**
    -   Create or edit the following parameter in SAP Web Dispatcher:

        `icm/trusted_reverse_proxy_<x> = SUBJECT="<subject>", ISSUER="<issuer>"`

        -   Select a free index for `<x>`.

        -   `<subject>`: Subject of the system certificate \(example data: `CN=SCC, OU=BTP Scenarios, O=Trust Community, C=DE`\)

        -   `<issuer>`: Issuer of the system certificate \(example data: `CN=MyCompany CA, O=Trust Community, C=DE`\)


        **Example**: `icm/trusted_reverse_proxy_0 = SUBJECT="CN=SCC, OU=BTP Scenarios, O=Trust Community, C=DE", ISSUER="CN=MyCompany CA, O=Trust Community, C=DE"`

        > ### Caution:  
        > The ICM expects *blanks after the separating comma* for the issuer and subject elements. So, even if the Cloud Connector administration UI shows a string without blanks, for example: *CN=SCC,OU=BTP Scenarios,O=Trust Community,C=DE*, you must specify in ICM: *CN=SCC, OU=BTP Scenarios, O=Trust Community, C=DE*.

    -   **\[Deprecated\]** Create or edit the following two parameters in SAP Web Dispatcher:

        > ### Note:  
        > Use the parameters below \(instead of `icm/trusted_reverse_proxy_<x>`\) only if your kernel release does not yet support parameter `icm/trusted_reverse_proxy_<x>`.

        -   `icm/HTTPS/trust_client_with_issuer`: Issuer of the system certificate \(example data: `CN=MyCompany CA, O=Trust Community, C=DE`\)

        -   `icm/HTTPS/trust_client_with_subject`: Subject of the system certificate \(example data: `CN=SCC, OU=BTP Scenarios, O=Trust Community, C=DE` \)



> ### Note:  
> Make sure `icm/HTTPS/verify_client` is set to `1` \(request certificate\) or `2` \(require certificate\). If set to `0`, trust cannot be established. The default value is `1`, so it is OK if the parameter is not set at all.

Back to [Tasks](configure-identity-propagation-via-sap-web-dispatcher-9025d5f.md#loio9025d5f808d14fef9bad1de88d93f3a3__tasks)

Back to [Concept](configure-identity-propagation-via-sap-web-dispatcher-9025d5f.md#loio9025d5f808d14fef9bad1de88d93f3a3__concept)



<a name="loio9025d5f808d14fef9bad1de88d93f3a3__next"/>

## Next Steps

Now you can proceed with:

-   Step 1 of the basic identity propagation setup for HTTPS, see [Configure an ABAP System to Trust the Cloud Connector's System Certificate](configure-identity-propagation-for-https-a8bb87a.md#loioa8bb87a72d094e0d981d2b1f67df7bc3__abap). However, when using SAP Web Dispatcher, the ABAP backend must trust the *SAP Web Dispatcher* instead of the *Cloud Connector*, see [Forward SSL Certificates for X.509 Authentication](https://help.sap.com/viewer/683d6a1797a34730a6e005d1e8de6f22/latest/en-US/2a6cec67c50842aab1444f7dfd0257e1.html), step 2 for details.

Then perform the remaining steps of the basic identity propagation setup for HTTPS as described here:

-   [Map Short-Lived Certificates to Users](configure-identity-propagation-for-https-a8bb87a.md#loioa8bb87a72d094e0d981d2b1f67df7bc3__map) 
-   [Access ICF Services](configure-identity-propagation-for-https-a8bb87a.md#loioa8bb87a72d094e0d981d2b1f67df7bc3__logon)

Back to [Tasks](configure-identity-propagation-via-sap-web-dispatcher-9025d5f.md#loio9025d5f808d14fef9bad1de88d93f3a3__tasks)

Back to [Concept](configure-identity-propagation-via-sap-web-dispatcher-9025d5f.md#loio9025d5f808d14fef9bad1de88d93f3a3__concept)

