<!-- loio4e13a04147314e8e9e54321f25d93fdc -->

# Client Certificate Authentication

Create and configure a *Client Certificate* destination for an application.

This authentication type is used for destinations that refer to a service on the Internet or a *Private Link* endpoint. The relevant property value is:


<table>
<tr>
<td valign="top">

`Authentication`=`ClientCertificateAuthentication`

</td>
</tr>
</table>

The following credentials must be specified:


<table>
<tr>
<th valign="top">

Property

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`KeyStore.Source`

</td>
<td valign="top">

Optional. Specifies the storage location of the certificate to be used by the client. Supported values are:

-   `ClientProvided`: The key store is managed by the client \(the application itself\).
-   `DestinationService`: The key store is managed by the Destination service.

If the property is not set, the key store is managed by the Destination service \(default\).

</td>
</tr>
<tr>
<td valign="top">

`KeyStoreLocation` 

</td>
<td valign="top">

The name of the key store file that contains the client certificate\(s\) for client certificate authentication against a remote server. This property is optional if `KeyStore.Source` is set to `ClientProvided`.

</td>
</tr>
<tr>
<td valign="top">

`KeyStorePassword` 

</td>
<td valign="top">

Password for the key store file specified by `KeyStoreLocation`. This property is optional if `KeyStoreLocation` is used in combination with `KeyStore.Source`, and `KeyStore.Source` is set to `ClientProvided`.

</td>
</tr>
</table>

> ### Note:  
> You can upload `KeyStore` JKS files using the same command for uploading destination configuration property file. You only need to specify the JKS file instead of the destination configuration file.

**Related Information**  


[Server Certificate Authentication](server-certificate-authentication-e75d7f1.md "Create and configure a Server Certificate destination for an application.")

