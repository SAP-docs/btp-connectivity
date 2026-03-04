<!-- loio236c0842c2cf48238b919d8f95a5afac -->

# System Certificate APIs

Manage a system certificate via API.

> ### Note:  
> The APIs below are available as of Cloud Connector version 2.13.0.

> ### Caution:  
> The path component *onPremises* of the URI is available as of version 2.18.0. Older versions must use *onPremise*. The latter is currently accepted by all versions, but we recommend that you use *onPremises* as *onPremise* may be discontinued at some point.



<a name="loio236c0842c2cf48238b919d8f95a5afac__section_rcp_l1b_vcb"/>

## Get Description for a System Certificate


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/onPremises/systemCertificate` 

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

Accept: application/json

</td>
</tr>
<tr>
<td valign="top">

Response

</td>
<td valign="top">

```
{subjectDN, issuer, notBeforeTimeStamp, notAfterTimeStamp, subjectAltNames}

```



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

Administrator, Associate Administrator, Subaccount Administrator, Display, Support, Monitoring

</td>
</tr>
</table>

**Response Properties:**

-   `subjectDN`: the subject distinguished name \(a string\)
-   `issuer`: the issuer \(a string\)
-   `notBeforeTimeStamp`: timestamp of the beginning of the validity period \(a UTC long number\)
-   `notAfterTimeStamp`: timestamp of the end of the validity period \(a UTC long number\)
-   `subjectAltNames`: subject alternative names.

**Errors:**

-   `NOT_FOUND` \(404\): there is no system certificate.

> ### Note:  
> `subjectAltNames` is not present if there are no subject alternative names.



## Example

```
curl -i -k -H "Accept: application/json" -u <user>:<password> -X GET  https://<host>:<port>/api/v1/configuration/connector/onPremises/systemCertificate
```



<a name="loio236c0842c2cf48238b919d8f95a5afac__section_lys_l1b_vcb"/>

## Get Binary Content of a System Certificate


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/onPremises/systemCertificate` 

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

Response

</td>
<td valign="top">

Binary data of the certificate.

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

Administrator, Associate Administrator, Subaccount Administrator, Display, Support, Monitoring

</td>
</tr>
</table>

**Response:**

-   `Success`: the binary data of the certificate; you can verify the downloaded certificate by storing it in file `sys.crt`, for instance, and then running

    ```
    keytool -printcert -file sys.crt
    ```

-   `Failure`: an error in the usual JSON format; the content type of the response is *application/json* in this case.

**Errors:**

-   `NOT_FOUND` \(404\): there is no system certificate.



## Example

```
curl -i -k -H "Accept: application/pkix-cert" -u <user>:<password> -X GET --output sys.crt https://<host>:<port>/api/v1/configuration/connector/onPremises/systemCertificate

```



<a name="loio236c0842c2cf48238b919d8f95a5afac__section_j4c_12b_vcb"/>

## Create a Self-Signed System Certificate \(Master Only\)


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/onPremises/systemCertificate` 

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

CONTENT\_TYPE: application/json

</td>
</tr>
<tr>
<td valign="top">

Request

</td>
<td valign="top">

```
{type, keySize, subjectDN}
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



</td>
</tr>
<tr>
<td valign="top">

Roles

</td>
<td valign="top">

Administrator, Associate Administrator

</td>
</tr>
</table>

**Request Properties:**

-   `type`: the string *selfsigned*
-   `keySize`: Key size, which must be either 2048 or 4096 bits. Optional property. Default value is 4096.

    > ### Note:  
    > This property is available as of version 2.15.0.

-   `subjectDN`: the subject distinguished name \(a string\)
-   `subjectAltNames`: subject alternative names. This property is optional. As of version 2.16.1, the value is ignored. SAN on system certificate had never any effect.

The certificate created this way has a validity of 1 year.



## Example

```
curl -i -k -H "Accept: application/json" -H "Content-Type: application/json" -u <user>:<password> -X POST --data '{"type":"selfsigned", "subjectDN":"CN=me"}'  https://<host>:<port>/api/v1/configuration/connector/onPremises/systemCertificate

```



<a name="loio236c0842c2cf48238b919d8f95a5afac__section_ld3_5zz_c4b"/>

