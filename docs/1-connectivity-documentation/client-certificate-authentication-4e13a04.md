<!-- loio4e13a04147314e8e9e54321f25d93fdc -->

# Client Certificate Authentication

Create and configure a *Client Certificate* destination for an application.

> ### Caution:  
> In the cockpit, this authentication type is shown in the selection list only if you have entered a URL that starts with `https://`.

To configure a destination of this authentication type, you must specify all the required properties.


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

**Required**

</td>
</tr>
<tr>
<td valign="top">

Name

</td>
<td valign="top">

`Name`

</td>
<td valign="top">

Destination name. Must be unique for the destination level.

</td>
</tr>
<tr>
<td valign="top">

Type

</td>
<td valign="top">

`Type`

</td>
<td valign="top">

Destination type. Use `HTTP` as value for all HTTP\(S\) destinations.

</td>
</tr>
<tr>
<td valign="top">

URL

</td>
<td valign="top">

`URL`

</td>
<td valign="top">

URL of the target endpoint.

</td>
</tr>
<tr>
<td valign="top">

Proxy Type

</td>
<td valign="top">

`ProxyType`

</td>
<td valign="top">

`Internet`, `OnPremise`, or `PrivateLink`.

</td>
</tr>
<tr>
<td valign="top">

Authentication

</td>
<td valign="top">

`Authentication`

</td>
<td valign="top">

Authentication type. Use `ClientCertificateAuthentication` as value.

</td>
</tr>
<tr>
<td valign="top" colspan="3">

**Optional**

</td>
</tr>
<tr>
<td valign="top">

Key Store Source

</td>
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

Key Store Location

</td>
<td valign="top">

`KeyStoreLocation` 

</td>
<td valign="top">

The name of the key store file that contains the client certificate\(s\) for client certificate authentication against a remote server. This property is optional if `KeyStore.Source` is set to `ClientProvided`.

</td>
</tr>
<tr>
<td valign="top">

Key Store Password

</td>
<td valign="top">

`KeyStorePassword` 

</td>
<td valign="top">

Password for the key store file specified by `KeyStoreLocation`. Can be set empty.

</td>
</tr>
<tr>
<td valign="top">

Trust Store Location

</td>
<td valign="top">

`TrustStoreLocation` 

</td>
<td valign="top">

Path to the keystore file which contains trusted certificates \(Certificate Authorities\) for authentication against a remote client.

-   When using a local environment: The relative path to the JKS file. The root path is the server's location on the file system.
-   When using a cloud environment: The name of the JKS file.

Only shown and required if the default clilent trust store is not used.

> ### Note:  
> The default JDK truststore is appended to the truststore defined in the destination configuration. As a result, the destination simultaneously uses both truststores. If the `TrustStoreLocation` property is not specified, the JDK truststore is used as a default truststore for the destination.



</td>
</tr>
<tr>
<td valign="top">

Trust Store Password

</td>
<td valign="top">

`TrustStorePassword` 

</td>
<td valign="top">

Only shown if the default clilent trust store is not used. Can be set empty.

</td>
</tr>
</table>

> ### Note:  
> You can upload `KeyStore` files using the same command for uploading destination configuration property file. You only need to specify the `KeyStore` file instead of the destination configuration file.
> 
> For more information on supported file formats, see [Manage Destination Certificates](manage-destination-certificates-df1bb55.md).

**Related Information**  


[Server Certificate Authentication](server-certificate-authentication-e75d7f1.md "Create and configure a Server Certificate destination for an application.")

