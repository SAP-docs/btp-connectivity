<!-- loio4e13a04147314e8e9e54321f25d93fdc -->

# Client Authentication Types for HTTP Destinations

Find details about client authentication types for HTTP destinations.



<a name="loio4e13a04147314e8e9e54321f25d93fdc__section_N10017_N10011_N10001"/>

## Context

This section lists the supported client authentication types and the relevant supported properties.



<a name="loio4e13a04147314e8e9e54321f25d93fdc__section_EB93679A17BA40F4A1E1023D10A27D04"/>

## No Authentication

This authentication type is used for destinations that refer to a service on the Internet, an on-premise system, or a *Private Link* endpoint that does not require authentication. The relevant property value is:


<table>
<tr>
<td valign="top">

`Authentication`=`NoAuthentication`

</td>
</tr>
</table>



> ### Note:  
> When a destination is using HTTPS protocol to connect to a Web resource, the JDK truststore is used as truststore for the destination.



<a name="loio4e13a04147314e8e9e54321f25d93fdc__section_0DE472D20F72416BAC5DEEDE623FE331"/>

## Basic Authentication

Used for destinations that refer to a service on the Internet, an on-premise system, or a *Private Link* endpoint that requires basic authentication. The relevant property value is:


<table>
<tr>
<td valign="top">

`Authentication`=`BasicAuthentication`

</td>
</tr>
</table>



The following credentials need to be specified:

> ### Caution:  
> Do not use your *own personal credentials* in the *<User\>* and *<Password\>* fields. Always use a *technical user* instead.


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

`User` 

</td>
<td valign="top">

User name of the technical user to be used.

</td>
</tr>
<tr>
<td valign="top">

`Password` 

</td>
<td valign="top">

Password of the technical user to be used.

</td>
</tr>
<tr>
<td valign="top">

`Preemptive` 

</td>
<td valign="top">

If this property is not set or is set to `TRUE` \(that is, the default behavior is to use preemptive sending\), the authentication token is sent preemptively. Otherwise, it relies on the challenge from the server \(401 HTTP code\). The default value \(used if no value is explicitly specified\) is `TRUE`. For more information about preemptiveness, see [http://tools.ietf.org/html/rfc2617\#section-3.3](http://tools.ietf.org/html/rfc2617#section-3.3).

</td>
</tr>
</table>

> ### Note:  
> When a destination is using the HTTPS protocol to connect to a Web resource, the JDK truststore is used as truststore for the destination.

> ### Note:  
> `Basic Authentication` and `No Authentication` can be used in combination with `ProxyType`=`OnPremise`. In this case, also the `CloudConnectorLocationId` property can be specified. You can connect multiple Cloud Connectors to a subaccount as long as their location ID is different. The value defines the location ID identifying the Cloud Connector over which the connection shall be opened. The default value is the empty string identifying the Cloud Connector that is connected without any location ID.

The response for "find destination" contains an `authTokens` object in the format given below. For more information on the fields in `authTokens`, see ["Find a Destination" Response Structure](find-a-destination-response-structure-83a3f3b.md).

> ### Sample Code:  
> ```
> "authTokens": [
>     {
>         "type": "Basic",
>         "value": "dGVzdDpwYXNzMTIzNDU=",
>         "http_header": {
>             "key":"Authorization",
>             "value":"Basic dGVzdDpwYXNzMTIzNDU="
>         }
>     }
> ]
> ```



<a name="loio4e13a04147314e8e9e54321f25d93fdc__clientCert"/>

## Client Certificate Authentication

Used for destinations that refer to a service on the Internet or a *Private Link* endpoint. The relevant property value is:


<table>
<tr>
<td valign="top">

`Authentication`=`ClientCertificateAuthentication`

</td>
</tr>
</table>

The following credentials need to be specified:


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



## Configuration

-   [Managing Destinations](managing-destinations-84e45e0.md)

**Related Information**  


[Server Certificate Authentication](server-certificate-authentication-e75d7f1.md "Create and configure a Server Certificate destination for an application.")

