<!-- loio9f634f6c9cd148b7a32c4ac2b56a24c0 -->

# OAuth Authorization Code Authentication

Create and configure an *OAuth Authorization Code* destination for an application.



<a name="loio9f634f6c9cd148b7a32c4ac2b56a24c0__section_zk2_cjh_ytb"/>

## Overview

The *OAuth Authorization Code* flow is a standard mechanism for business user login. It is a two-step procedure. In a first step, business users authenticate themselves towards an authorization server, which grants users an authorization code. The second step exchanges the authorization code for an access token through a token service. Applications can use this flow to access OAuth-protected resources.

The client credentials and an authorization code are used to request an access token from an OAuth server, referred to below as *token service*. This is performed automatically by the Destination service when using the "Find a destination" REST endpoint.



<a name="loio9f634f6c9cd148b7a32c4ac2b56a24c0__section_al2_cjh_ytb"/>

## Properties

The table below lists the destination properties for the *OAuth2AuthorizationCode* authentication type.


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

Authentication type. Use `OAuth2AuthorizationCode` as value.

</td>
</tr>
<tr>
<td valign="top">

`clientId`

</td>
<td valign="top">

Client ID of the application.

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

`clientAssertion.destinationName`

</td>
<td valign="top">

Name of the destination that provides client assertions when using client assertion authentication mechanism. Must be on the same subaccount or service instance as this destination. This is used in case of automated client assertion fetching by the service.

For more information, see [Client Assertion with Automated Assertion Fetching by the Service](client-assertion-with-automated-assertion-fetching-by-the-service-1c34472.md).

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



<a name="loio9f634f6c9cd148b7a32c4ac2b56a24c0__section_rcx_gmh_ytb"/>

## Example: OAuth2 Authorization Code Destination

> ### Sample Code:  
> ```
> {
>     "Name": "SapOAuth2AuthorizationCodeDestination",
>     "Type": "HTTP",
>     "URL": "https://myapp.cfapps.sap.hana.ondemand.com/mypath",
>     "ProxyType": "Internet",
>     "Authentication": "OAuth2AuthorizationCode",
>     "clientId": "my-client-id",
>     "clientSecret": "my-client-pass",
>     "tokenServiceURL": "https://authentication.sap.hana.ondemand.com/oauth/token"
> }
> ```



<a name="loio9f634f6c9cd148b7a32c4ac2b56a24c0__section_hh3_3mh_ytb"/>

## Calling "Find Destination"

When calling the destination, an *X-code* is a required header parameter. *X-redirect-uri* and *X-code-verifier* are optional header parameters. They depend on the call for the authorization code fetch. If a redirect URI was specified in that call, the same redirect URI must be used as value for the *X-redirect-uri* header. If a code challenge was presented in the authorization code fetch request, a code verifier must be given as value for the *X-code-verifier* header.

**Curl call example**

> ### Sample Code:  
> ```
> curl --location --request GET 'https://<destination>.<environment>.hanavlab.ondemand.com/destination-configuration/v1/destinations/<destination-name>' \
> --header 'X-code: <authorization_code>' \ # mandatory parameter
> --header 'X-redirect-uri: <redirect_uri>' \ # optional parameter
> --header 'X-code-verifier: <code_verifier>' \ # optional parameter
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