## Create a Certificate Signing Request for a System Certificate \(Master Only\)


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/onPremises/systemCertificate` 

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

CONTENT\_TYPE: application/json

</td>
</tr>
<tr>
<td valign="top">

Request

</td>
<td valign="top">

```
{type, keySize, subjectDN}
```



</td>
</tr>
<tr>
<td valign="top">

Response

</td>
<td valign="top">

PEM-encoded certificate request

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

Administrator, Associate Administrator

</td>
</tr>
</table>

**Request Properties:**

-   `type`: the string *csr*
-   `keySize`: Key size, which must be either 2048 or 4096 bits. Optional property. Default value is 4096.

    > ### Note:  
    > This property is available as of version 2.15.0.

-   `subjectDN`: the subject distinguished name \(a string\)
-   `subjectAltNames`: subject alternative names. This property is optional. As of version 2.16.1, the value is ignored. SAN on system certificate had never any effect.



## Example

```
curl -k -u <user>:<password> -X POST -H "Content-Type: application/json" --data '{"type":"csr", "subjectDN":"CN=me"}' 
https://<host>:<port>/api/v1/configuration/connector/onPremises/systemCertificate  -o csr.pem
```





<a name="loio236c0842c2cf48238b919d8f95a5afac__section_unl_5zz_c4b"/>

## Upload a Signed Certificate Chain as System Certificate \(Master Only\)


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/onPremises/systemCertificate` 

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

Request

</td>
<td valign="top">

multipart/form-data with the following parameter: `signedCertificate`.

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

Administrator, Associate Administrator

</td>
</tr>
</table>



**Request Properties:**

-   `signedCertificate`: the signed certificate and CA certificate chain \(PEM-encoded\)

**Errors:**

-   `INVALID_REQUEST` \(400\): the certificate chain provided does not match the most recent certificate request, or it is not a certificate chain in the correct format \(PEM-encoded\).



## Example

```
curl -i -k -u <user>:<password> -X PATCH -F signedCertificate=@<signedchain.pem> https://<host>:<port>/api/v1/configuration/connector/onPremises/systemCertificate

```

For test purposes, you can sign the certificate signing request with keytool:

```
keytool -genkeypair -keyalg RSA -keysize 1024 -alias mykey -dname "cn=very trusted, c=test" -validity 365 -keystore ca.ks -keypass testit -storepass testit
keytool -gencert -rfc -infile csr.pem -outfile signedcsr.pem -alias mykey -keystore ca.ks -keypass testit -storepass testit
keytool -exportcert -rfc -file ca.pem -alias mykey -keystore ca.ks -keypass testit -storepass testit
cat signedcsr.pem ca.pem > signedchain.pem
```



<a name="loio236c0842c2cf48238b919d8f95a5afac__section_oqh_3st_mlb"/>

## Upload a PKCS\#12 Certificate as System Certificate \(Master Only\)


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/onPremises/systemCertificate` 

</td>
</tr>
<tr>
<td valign="top">

Method

</td>
<td valign="top">

*PUT* 

</td>
</tr>
<tr>
<td valign="top">

Request

</td>
<td valign="top">

Multipart/form-data with the following form parameters: `pkcs12`, `password`, `keyPassword` 

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

INVALID\_REQUEST

</td>
</tr>
<tr>
<td valign="top">

Roles

</td>
<td valign="top">

Administrator, Associate Administrator

</td>
</tr>
</table>

**Request Parameters:**

-   `pkcs12`: contents of PKCS\#12 file
-   `password`: password for decrypting PKCS\#12 file
-   `keyPassword`: optional password for the private key

**Errors:**

-   `INVALID_REQUEST` \(400\): contents of PKCS\#12 or password are invalid

> ### Note:  
> `keyPassword` is optional. If it is missing, `password` is used to decrypt the pkcs\#12 file and the private key.



## Example

```
curl -i -k -u <user>:<password> https://<host>:<port>/api/v1/configuration/connector/onPremises/systemCertificate -X PUT -F password=<p21Password> -F pkcs12=@<p12file>

```

Create an own self-signed pkcs\#12 certificate for tests with:

```
keytool -genkeypair -alias key -keyalg RSA -keysize 2048 -validity 365 -keypass test20 -keystore test.p12 -storepass test20 -storetype PKCS12 -dname 'CN=test'

```



## Delete a System Certificate \(Master Only\)


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/onPremises/systemCertificate` 

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

Administrator, Associate Administrator

</td>
</tr>
</table>

**Errors:**

-   `NOT_FOUND` \(404\): there is no system certificate.



## Example

```
curl -k -H "Accept: application/json" -u <user>:<password> --request DELETE https://localhost:8443/api/v1/configuration/connector/onPremises/systemCertificate

```

