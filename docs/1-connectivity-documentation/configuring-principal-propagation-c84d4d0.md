<!-- loioc84d4d0b12d34890b334998185f49e88 -->

# Configuring Principal Propagation

Use principal propagation to simplify the access of SAP BTP users to on-premises systems.

Tasks in this section:


<table>
<tr>
<th valign="top">

Task

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

[Set Up Trust](set-up-trust-a4ee70f.md) 

</td>
<td valign="top">

Configure a trusted relationship in the Cloud Connector to support principal propagation. Principal propagation lets you forward the logged-on identity in the cloud to the internal system without requesting a password.

</td>
</tr>
<tr>
<td valign="top">

[Configure a CA Certificate](configure-a-ca-certificate-d0c4d56.md) 

</td>
<td valign="top">

Install and configure an X.509 certificate to enable support for principal propagation.

</td>
</tr>
<tr>
<td valign="top">

[Configuring Identity Propagation to an ABAP System](configuring-identity-propagation-to-an-abap-system-6705cc3.md) 

</td>
<td valign="top">

Learn more about the different types of configuring and supporting principal propagation for a particular AS ABAP.

</td>
</tr>
<tr>
<td valign="top">

[Configure Subject Patterns](configure-subject-patterns-58803a2.md) 

</td>
<td valign="top">

Define a pattern identifying the user for the subject of the generated short-lived `X.509` certificate, as well as its validity period.

</td>
</tr>
<tr>
<td valign="top">

[Configure a Secure Login Server](configure-a-secure-login-server-de5bbf9.md) 

</td>
<td valign="top">

Configuration steps for Java Secure Login Server \(SLS\) support.

</td>
</tr>
<tr>
<td valign="top">

[Configure Kerberos](configure-kerberos-f2339d8.md) 

</td>
<td valign="top">

The Cloud Connector lets you propagate users authenticated in SAP BTP via Kerberos against back-end systems. It uses the **Service For User and Constrained Delegation** protocol extension of Kerberos.

</td>
</tr>
<tr>
<td valign="top">

[Configuring Identity Propagation to SAP NetWeaver AS for Java](configuring-identity-propagation-to-sap-netweaver-as-for-java-2e96287.md)

</td>
<td valign="top">

Find step-by-step instructions on how to configure principal propagation to an application server Java \(AS Java\).

</td>
</tr>
</table>



<a name="loioc84d4d0b12d34890b334998185f49e88__section_wkz_qft_ngb"/>

## Related Information

[Principal Propagation](principal-propagation-e2cbb48.md)\(multi-cloud environment\)

[Principal Propagation](https://help.sap.com/viewer/b865ed651e414196b39f8922db2122c7/Cloud/en-US/d4d3e1e9b2dd44318b49a4812cd51383.html "Forward the identity of cloud users to an on-premise system to enable single sign-on (Neo environment).") :arrow_upper_right: \(Neo environment\)

