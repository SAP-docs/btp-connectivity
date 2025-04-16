<!-- loiobff0136772d944348d982b2b427befb9 -->

# OAuth Refresh Token Authentication

Create and configure an *OAuth refresh token* destination for an application.



<a name="loiobff0136772d944348d982b2b427befb9__section_zk2_cjh_ytb"/>

## Overview

SAP BTP provides support for applications to use the *OAuth2 refresh token* flow for consuming OAuth-protected resources.

Refresh tokens are a common way to maintain certain levels of access, without requiring the use of credentials for getting a new access token. They have a longer validity compared to access tokens and can be used to fetch brand new access tokens without performing again the original flow.

The client credentials and a refresh token are used to request an access token from an OAuth server, referred to below as *token service*. This is automatically performed by the Destination service when using the "Find a destination" REST endpoint.



<a name="loiobff0136772d944348d982b2b427befb9__section_al2_cjh_ytb"/>

## Properties

The table below lists the destination properties for the *OAuth refresh token* authentication type.


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
<td valign="top" colspan="2">

**Required**

</td>
</tr>
<tr>
<td valign="top">

`Name`

</td>
<td valign="top">

Name of the destination. It must be the same as the destination name you use for the configuration tools, that is, the console client and *Destinations* editor \(cockpit\).

</td>
</tr>
<tr>
<td valign="top">

`Type`

</td>
<td valign="top">

Destination type. Choose `HTTP` for all HTTP\(S\) destinations.

</td>
</tr>
<tr>
<td valign="top">

`URL`

</td>
<td valign="top">

The URL of the protected target resource.

</td>
</tr>
<tr>
<td valign="top">

`ProxyType`

</td>
<td valign="top">

Choose `Internet` or `OnPremise`. If `OnPremise` is used, the OAuth server must be accessed through the Cloud Connector.

</td>
</tr>
<tr>
<td valign="top">

`Authentication`

</td>
<td valign="top">

Authentication type. Use `OAuth2RefreshToken` as value.

</td>
</tr>
<tr>
<td valign="top">

`clientId`

</td>
<td valign="top">

Client ID used to retrieve the access token.

</td>
</tr>
<tr>
<td valign="top">

`clientSecret`

</td>
<td valign="top">

Client secret for the Client ID.

</td>
</tr>
<tr>
<td valign="top">

`tokenServiceURL`

</td>
<td valign="top">

Token retrieval URL of the OAuth server.

</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Additional**

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

`scope`

</td>
<td valign="top">

Value of the OAuth 2.0 `scope` parameter, expressed as a list of space-delimited, case-sensitive strings.

</td>
</tr>
<tr>
<td valign="top">

`tokenServiceURLType`

</td>
<td valign="top">

Either `Dedicated` \(if the `tokenServiceURL` serves only a single tenant\), or `Common` \(if the `tokenServiceURL` serves multiple tenants\).

</td>
</tr>
<tr>
<td valign="top">

`tokenServiceURL.headers.<header-key>` 

</td>
<td valign="top">

Static key prefix used as a namespace grouping of the `tokenServiceUrl`'s HTTP headers. Its values will be sent to the token service during token retrieval. For each HTTP header's key you must add a *'tokenServiceURL.headers'* prefix separated by dot delimiter. For example:

> ### Sample Code:  
> ```
> {
>     ...
>     "tokenServiceURL.headers.<header-key-1>" : "<header-value-1>",
>     ...
>     "tokenServiceURL.headers.<header-key-N>": "<header-value-N>",
> }
> ```



</td>
</tr>
<tr>
<td valign="top">

`tokenServiceURL.queries.<query-key>` 

</td>
<td valign="top">

Static key prefix used as a namespace grouping of `tokenServiceUrl`'s query parameters. Its values will be sent to the token service during token retrieval. For each query paramester's key you must add a *'tokenServiceURL.queries'* prefix separated by dot delimiter. For example:

> ### Sample Code:  
> ```
> {
>     ...
>     "tokenServiceURL.queries.<query-key-1>" : "<query-value-1>",
>     ...
>     "tokenServiceURL.queries.<query-key-N>": "<query-value-N>",
> }
> ```



</td>
</tr>
<tr>
<td valign="top">

`tokenService.body.<param-key>`

</td>
<td valign="top">

A static key prefix used as a namespace grouping of parameters which are sent as part of the token request to the token service during token retrieval. For each request, a `tokenService.body` prefix must be added to the parameter key, separated by dot-delimiter. For example:

> ### Sample Code:  
> ```
> {
> 	...
> 	"tokenService.body.<param-key-1>" : "<param-value-1>",
> 	...
> 	"tokenService.body.<param-key-N>": "<param-value-N>",
> }
> ```



</td>
</tr>
<tr>
<td valign="top">

`tokenService.KeyStoreLocation` 

</td>
<td valign="top">

