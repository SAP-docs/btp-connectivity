<!-- loioe75d7f15b808428e87ae70f494da0b42 -->

# Server Certificate Authentication

Create and configure a *Server Certificate* destination for an application.



<a name="loioe75d7f15b808428e87ae70f494da0b42__section_N10017_N10011_N10001"/>

## Context

The server certificate validation is applicable to all destinations with proxy type `Internet` and `PrivateLink` that use the HTTPS protocol.



<a name="loioe75d7f15b808428e87ae70f494da0b42__section_N10024_N10011_N10001"/>

## Properties

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

**Optional**

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

Password for the JKS trust store file. This property is mandatory if `TrustStoreLocation` is used.

</td>
</tr>
<tr>
<td valign="top" colspan="3">

**Additional**

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

**Key**

</td>
<td valign="top">

**Description**

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

`TrustAll`

</td>
<td valign="top">

If this property is set to `TRUE` in the destination, the server certificate will not be checked for SSL connections. It is intended for test scenarios only, and should not be used in production \(since the SSL server certificate is not checked, the server is not authenticated\). The possible values are `TRUE` or `FALSE`; the default value is `FALSE` \(that is, if the property is not present at all\).

If `TrustAll` = `TRUE`, the `TrustStoreLocation` property is ignored so you can omit it.

If `TrustAll` = `FALSE`, the `TrustStoreLocation` property is mandatory to be used.

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

`HostnameVerifier`

</td>
<td valign="top">

Optional property. It has two values: `Strict` and `BrowserCompatible`. This property specifies how the server hostname matches the names stored inside the server's X.509 certificate. This verifying process is only applied if TLS or SSL protocols are used and is not applied if the `TrustAll` property is specified. The default value \(used if no value is explicitly specified\) is `Strict`.

-   `Strict HostnameVerifier` works in the same way as Oracle Java 1.4, Oracle Java 5, and Oracle Java 6-rc. It is also similar to Microsoft Internet Explorer 6. This implementation appears to be compliant with RFC 2818 for dealing with wildcards. A wildcard such as "\*.foo.com" matches only subdomains at the same level, for example "a.foo.com". It does not match deeper subdomains such as "a.b.foo.com".

-   `BrowserCompatible HostnameVerifier` works in the same way as Curl and Mozilla Firefox. The hostname must match either the first common name \(CN\) or any of the subject-alts. A wildcard can occur in the CN and in any of the subject-alts.


The only difference between `BrowserCompatible` and `Strict` is that a wildcard \(such as ".foo.com"\) with `BrowserCompatible` matches all subdomains, including "a.b.foo.com".

For more information about these Java classes, see [Package org.apache.http.conn.ssl](http://hc.apache.org/httpcomponents-client-ga/httpclient/apidocs/org/apache/http/conn/ssl/package-summary.html).



If *<TrustAll\>* = `TRUE`, the *<HostnameVerifier\>* property is ignored so you can omit it.

</td>
</tr>
</table>

> ### Note:  
> Connections to remote services which require *Java Cryptography Extension \(JCE\) unlimited strength jurisdiction policy* are not supported.



## Configuration

-   [Managing Destinations](managing-destinations-84e45e0.md)

**Related Information**  


[Client Certificate Authentication](client-certificate-authentication-4e13a04.md "Create and configure a Client Certificate destination for an application.")

