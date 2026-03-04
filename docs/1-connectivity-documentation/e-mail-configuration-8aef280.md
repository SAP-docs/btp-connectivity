<!-- loio8aef280ba2624c6c8512ee89c49ad0a4 -->

# E-Mail Configuration

Read and edit the Cloud Connector's e-mail settings via API.



## Get E-Mail Configuration


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/email` 

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

```
{enabled, trustOption, sendTo, sendCc, sendFrom, smtpHost, smtpPort, smtpUsername, additionalProperties}
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

Administrator, Associate Administrator, Subaccount Administrator, Display, Support, Monitoring

</td>
</tr>
</table>

**Response**:

-   `enabled`: Boolean - whether e-mails should be sent in case of an alert or not
-   `trustOption`: String - one of the following levels of trust options for the e-mail server \(see [Configure Trust](configure-trust-13bfb28.md)\): 'tlsDisabled', 'emailTrustStore', 'jdkAndEmailTrustStore', 'trustAll'
-   `sendTo`: String - e-mail addresses of the recipients in [RFC 822](https://www.ietf.org/rfc/rfc822.txt) format
-   `sendCc` \(optional\): String - e-mail addresses of the recipients that should get a copy of the e-mail in [RFC 822](https://www.ietf.org/rfc/rfc822.txt) format
-   `sendFrom`: String - e-mail address of the sender in [RFC 822](https://www.ietf.org/rfc/rfc822.txt) format
-   `smtpHost`: String - host of the mail server
-   `smtpPort` \(optional\): String or Integer - port of the mail server
-   `smtpUsername` \(optional\): String - username for authentication with the mail server
-   `additionalProperties` \(optional\): Dictionary - additional properties that are supported by the [java mail library](https://javaee.github.io/javamail/docs/api/com/sun/mail/smtp/package-summary.html)

> ### Sample Code:  
> ```
> curl -i -k -H "Accept: application/json" -u <user>:<password> -X GET https://<host>:<port>/api/v1/configuration/connector/email
> ```

> ### Sample Code:  
> **Sample output: E-mail configuration \(GET - without optional values\)**
> 
> ```
> {
>   "enabled": true,
>   "trustOption": "emailTrustStore",
>   "sendTo": "recipient@corp.de",
>   "sendFrom": "sender@othercorp.com",
>   "smtpHost": "walldorf.corp.host"
> }
> ```

> ### Sample Code:  
> Sample output: E-mail configuration \(GET - with optional values\)
> 
> ```
> {
>   "enabled": true,
>   "trustOption": "emailTrustStore",
>   "sendTo": "recipient@corp.de",
>   "sendCc": "John Doe <j.doe@company.com>, Jane Doe <j2.doe@company.com>",
>   "sendFrom": "sender@othercorp.com",
>   "smtpHost": "walldorf.corp.host",
>   "smtpPort": 587,
>   "smtpUsername": "username123",
>   "additionalProperties": {
>     "mail.smtp.someKey": "someValue"
>   }
> }
> ```



## Set E-Mail Configuration


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/email` 

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

```
{enabled, trustOption, sendTo, sendCc, sendFrom, smtpHost, smtpPort, smtpUsername, smtpPassword, additionalProperties}
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

**Request**:

-   `enabled`: Boolean - whether e-mails should be sent in case of an alert or not
-   `trustOption`: String - one of the following levels of trust options for the e-mail server \(see [Configure Trust](configure-trust-13bfb28.md)\): 'tlsDisabled', 'emailTrustStore', 'jdkAndEmailTrustStore', 'trustAll'
-   `sendTo`: String - e-mail addresses of the recipients in [RFC 822](https://www.ietf.org/rfc/rfc822.txt) format
-   `sendCc` \(optional\): String - e-mail addresses of the recipients that should get a copy of the e-mail in [RFC 822](https://www.ietf.org/rfc/rfc822.txt) format
-   `sendFrom`: String - e-mail address of the sender in [RFC 822](https://www.ietf.org/rfc/rfc822.txt) format
-   `smtpHost`: String - host of the mail server
-   `smtpPort` \(optional\): String or Integer - port of the mail server
-   `smtpUsername` \(optional\): String - username for authentication with the mail server
-   `smtpPassword` \(optional\): String - password for authentication with the mail server
-   `additionalProperties` \(optional\): Dictionary - additional properties that are supported by the [java mail library](https://javaee.github.io/javamail/docs/api/com/sun/mail/smtp/package-summary.html)

**Errors**:

-   `INVALID_REQUEST`:
    -   empty input
    -   mandatory values are not set
    -   invalid value for `trustOption`
    -   format of the e-mail addresses is incorrect
    -   format of host is wrong
    -   port is not within the range 1-65535\(inclusive\)


> ### Caution:  
> Validation of the configuration only happens if `enabled` is set to `true`.

> ### Sample Code:  
> ```
> curl -i -k -H "Content-Type: application/json" -u <user>:<password> -X PUT https://<host>:<port>/api/v1/configuration/connector/email
> ```

> ### Sample Code:  
> **Sample input: E-mail configuration \(PUT- with optional values\)** 
> 
> ```
> {
>   "enabled": true,
>   "trustOption": "emailTrustStore",
>   "sendTo": "recipient@corp.de",
>   "sendFrom": "sender@othercorp.com",
>   "smtpHost": "walldorf.corp.host",
>   "smtpPort": 587,
>   "sendCc": "John Doe <j.doe@company.com>, Jane Doe <j2.doe@company.com>",
>   "smtpUsername": "username123",
>   "smtpPassword": "password123",
>   "additionalProperties": {
>     "mail.smtp.someKey": "someValue"
>   }
> }
> ```



## Modify E-Mail Configuration


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/email` 

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

```
{<values to be changed>}
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

**Request**:

One or several values of

-   `enabled`: Boolean - whether e-mails should be sent in case of an alert or not
-   `trustOption`: String - one of the following levels of trust options for the e-mail server \(see [Configure Trust](configure-trust-13bfb28.md)\): 'tlsDisabled', 'emailTrustStore', 'jdkAndEmailTrustStore', 'trustAll'
-   `sendTo`: String - e-mail addresses of the recipients in [RFC 822](https://www.ietf.org/rfc/rfc822.txt) format
-   `sendCc` \(optional\): String - e-mail addresses of the recipients that should get a copy of the e-mail in [RFC 822](https://www.ietf.org/rfc/rfc822.txt) format
-   `sendFrom`: String - e-mail address of the sender in [RFC 822](https://www.ietf.org/rfc/rfc822.txt) format
-   `smtpHost`: String - host of the mail server
-   `smtpPort` \(optional\): String or Integer - port of the mail server
-   `smtpUsername` \(optional\): String - username for authentication with the mail server
-   `smtpPassword` \(optional\): String - password for authentication with the mail server
-   `additionalProperties` \(optional\): Dictionary - additional properties that are supported by the [java mail library](https://javaee.github.io/javamail/docs/api/com/sun/mail/smtp/package-summary.html)

**Errors**:

-   `INVALID_REQUEST`:
    -   empty input
    -   mandatory values are not set
    -   invalid value for `trustOption`
    -   format of the e-mail addresses is incorrect
    -   format of host is wrong
    -   port is not within the range 1-65535\(inclusive\)


> ### Caution:  
> Validation of the configuration only happens if `enabled` is set to `true`.

> ### Sample Code:  
> ```
> curl -i -k -H "Content-Type: application/json" -u <user>:<password> -X PATCH https://<host>:<port>/api/v1/configuration/connector/email
> ```



## Get Truststore Information


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/email/truststore` 

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

```
{trustedEmailCertificates}
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

Administrator, Associate Administrator, Subaccount Administrator, Display, Support, Monitoring

</td>
</tr>
</table>

**Response**:

-   `trustedEmailCertificates`: A list of trusted e-mail server certificates with the following properties:

*Certificate Properties*:

-   `alias`: String - the alias of a trusted certificate \(a string\)
-   `subjectDN`: String - the subject DN \(a string\)
-   `issuer`: String - the issuer \(a string\)
-   `notAfterTimeStamp`: Long - the end date of the certificate's validity period, represented as the number of milliseconds since January 1, 1970, 00:00:00 GMT

> ### Sample Code:  
> ```
> curl -i -k -H "Accept: application/json" -u <user>:<password> -X GET https://<host>:<port>/api/v1/configuration/connector/email/truststore
> ```

> ### Sample Code:  
> **Sample output: Trusted e-mail certificates \(GET Response\)** 
> 
> ```
> {
>   "trustedEmailCertificates": [
>     {
>       "alias": "trustedemailserver.1.1",
>       "subjectDN": "CN=*.example.com, OU=IT, O=Example Corp, C=US",
>       "issuer": "CN=Example Root CA, O=Example Corp, C=US",
>       "notAfterTimeStamp": 2145916801000
>     },
>     {
>       "alias": "trustedemailserver.1.2",
>       "subjectDN": "CN=mail.internal.example.org, O=Example Org, C=US",
>       "issuer": "CN=Example Intermediate CA, O=Example Org, C=US",
>       "notAfterTimeStamp": 1966607187000
>     },
>     {
>       "alias": "trustedemailserver.1.3",
>       "subjectDN": "CN=selfsigned.example.local, O=Internal Systems, C=US",
>       "issuer": "CN=selfsigned.example.local, O=Internal Systems, C=US",
>       "notAfterTimeStamp": 2044533167000
>     }
>   ]
> }
> ```



## Get Single Truststore Certificate by Aalias


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/email/truststore/certificates/<alias>` 

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

certificate in the specified format

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

**Request Header**:

-   `Accept`: application/x-pem-file - requests the certificate in PEM format \(Base64-encoded\)
-   `Accept`: application/pkix-cert - requests the certificate in DER format \(binary format\)

**Errors**:

-   `NOT_FOUND`\): if the certificate with the specified alias could not be found

> ### Sample Code:  
> ```
> curl -i -k -H "Accept: application/x-pem-file" -u <user>:<password> -X GET --output <pemFile> https://<host>:<port>/api/v1/configuration/connector/email/truststore/certificates/<alias>
> curl -i -k -H "Accept: application/pkix-cert"  -u <user>:<password> -X GET --output <derFile> https://<host>:<port>/api/v1/configuration/connector/email/truststore/certificates/<alias>
> ```



## Get All Truststore Certificates


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/email/truststore/certificates` 

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

certificates in the specified format

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

Administrator, Associate Administrator, Subaccount Administrator, Display, Support, Monitoring

</td>
</tr>
</table>

**Request Header**:

-   `Accept`: application/x-pem-file - requests the certificate in PEM format \(Base64-encoded\)
-   `Accept`: application/pkix-cert - requests the certificate in DER format \(binary format\)

> ### Sample Code:  
> ```
> curl -i -k -H "Accept: application/x-pem-file" -u <user>:<password> -X GET --output <pemFile> https://<host>:<port>/api/v1/configuration/connector/email/truststore/certificates
> curl -i -k -H "Accept: application/pkix-cert"  -u <user>:<password> -X GET --output <derFile> https://<host>:<port>/api/v1/configuration/connector/email/truststore/certificates
> ```



## Create a Truststore Certificate


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/email/truststore/certificates` 

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

multipart/form-data with the following form parameter: `certificates` 

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

**Request Properties**:

-   `certificates`: one or multiple certificates in DER or PEM format

**Errors**:

-   `INVALID_REQUEST`: if no or a duplicate certificate was provided

> ### Sample Code:  
> ```
> curl -i -k -u <user>:<password> -X POST -F "certificates=@<file>" https://<host>:<port>/api/v1/configuration/connector/email/truststore/certificates
> ```



## Delete Single Truststore Certificate by Alias


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/email/truststore/certificates/<alias>` 

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

**Errors**:

-   `NOT_FOUND`: if the certificate with the specified alias could not be found

> ### Sample Code:  
> ```
> curl -i -k -u <user>:<password> -X DELETE https://<host>:<port>/api/v1/configuration/connector/email/truststore/certificates/<alias>
> ```



## Delete All Truststore Certificates


<table>
<tr>
<td valign="top">

URI

</td>
<td valign="top">

`/api/v1/configuration/connector/email/truststore/certificates` 

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

> ### Sample Code:  
> ```
> curl -i -k -u <user>:<password> -X DELETE https://<host>:<port>/api/v1/configuration/connector/email/truststore/certificates
> ```

