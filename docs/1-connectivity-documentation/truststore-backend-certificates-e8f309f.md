<!-- loioe8f309f6f28b45a9afe342a6e515f3fc -->

# Truststore Backend Certificates

Manage backend certificates in the truststore via API.



<a name="loioe8f309f6f28b45a9afe342a6e515f3fc__section_rcp_l1b_vcb"/>

## Get Truststore Configuration

> ### Note:  
> This API is available as of Cloud Connector version 2.15.0.


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/onPremise/truststore` 

</td>
</tr>
<tr>
<td valign="top">

Method

</td>
<td valign="top">

*GET* 

</td>
</tr>
<tr>
<td valign="top">

Header

</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

Response

</td>
<td valign="top">

```
{trustAllBackends, trustedBackends}
```



</td>
</tr>
<tr>
<td valign="top">

Errors

</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

Roles

</td>
<td valign="top">

Administrator, Subaccount Administrator, Display, Support

</td>
</tr>
</table>

**Response Properties:**

-   `trustAllBackends`: flag \(boolean\) indicating whether all backends are trusted \(`true`\), or only the backends represented by certificates are trusted \(`false`\).
-   `trustedBackendSystems`: list \(array\) of certificates representing the trusted backends. Each certificate is specified through an object with the following properties:

**Certificate Properties:**

-   `alias`: alias of CA certificate \(a string\).
-   `subjectDN`: subject DN \(a string\).
-   `issuer`: the issuer \(a string\).
-   `notAfterTimeStamp`: \(a UTC long number\).

> ### Note:  
> No HTTP requests can be executed if `trustAllBackends` is `false` and the certificate list as per `trustedBackendSystems` is empty.



## Example

```
curl -i -k -u <user>:<password> -X GET https://<host>:<port>/api/v1/configuration/connector/onPremise/truststoreConfiguration
```



<a name="loioe8f309f6f28b45a9afe342a6e515f3fc__section_vkf_13d_s5b"/>

## Change Truststore Configuration \(Master Only\)

> ### Note:  
> This API is available as of Cloud Connector version 2.15.0.


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/onPremise/truststore` 

</td>
</tr>
<tr>
<td valign="top">

Method

</td>
<td valign="top">

*PATCH* 

</td>
</tr>
<tr>
<td valign="top">

Header

</td>
<td valign="top">

Accept: application/json

</td>
</tr>
<tr>
<td valign="top">

Request

</td>
<td valign="top">

```
{trustAllBackends}
```



</td>
</tr>
<tr>
<td valign="top">

Response

</td>
<td valign="top">

204 on success

</td>
</tr>
<tr>
<td valign="top">

Errors

</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

Roles

</td>
<td valign="top">

Administrator

</td>
</tr>
</table>

**Request Properties:**

-   `trustAllBackends`: flag \(boolean\) indicating whether all backends are trusted \(`true`\), or only the backends represented by certificates are trusted \(`false`\)

> ### Caution:  
> We discourage trusting all backends and recommend that you trust only specific backends represented by their respective certificates.



## Example

```
curl -k -u <user>:<password> -X PATCH  -H "Accept: application/json" -d '{"trustAllBackends": true}' https://<host>:<port>/api/v1/configuration/connector/onPremise/truststore
```



<a name="loioe8f309f6f28b45a9afe342a6e515f3fc__section_wpj_r4x_ycc"/>

## Add a Backend Certificate to Truststore \(Master Only\)

> ### Note:  
> This API is available as of Cloud Connector version 2.18.0.


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/onPremise/truststore/certificates` 

</td>
</tr>
<tr>
<td valign="top">

Method

</td>
<td valign="top">

*POST* 

</td>
</tr>
<tr>
<td valign="top">

Header

</td>
<td valign="top">

CONTENT\_TYPE: multipart/form-data

</td>
</tr>
<tr>
<td valign="top">

Request

</td>
<td valign="top">

```
multipart/form-data with the following form parameter: certificate
```



</td>
</tr>
<tr>
<td valign="top">

Response

</td>
<td valign="top">

201 on success

</td>
</tr>
<tr>
<td valign="top">

Errors

</td>
<td valign="top">

INVALID\_REQUEST

</td>
</tr>
<tr>
<td valign="top">

Roles

</td>
<td valign="top">

Administrator

</td>
</tr>
</table>

**Request Properties:**

-   `certificates`: one or more certificates in DER or PEM format.

**Errors:**

-   INVALID\_REQUEST: if one of the certificates is already available.

> ### Note:  
> Prior to version 2.18, only *one* certificate was supported by that API with the parameter `certificate`. For compatibility reasons, this parameter is still supported. However, it should not be used anymore.



## Example

```
curl -k -u <user>:<password> --request POST -F 'certificates=@<file>' https://<host>:<port>/api/v1/configuration/connector/onPremise/truststore/certificates
```



<a name="loioe8f309f6f28b45a9afe342a6e515f3fc__section_ddp_xfd_5cc"/>

## Download All Backend Certificates From Truststore \(Master Only\)

> ### Note:  
> This API is available as of Cloud Connector version 2.18.0.


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/onPremise/truststore/certificates` 

