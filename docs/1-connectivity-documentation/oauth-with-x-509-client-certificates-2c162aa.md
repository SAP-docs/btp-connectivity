<!-- loio2c162aaa9e464480b2307879d1b865f5 -->

# OAuth with X.509 Client Certificates

Use an X.509 certificate instead of a secret to authenticate against the authentication server.

> ### Caution:  
> OAuth with X.509 is only supported for *<ProxyType\>*=`Internet`.

To perform mutual TLS, you can use an X.509 client certificate instead of a client secret when connecting to the authorization server. To do so, you must create a certificate configuration containing a valid X.509 client certificate or a keystore, and link it to the destination configuration using these properties:



## Properties


<table>
<tr>
<th valign="top">

Cockpit Label

</th>
<th valign="top">

JSON Key

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top" colspan="3">

**Optional**

</td>
</tr>
<tr>
<td valign="top">

Token Service Key Store Location

</td>
<td valign="top">

`tokenService.KeyStoreLocation` 

</td>
<td valign="top">

Contains the name of the certificate configuration to be used. This property is required.

</td>
</tr>
<tr>
<td valign="top">

Token Service Key Store Password

</td>
<td valign="top">

`tokenService.KeyStorePassword`

</td>
<td valign="top">

Contains the password for the certificate configuration \(if one is needed\).

</td>
</tr>
</table>

> ### Caution:  
> Mutual TLS with an X.509 client certificate is performed only if the `tokenService.KeyStoreLocation` property is set in the destination configuration. Otherwise, the client secret is used.



<a name="loio2c162aaa9e464480b2307879d1b865f5__section_tzz_zph_n4b"/>

## Supported Certificate Configuration Formats

-   Java Keystore \(.jks\): Requires the `tokenService.KeyStorePassword` property.
-   PKCS12 \(.pfx or .p12\): Requires the `tokenService.KeyStorePassword` property.
-   PEM-encoded X.509 client certificate and private key \(.crt, .cer and .pem\): The certificate configuration can contain several valid X.509 certificates and private keys.



<a name="loio2c162aaa9e464480b2307879d1b865f5__section_u42_1qh_n4b"/>

## Supported OAuth Flows

-   [OAuth Client Credentials Authentication](oauth-client-credentials-authentication-4e1d742.md)
-   [OAuth Password Authentication](oauth-password-authentication-452357c.md)
-   [OAuth User Token Exchange Authentication](oauth-user-token-exchange-authentication-e3c333f.md)
-   [OAuth JWT Bearer Authentication](oauth-jwt-bearer-authentication-283cd2d.md)
-   [OAuth SAML Bearer Assertion Authentication](oauth-saml-bearer-assertion-authentication-c69ea6a.md)

