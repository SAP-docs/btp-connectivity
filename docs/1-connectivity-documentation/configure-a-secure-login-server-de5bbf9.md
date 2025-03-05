<!-- loiode5bbf9a92ce402cb0e21952c37b146d -->

# Configure a Secure Login Server

Configuration steps for Java SLS support.

> ### Note:  
> The information in this section applies to both principal propagation and technical user propagation.

> ### Note:  
> The Secure Login Server mainstream maintenance ends on December 31, 2027. In particular, this is also relevant when using it with the Cloud Connector for the scenarios with principal propagation and technical user propagation.



<a name="loiode5bbf9a92ce402cb0e21952c37b146d__content"/>

## Content

[Overview](configure-a-secure-login-server-de5bbf9.md#loiode5bbf9a92ce402cb0e21952c37b146d__overview)

[Requirements](configure-a-secure-login-server-de5bbf9.md#loiode5bbf9a92ce402cb0e21952c37b146d__requirements)

[Implementation](configure-a-secure-login-server-de5bbf9.md#loiode5bbf9a92ce402cb0e21952c37b146d__implementation)



<a name="loiode5bbf9a92ce402cb0e21952c37b146d__overview"/>

## Overview

The Cloud Connector can use on-the-fly generated X.509 user certificates to log in to on-premises systems if the external user session is authenticated \(for example by means of SAML\). If you do not want to use the built-in certification authority \(CA\) functionality of the Cloud Connector \(for example because of security considerations\), you can connect SAP SSO 2.0 Secure Login Server \(SLS\) or higher.

> ### Note:  
> Make sure you use a version that is still supported, which is currently at least SAP SSO 3.0 Secure Login Server.

SLS is a Java application running on AS JAVA 7.20 or higher, which provides interfaces for certificate enrollment.

SLS supports the following formats:

-   HTTPS
-   REST
-   JSON
-   PKCS\#10/PKCS\#7

> ### Note:  
> Any enrollment requires a successful user or client authentication, which can be a single, multiple or even a multi factor authentication.

The following schemes are supported:

-   LDAP/ADS
-   RADIUS
-   SAP SSO OTP
-   ABAP RFC
-   Kerberos/SPNego
-   X.509 TLS Client Authentication

SLS lets you define arbitrary enrollment profiles, each with a unique profile UID in its URL, and with a configurable authentication and certificate generation.

Back to [Content](configure-a-secure-login-server-de5bbf9.md#loiode5bbf9a92ce402cb0e21952c37b146d__content)



<a name="loiode5bbf9a92ce402cb0e21952c37b146d__requirements"/>

## Requirements

For user certification, SLS must provide a profile that adheres to the following:

-   Cloud Connector client authentication by its X.509 system certificate

-   Cloud Connector system certificate and SLS may live in different PKIs

-   Cloud Connector hands over the full user´s certificate subject name


With SAP SSO 2.0 SP06, SLS provides the following required features:

-   TLS Client Authentication-based enrollment with `SecureLoginModuleUserDelegationWithSSL` \(available since SP04\)

-   multi-PKI support is implemented by all standard components of Application Server \(AS\) JAVA, AS ABAP, HANA, by importing trusted root CA certificates
-   SLS allows `PKCS10:SUBJECT` in a profile´s certificate configuration \(SP06\)

Back to [Content](configure-a-secure-login-server-de5bbf9.md#loiode5bbf9a92ce402cb0e21952c37b146d__content)



<a name="loiode5bbf9a92ce402cb0e21952c37b146d__implementation"/>

## Implementation

**INSTALLATION** 

Follow the standard installation procedures for SLS. This includes the initial setup of a PKI \(public key infrastructure\).

> ### Note:  
> SLS allows you to set up one or more own PKIs with Root CA, User CA, and so on. You can also import CAs as PKCS\#12 file or use a hardware security module \(HSM\) as "External User CA".

> ### Note:  
> You should only use HTTPS connections for any communication with SLS. AS JAVA / ICM supports TLS, and the default configuration comes with a self-signed sever certificate. You may use SLS to replace this certificate by a PKI certificate.

**CONFIGURATION** 

**SSL Ports** 

1.  Open the NetWeaver Administrator, choose *Configuration* \> *SSL* and define a new port with `Client Authentication Mode = REQUIRED`.

    > ### Note:  
    > You may also define another port with `Client Authentication Mode = Do not request` if you did not do so yet.

2.  Import the root CA of the PKI that issued your Cloud Connector system certificate.
3.  Save the configuration and restart the Internet Communication Manager \(ICM\).

**Authentication Policy**

1.  Open the NetWeaver Administrator \(NWA, https://<host:port\>/nwa\).
2.  From the top-level menu, choose *Configuration* \> *Authentication and Single Sign-On* .
3.  In the *Policy Configuration* table, switch to `Type = Custom`.
4.  Choose *Add* to create a new policy and assign it a name, for example, `SecureLoginCloudConnector`.
5.  Open *Edit* mode.
6.  In the *Details* section of the authentication configuration, choose *Authentication Stack* \> *Login Modules* and add `SecureLoginModuleUserDelegationWithSSL`.
7.  In *<Rule1.subjectName\>* and *<Rule1.issuerName\>*, enter the respective certificate names of your Cloud Connector system certificate.
8.  In the *Details* section of the authentication configuration, choose *Properties* and add the property `UserNameMapping` with value `VirtualUser`.
9.  Save the policy.

**Client Authentication Profile**

1.  Open the SLS Administration Console \(SLAC, https://host:port/slac\).
2.  From the top-level menu, choose *Profile Management* \> *Authentication Profiles* .
3.  Create a new profile with `Client Type = Secure Login Client` and assign it a name, for example, `Cloud Connector User Certificates`.
4.  Choose *User Authentication* \> *Use Policy Configuration* and select `Policy Configuration Name = SecureLoginCloudConnector`.
5.  Edit all required fields in the wizard according to your requirements.
6.  In tab *Authentication Configuration*, check the box *Virtual User*.
7.  Save your entries.
8.  Select the new profile and open *Edit* mode.
9.  Choose *Certificate Configuration* \> *Certificate Name and Alternative Names* and set `Appendix Subject Name = (PKCS10:SUBJECT)`.
10. Leave all other fields in *Certificate Name and Alternative Names* empty.
11. On the *Enrollment Configuration* page, make sure that the *<Enrollment URL\>* has the correct value, otherwise edit and fix it:
    1.  full DNS name
    2.  port *with* TLS Client Authentication \(see port number in NWA SSL Configuration\).

12. Save your entries.

**User Profile Group**

1.  Open the SLS Administration Console \(SLAC, https://host:port/slac\).
2.  Go to the top level menu and choose *Profile Management* \> *User Profile Groups*.
3.  Create a new profile group, make sure the *<Policy URL\>* has the correct value:
    1.  Full DNS name
    2.  Port *without* TLS Client Authentication \(see port number in NWA SSL Configuration\).

4.  In tab *Profiles*, add the profile `Cloud Connector User Certificates`.
5.  Save your entries.

**Root CA Certificate**

1.  Open SLS Administration Console \(SLAC, https://host:port/slac\).
2.  Go to the top level menu and choose *Certificate Management*.
3.  Select the Root CA certificate you are using in your profile.
4.  Choose *Export entry* \> *X.509 Certificate* and download the certificate file.

**Cloud Connector**

Follow the standard installation procedure of the Cloud Connector and configure SLS support as explained in [Configuration of a CA hosted by a Secure Login Server](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/configure-ca-certificate-for-principal-propagation#configure-a-ca-hosted-by-a-secure-login-server):

1.  Enter the policy URL that points to the SLS user profile group.
2.  Select the profile, for example, `Cloud Connector User Certificates`.
3.  Import the Root CA certificate of SLS into the Cloud Connector´s [Trust Store](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/a4ee70f0274248f8bbc7594179ef948d.html#loioa4ee70f0274248f8bbc7594179ef948d__section_TrustStore).

**On-Premises Target Systems**

Follow the standard configuration procedure for Cloud Connector support in the corresponding target system and configure SLS support.

To do so, import the Root CA certificate of SLS into the system´s truststore:

-   **AS ABAP**: choose transaction STRUST and follow the steps in [Maintaining the SSL Server PSE's Certificate List](https://help.sap.com/viewer/e73bba71770e4c0ca5fb2a3c17e8e229/7.51.0/en-US/49250a3467cd3895e10000000a421937.html).

-   **AS Java**: open the Netweaver Administrator and follow the steps described in [Configuring the SSL Key Pair and Trusted X.509 Certificates](https://help.sap.com/viewer/a42446bded624585958a36a71903a4a7/7.5.8/en-US/4a0142abaee3088ce10000000a421937.html).

Back to [Content](configure-a-secure-login-server-de5bbf9.md#loiode5bbf9a92ce402cb0e21952c37b146d__content)