</td>
</tr>
<tr>
<td valign="top">

Method

</td>
<td valign="top">

*GET* 

</td>
</tr>
<tr>
<td valign="top">

Header

</td>
<td valign="top">

Accept: application/x-pem-file

Accept: application/pkix-cert

</td>
</tr>
<tr>
<td valign="top">

Request

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Response

</td>
<td valign="top">

CA certificate in binary format

</td>
</tr>
<tr>
<td valign="top">

Errors

</td>
<td valign="top">

NOT\_FOUND

</td>
</tr>
<tr>
<td valign="top">

Roles

</td>
<td valign="top">

Administrator, Subaccount Administrator, Support

</td>
</tr>
</table>

**Request Header:**

-   `Accept: application/pkix-cert` forces binary output containing the specified certificates.

**Errors:**

-   NOT\_FOUND: if a certificate with a given alias is not available.



## Example

```
curl -k -u <user>:<password> --request GET  -H "Accept: application/x-pem-file" --output <pem file> https://<host>:<port>/api/v1/configuration/connector/onPremise/truststore/certificates
```



<a name="loioe8f309f6f28b45a9afe342a6e515f3fc__section_p4d_5wv_tcc"/>

## Download a Backend Certificate From Truststore \(Master Only\)

> ### Note:  
> This API is available as of Cloud Connector version 2.18.0.


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/onPremise/truststore/certificates/<alias>` 

</td>
</tr>
<tr>
<td valign="top">

Method

</td>
<td valign="top">

*GET* 

</td>
</tr>
<tr>
<td valign="top">

Header

</td>
<td valign="top">

Accept: application/pkix-cert

</td>
</tr>
<tr>
<td valign="top">

Request

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Response

</td>
<td valign="top">

CA certificate in binary format

</td>
</tr>
<tr>
<td valign="top">

Errors

</td>
<td valign="top">

NOT\_FOUND

</td>
</tr>
<tr>
<td valign="top">

Roles

</td>
<td valign="top">

Administrator, Subaccount Administrator, Support

</td>
</tr>
</table>

**Request Header:**

-   `Accept: application/pkix-cert` forces binary output containing the specified certificate.

**Errors:**

-   NOT\_FOUND: if the certificate with the given alias is not available.



## Example

```
curl -k -u <user>:<password> --request GET  -H "Accept: application/pkix-cert" --output <cert file> https://<host>:<port>/api/v1/configuration/connector/onPremise/truststore/certificates/<alias>
```



<a name="loioe8f309f6f28b45a9afe342a6e515f3fc__section_snl_13d_s5b"/>

## Delete a Backend Certificate From Truststore \(Master Only\)

> ### Note:  
> This API is available as of Cloud Connector version 2.15.0.


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/onPremise/truststore/certificates/<alias>` 

</td>
</tr>
<tr>
<td valign="top">

Method

</td>
<td valign="top">

*DELETE* 

</td>
</tr>
<tr>
<td valign="top">

Header

</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

Response

</td>
<td valign="top">

204 on success

</td>
</tr>
<tr>
<td valign="top">

Errors

</td>
<td valign="top">

NOT\_FOUND

</td>
</tr>
<tr>
<td valign="top">

Roles

</td>
<td valign="top">

Administrator

</td>
</tr>
</table>

**Errors:**

-   NOT\_FOUND: if the certificate with the given alias is not available.



## Example

```
curl -k -H "Accept: application/json" -u <user>:<password> --request DELETE https://<host>:<port>/api/v1/configuration/connector/onPremise/truststore/certificates/<alias>
```



<a name="loioe8f309f6f28b45a9afe342a6e515f3fc__section_akp_13d_s5b"/>

## Delete All CA Backend From Truststore \(Master Only\)

> ### Note:  
> This API is available as of Cloud Connector version 2.15.0.


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/onPremise/truststore/certificates` 

</td>
</tr>
<tr>
<td valign="top">

Method

</td>
<td valign="top">

*DELETE* 

</td>
</tr>
<tr>
<td valign="top">

Header

</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

Response

</td>
<td valign="top">

204 on success

</td>
</tr>
<tr>
<td valign="top">

Errors

</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

Roles

</td>
<td valign="top">

Administrator

</td>
</tr>
</table>



## Example

```
curl -k -H "Accept: application/json" -u <user>:<password> --request DELETE https://<host>:<port>/api/v1/configuration/connector/onPremise/truststore/certificates
```