Contains the name of the certificate configuration to be used. This property is required when using client certificates for authentication. See [OAuth with X.509 Client Certificates](oauth-with-x-509-client-certificates-2c162aa.md).

</td>
</tr>
<tr>
<td valign="top">

`tokenService.KeyStorePassword`

</td>
<td valign="top">

Contains the password for the certificate configuration \(if one is needed\) when using client certificates for authentication. See [OAuth with X.509 Client Certificates](oauth-with-x-509-client-certificates-2c162aa.md).

</td>
</tr>
<tr>
<td valign="top">

`tokenService.addClientCredentialsInBody` 

</td>
<td valign="top">

Specifies whether the client credentials should be placed in the request body of the token request, rather than the `Authorization` header. Default is `true`.

</td>
</tr>
<tr>
<td valign="top">

`URL.headers.<header-key>`

</td>
<td valign="top">

Static key prefix used as a namespace grouping of the URL's HTTP headers whose values will be sent to the target endpoint. For each HTTP header's key, you must add a `URL.headers` prefix separated by dot-delimiter. For example:

> ### Sample Code:  
> ```
> {
>     ...
>     "URL.headers.<header-key-1>" : "<header-value-1>",
>     ...
>     "URL.headers.<header-key-N>": "<header-value-N>",
> }
> ```

> ### Note:  
> This is a naming convention. As the call to the target endpoint is performed on the client side, the service only provides the configured properties. The expectation for the client-side processing logic is to parse and use them. If you are using higher-level libraries and tools, please check if they support this convention.



</td>
</tr>
<tr>
<td valign="top">

`tokenServiceURL.ConnectionTimeoutInSeconds`

</td>
<td valign="top">

Defines the connection timeout for the token service retrieval. The minimum value allowed is 0, the maximum is 60 seconds. If the value exceeds the allowed number, the default value \(10 seconds\) is used.

</td>
</tr>
<tr>
<td valign="top">

`tokenServiceURL.SocketReadTimeoutInSeconds`

</td>
<td valign="top">

Defines the read timeout for the token service retrieval. The minimum value allowed is 0, the maximum is 600 seconds. If the value exceeds the allowed number, the default value \(10 seconds\) is used.

</td>
</tr>
<tr>
<td valign="top">

`URL.queries.<query-key>` 

</td>
<td valign="top">

Static key prefix used as a namespace grouping of URL's query parameters whose values will be sent to the target endpoint. For each query parameter's key, you must add a `URL.queries` prefix separated by dot-delimiter. For example:

> ### Sample Code:  
> ```
> {
>     ...
>     "URL.queries.<query-key-1>" : "<query-value-1>",
>     ...
>     "URL.queries.<query-key-N>": "<query-value-N>",
> }
> ```

> ### Note:  
> This is a naming convention. As the call to the target endpoint is performed on the client side, the service only provides the configured properties. The expectation for the client-side processing logic is to parse and use them. If you are using higher-level libraries and tools, please check if they support this convention.



</td>
</tr>
</table>

> ### Note:  
> When the OAuth server is called, the caller side trusts the server based on the trust settings of the destination. For more information, see [Server Certificate Authentication](server-certificate-authentication-e75d7f1.md).



<a name="loiobff0136772d944348d982b2b427befb9__section_rcx_gmh_ytb"/>

## Example: OAuth2 RefreshToken Destination

> ### Sample Code:  
> ```
> {
>     "Name": "SapOAuthPassGrant",
>     "Type": "HTTP",
>     "URL": "https://myapp.cfapps.sap.hana.ondemand.com/mypath",
>     "ProxyType": "Internet",
>     "Authentication": "OAuth2RefreshToken",
>     "clientId": "my-client-id",
>     "clientSecret": "my-client-pass",
>     "tokenServiceURL": "https://authentication.sap.hana.ondemand.com/oauth/token"
> }
> ```



<a name="loiobff0136772d944348d982b2b427befb9__section_hh3_3mh_ytb"/>

## Calling "Find Destination"

When calling the destination an *X-refresh-token* is a required header parameter.

**Curl call example**

> ### Sample Code:  
> ```
> curl --location --request GET 'https://<destination>.<environment>.hanavlab.ondemand.com/destination-configuration/v1/destinations/<destination-name>' \
> --header 'X-refresh-token: <refresh_token>' \ # mandatory parameter
> --header 'Authorization: Bearer <destination_token>'
> ```

The response for *Find Destination* will contain an `authTokens` object in the format given below. For more information on the fields in `authTokens`, see ["Find a Destination" Response Structure](find-a-destination-response-structure-83a3f3b.md).

> ### Sample Code:  
> ```
> "authTokens": [
>     {
>         "type": "Bearer",
>         "value": "eyJhbGciOiJSUzI1NiIsInR5cC...",
>         "http_header": {
>             "key":"Authorization",
>             "value":"Bearer eyJhbGciOiJSUzI1NiIsInR5cC..."
>         }
>     }
> ]
> ```

