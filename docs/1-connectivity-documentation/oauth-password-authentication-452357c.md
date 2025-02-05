<!-- loio452357cdd82a4c0ba6095b36c0057526 -->

# OAuth Password Authentication

Learn about the OAuth password authentication type for HTTP destinations: use cases, supported properties and examples.



<a name="loio452357cdd82a4c0ba6095b36c0057526__content"/>

## Content

[Overview](oauth-password-authentication-452357c.md#loio452357cdd82a4c0ba6095b36c0057526__overview)

[Properties](oauth-password-authentication-452357c.md#loio452357cdd82a4c0ba6095b36c0057526__properties)

[Example: OAuth Token Service](oauth-password-authentication-452357c.md#loio452357cdd82a4c0ba6095b36c0057526__example)



<a name="loio452357cdd82a4c0ba6095b36c0057526__overview"/>

## Overview

SAP BTP provides support for applications to use the OAuth password grant flow for consuming OAuth-protected resources.

The client credentials as well as the user name and password are used to request an access token from an OAuth server, referred to as *token service* below. Access token retrieval is performed automatically by the Destination service when using the "find destination" REST endpoint.

Back to [Content](oauth-password-authentication-452357c.md#loio452357cdd82a4c0ba6095b36c0057526__content)



<a name="loio452357cdd82a4c0ba6095b36c0057526__properties"/>

## Properties

The table below lists the destination properties needed for the OAuth2Password authentication type.

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
<td valign="top" colspan="2">

**Required**

</td>
</tr>
<tr>
<td valign="top">

`Name`

</td>
<td valign="top">

Destination name. It must be the same as the destination name you use for the configuration tools, that is, the console client and *Destinations* editor \(cockpit\).

</td>
</tr>
<tr>
<td valign="top">

`Type`

</td>
<td valign="top">

Destination type. Choose `HTTP` \(for HTTP or HTTPS communication\).

</td>
</tr>
<tr>
<td valign="top">

`URL`

</td>
<td valign="top">

URL of the protected resource being accessed.

</td>
</tr>
<tr>
<td valign="top">

`ProxyType`

</td>
<td valign="top">

You can only use proxy type `Internet` or `OnPremise`. If `OnPremise` is used, the OAuth server must be accessed through the Cloud Connector.

</td>
</tr>
<tr>
<td valign="top">

`Authentication`

</td>
<td valign="top">

Authentication type. Use `OAuth2Password` as value.

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

Client secret for the client ID.

</td>
</tr>
<tr>
<td valign="top">

`User`

</td>
<td valign="top">

User name of the technical user trying to get a token.

</td>
</tr>
<tr>
<td valign="top">

`Password`

</td>
<td valign="top">

Password of the technical user trying to get a token.

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

`scope`

</td>
<td valign="top">

Value of the OAuth 2.0 `scope` parameter, expressed as a list of space-delimited, case-sensitive strings.

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

Back to [Content](oauth-password-authentication-452357c.md#loio452357cdd82a4c0ba6095b36c0057526__content)



<a name="loio452357cdd82a4c0ba6095b36c0057526__example"/>

## Example: OAuth Token Service

> ### Sample Code:  
> ```
> {
>     "Name": "SapOAuthPassGrant",
>     "Type": "HTTP",
>     "URL": "https://myapp.cfapps.sap.hana.ondemand.com/mypath",
>     "ProxyType": "Internet",
>     "Authentication": "OAuth2Password",
>     "clientId": "my-client-id",
>     "clientSecret": "my-client-pass",
>     "User": "my-username",
>     "Password": "my-password",
>     "tokenServiceURL": "https://authentication.sap.hana.ondemand.com/oauth/token"
> }
> ```

The response for "find destination" contains an `authTokens` object in the format given below. For more information on the fields in `authTokens`, see ["Find a Destination" Response Structure](find-a-destination-response-structure-83a3f3b.md).

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

Back to [Content](oauth-password-authentication-452357c.md#loio452357cdd82a4c0ba6095b36c0057526__content)

