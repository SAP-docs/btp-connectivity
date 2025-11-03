<!-- loio33a2f37b0f1e4b6d869ab85c8427db1b -->

# Configure Identity Propagation for RFC

Find step-by-step instructions to configure principal propagation to an ABAP server for RFC.

Configuring principal propagation for RFC requires an SNC \(Secure Network Communications\) connection. To enable SNC, you must configure the ABAP system and the Cloud Connector accordingly.

The following example provides step-by-step instructions for the SNC setup.

> ### Note:  
> It is important that you use the same SNC implementation on both communication sides. Contact the vendor of your SNC solution to check the compatibility rules.



<a name="loio33a2f37b0f1e4b6d869ab85c8427db1b__data"/>

## Example Data

The following data and setup is used:

> ### Note:  
> The parameters provided in this example are based on an SNC implementation that uses the **SAP Cryptographic Library**. Other vendors' libraries may require different values.

-   An SNC identity has been generated and installed on the Cloud Connector host. Generating this identity for the SAP Cryptographic Library is typically done using the tool `SAPGENPSE`. For more information, see [Configuring SNC for SAPCRYPTOLIB Using SAPGENPSE](https://help.sap.com/viewer/e73bba71770e4c0ca5fb2a3c17e8e229/7.52.3/en-US/4da6e296fd801f8de10000000a15822b.html).
-   The ABAP system is configured properly for SNC.

    > ### Note:  
    > For the latest system releases, you can use the SSO wizard to configure SNC \(transaction code: SNCWIZARD\). System prerequisites are described in SAP note [2015966](https://me.sap.com/notes/2015966) .

-   The Cloud Connector system identity's SNC name is `p:CN=SCC, OU=SAP CP Scenarios, O=Trust Community, C=DE`.
-   The ABAP system's SNC identity name is`p:CN=SID, O=Trust Community, C=DE`. This value can typically be found in the ABAP system instance profile parameter `snc/identity/as` and hence is provided per application server.
-   When using the SAP Cryptographic Library, we recommend that you use an ABAP system SNC identity and a Cloud Connector system identity signed by the same CA for mutual authentication.
-   The example short-lived certificate has the subject `CN=P1234567`, where `P1234567` is the SAP BTP application user.



<a name="loio33a2f37b0f1e4b6d869ab85c8427db1b__tasks"/>

## Tasks

1.  [Configure the ABAP System](configure-identity-propagation-for-rfc-33a2f37.md#loio33a2f37b0f1e4b6d869ab85c8427db1b__config_abap)
2.  [Map Short-Lived Certificates to Users](configure-identity-propagation-for-rfc-33a2f37.md#loio33a2f37b0f1e4b6d869ab85c8427db1b__map)
3.  [Configure the Cloud Connector](configure-identity-propagation-for-rfc-33a2f37.md#loio33a2f37b0f1e4b6d869ab85c8427db1b__config_scc)



<a name="loio33a2f37b0f1e4b6d869ab85c8427db1b__config_abap"/>

## 1. Configure the ABAP System to Trust the Cloud Connector's System SNC identity

1.  Open the *SNC Access Control List for Systems* \(transaction `SNC0`\).
2.  As the Cloud Connector does not have a system ID, use an arbitrary value for *<System ID\>* and enter it together with its SNC name: `p:CN=SCC, OU=SAP CP Scenarios, O=Trust Community, C=DE`.
3.  Save the entry and choose the *Details* button.
4.  In the next screen, activate the checkboxes for *Entry for RFC activated* and *Entry for certificate activated*.
5.  Save your settings.

Back to [Tasks](configure-identity-propagation-for-rfc-33a2f37.md#loio33a2f37b0f1e4b6d869ab85c8427db1b__tasks)

Back to [Example Data](configure-identity-propagation-for-rfc-33a2f37.md#loio33a2f37b0f1e4b6d869ab85c8427db1b__data)



<a name="loio33a2f37b0f1e4b6d869ab85c8427db1b__map"/>

## 2. Map Short-Lived Certificates to Users

You can do this manually in the system as described below or use an identity management solution for a more comfortable approach. For example, for large numbers of users the rule-based certificate mapping is a good way to save time and effort. See [Rule-Based Certificate Mapping](http://help.sap.com/saphelp_nw73ehp1/helpdata/en/c8/30fd902dc8473b9e59db1576cc784b/frameset.htm).

1.  Open *Assignment of External ID to Users* \(transaction `EXTID_DN`\).
2.  Switch to the edit mode.
3.  Create a new entry. Specify the subject of the certificate as `External ID`. Using the example data, this is CN=P1234567. In the *<User\>* field, provide an appropriate ABAP user, for example `JOHNDOE`.
4.  Save the mapping.
5.  Repeat the previous steps for all users that should be supported for the scenario.

Back to [Tasks](configure-identity-propagation-for-rfc-33a2f37.md#loio33a2f37b0f1e4b6d869ab85c8427db1b__tasks)

Back to [Example Data](configure-identity-propagation-for-rfc-33a2f37.md#loio33a2f37b0f1e4b6d869ab85c8427db1b__data)



<a name="loio33a2f37b0f1e4b6d869ab85c8427db1b__config_scc"/>

## 3. Configure the Cloud Connector

[Prerequisites](configure-identity-propagation-for-rfc-33a2f37.md#loio33a2f37b0f1e4b6d869ab85c8427db1b__prereq)

[Set up the Cloud Connector to Use the SNC Implementation](configure-identity-propagation-for-rfc-33a2f37.md#loio33a2f37b0f1e4b6d869ab85c8427db1b__setup)

[Create an RFC Hostname Mapping](configure-identity-propagation-for-rfc-33a2f37.md#loio33a2f37b0f1e4b6d869ab85c8427db1b__create)

**Prerequisites**

-   The required security product for the SNC flavor that is used by your ABAP back-end systems, is installed on the Cloud Connector host.
-   The Cloud Connector's system SNC identity is associated with the operating system user under which the Cloud Connector process is running.

    > ### Note:  
    > If you use SAP Cryptographic Library as SNC implementation, follow the steps described in [Initial Configuration \(RFC\)](initial-configuration-rfc-f09eefe.md). Additionally, SAP note [2642538](https://me.sap.com/notes/2642538) provides a good description to associate an SNC identity of SAP Cryptographic Library with a user running an external program that uses JCo. When using a different SNC offering, get in touch with the SNC library vendor for details.


Back to [Step](configure-identity-propagation-for-rfc-33a2f37.md#loio33a2f37b0f1e4b6d869ab85c8427db1b__config_scc)

**Set up the Cloud Connector to Use the SNC Implementation**

1.  In the Cloud Connector UI, choose *Configuration* from the main menu, select the *On Premise* tab, and go to the *SNC* section.
2.  Provide the fully qualified name of the SNC library \(the security product's shared library implementing the GSS API\), the SNC name of the above system identity, and the desired quality of protection by choosing the *Edit* icon.

    For more information, see [Initial Configuration \(RFC\)](initial-configuration-rfc-f09eefe.md).

    > ### Note:  
    > The example in [Initial Configuration \(RFC\)](initial-configuration-rfc-f09eefe.md) shows the library location if you use the SAP Secure Login Client as your SNC security product. In this case \(as well as for some other security products\), *SNC My Name* is optional, because the security product automatically uses the identity associated with the current operating system user under which the process is running, so you can leave that field empty. \(Otherwise, in this example it should be filled with `p:CN=SCC, OU=SAP CP Scenarios, O=Trust Community, C=DE`.\)
    > 
    > We recommend that you enter `Maximum Protection` for *<Quality of Protection\>*, if your security solution supports it, as it provides the best protection.

3.  Choose *Save* and *Close*.

Back to [Step](configure-identity-propagation-for-rfc-33a2f37.md#loio33a2f37b0f1e4b6d869ab85c8427db1b__config_scc)

**Create an RFC Hostname Mapping**

1.  In the *Access Control* section of the Cloud Connector, create a hostname mapping corresponding to the cloud-side RFC destination. See [Configure Access Control \(RFC\)](configure-access-control-rfc-ca58689.md).
2.  Make sure you choose `RFC SNC` as *<Protocol\>* and `ABAP System` as *<Back-end Type\>*. In the *<SNC Partner Name\>* field, enter the ABAP system's SNC identitiy name, for example, `p:CN=SID, O=Trust Community, C=DE`.
3.  Save your mapping.

Back to [Step](configure-identity-propagation-for-rfc-33a2f37.md#loio33a2f37b0f1e4b6d869ab85c8427db1b__config_scc)

Back to [Tasks](configure-identity-propagation-for-rfc-33a2f37.md#loio33a2f37b0f1e4b6d869ab85c8427db1b__tasks)

Back to [Example Data](configure-identity-propagation-for-rfc-33a2f37.md#loio33a2f37b0f1e4b6d869ab85c8427db1b__data)



<a name="loio33a2f37b0f1e4b6d869ab85c8427db1b__section_pb3_nwx_jgb"/>

## Related Information

[Secure Network Communications \(SNC\)](https://help.sap.com/viewer/e73bba71770e4c0ca5fb2a3c17e8e229/7.52.3/en-US/e656f466e99a11d1a5b00000e835363f.html)

[Using the SAP Cryptographic Library for SNC](https://help.sap.com/viewer/e73bba71770e4c0ca5fb2a3c17e8e229/7.52.3/en-US/32431c3aadda4f25e10000000a11402f.html)

[Rule-Based Mapping of Certificates](rule-based-mapping-of-certificates-4f8540f.md)

[Principal Propagation](principal-propagation-e2cbb48.md) \(multi-cloud environment\)

[Principal Propagation](https://help.sap.com/viewer/b865ed651e414196b39f8922db2122c7/Cloud/en-US/d4d3e1e9b2dd44318b49a4812cd51383.html "Forward the identity of cloud users to an on-premise system to enable single sign-on (Neo environment).") :arrow_upper_right: \(Neo environment\)

