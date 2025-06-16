<!-- loiob62e588470504a7f95df48c28265dd34 -->

# Configuring Technical User Propagation

Use technical user propagation to provide access of technical users to on-premises systems.

Using technical user propagation, you can forward the identity of technical users that are identified using an OAuth client and act on behalf of this identity in an on-premises system.

> ### Note:  
> Technical user propagation is possible only in the Cloud Foundry environment.

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

Configure a trusted relationship in the Cloud Connector to support technical user propagation. Technical user propagation lets you forward a technical user in the cloud to the internal system without requesting a password.

</td>
</tr>
<tr>
<td valign="top">

[Configure a CA Certificate](configure-a-ca-certificate-d0c4d56.md) 

</td>
<td valign="top">

Install and configure an X.509 certificate to enable support for technical user propagation.

</td>
</tr>
<tr>
<td valign="top">

[Configuring Identity Propagation to an ABAP System](configuring-identity-propagation-to-an-abap-system-6705cc3.md) 

</td>
<td valign="top">

Learn more about the different types of configuring and supporting technical user propagation for a particular AS ABAP.

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

The Cloud Connector lets you propagate users authenticated in SAP BTP via Kerberos against backend systems. It uses the **Service For User and Constrained Delegation** protocol extension of Kerberos.

</td>
</tr>
<tr>
<td valign="top">

[Configuring Identity Propagation to SAP NetWeaver AS for Java](configuring-identity-propagation-to-sap-netweaver-as-for-java-2e96287.md)

</td>
<td valign="top">

Find step-by-step instructions on how to configure technical user propagation to an application server Java \(AS Java\).

</td>
</tr>
</table>

**Related Information**  


[OAuth Technical User Propagation Authentication](oauth-technical-user-propagation-authentication-8634e21.md "Learn about the OAuth2TechnicalUserPropagation authentication type for HTTP destinations: use cases, supported properties and examples.")

