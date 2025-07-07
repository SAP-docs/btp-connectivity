<!-- loio007e40560d7a4a7b846d1eaeb44f8e94 -->

# Certificate Types

Find information on different certificate types you can use to configure destinations in your SAP BTP subaccount.


<table>
<tr>
<th valign="top">

Certificate Type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

Single \(X.509\) Certificate

</td>
<td valign="top">

Binds an identity to a public key using a digital signature. A certificate contains an identity \(hostname, organization, or individual\) and a public key. It is either signed by a certificate authority or is self-signed.

Supported file formats: PEM, CER, CRT

</td>
</tr>
<tr>
<td valign="top">

Key Store Certificate

</td>
<td valign="top">

Certificate stored in a key store repository, containing the public and private key of the certificate.

Supported file formats: JKS, PFX, P12

> ### Restriction:  
> Key stores are not supported in environments based on FIPS \(*Federal Information Processing Standard*\).



</td>
</tr>
</table>

