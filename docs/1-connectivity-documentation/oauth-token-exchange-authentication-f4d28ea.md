<!-- loiof4d28ea5a6ce441fb3dacce0a55d7a35 -->

# OAuth Token Exchange Authentication

Learn about the `OAuth2TokenExchange` authentication type for HTTP destinations: use cases, supported properties and ways to retrieve an access token in an automated way.



<a name="loiof4d28ea5a6ce441fb3dacce0a55d7a35__overview"/>

## Overview

To allow an application to call another application, passing the principal context, and fetch resources, the caller application needs to pass a security token. In this authorization flow, the initial security token is passed to the OAuth server as input data. This process is performed automatically by the Destination service, which helps simplify the application development - you only have to construct the right request to the target URL, by using the outcome \(another access token\) of the service side automation.

With this token exchange flow, any type of token can be used, provided that it is supported by the configured token service.



<a name="loiof4d28ea5a6ce441fb3dacce0a55d7a35__properties"/>

## Properties

To configure a destination of this type, you must specify all the required properties. You can create destinations of this type via the [Destination Service REST API](destination-service-rest-api-23ccafb.md).

> ### Restriction:  
> `OAuth2TokenExchange` destinations don’t support dynamic tenant-specific token service URLs. The token service URL is always taken as is.

The table below lists the destination properties needed for the creation of destination of `OAuth2TokenExchange` authentication type.


<table>
<tr>
<th valign="top">

Property/Key

</th>
<th valign="top">

Input/Description

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

Name of the destination. Must be unique for the destination level.

</td>
</tr>
<tr>
<td valign="top">

`Type`

</td>
<td valign="top">

Choose `HTTP` \(for HTTP or HTTPS communication\).

</td>
</tr>
<tr>
<td valign="top">

`URL`

</td>
<td valign="top">

URL of the target endpoint.

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

Use `OAuth2TokenExchange`.

</td>
</tr>
<tr>
<td valign="top">

`clientId`

</td>
<td valign="top">

OAuth 2.0 client ID to be used for the security access token exchange.

</td>
</tr>
<tr>
<td valign="top">

`tokenServiceURL`

</td>
<td valign="top">

The URL of the token service, against which the token exchange is performed.

> ### Note:  
> Tenant-specific URLs are not supported. The token service URL will be taken as is.



</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Optional**

</td>
</tr>
<tr>
<td valign="top">

`Description`

</td>
<td valign="top">

Human-readable description of the destination.

</td>
</tr>
<tr>
<td valign="top">

`clientSecret`

</td>
<td valign="top">

OAuth 2.0 client secret to be used for the security access token exchange.

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

Value of the OAuth 2.0 scope parameter expressed as a list of space-delimited, case-sensitive strings.

</td>
</tr>
<tr>
<td valign="top">

`tokenServiceURL.headers.<header-key>` 

</td>
<td valign="top">

A static key prefix used as a namespace grouping of the `tokenServiceUrl`'s HTTP headers. Its values will be sent to the token service during token retrieval. For each HTTP header's key you must add a *'tokenServiceURL.headers'* prefix separated by dot delimiter. For example:

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

A static key prefix used as a namespace grouping of `tokenServiceUrl`'s query parameters. Its values will be sent to the token service during token retrieval. For each query paramester's key you must add a *'tokenServiceURL.queries'* prefix separated by dot delimiter. For example:

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

`URL.headers.<header-key>`

</td>
<td valign="top">

A static key prefix used as a namespace grouping of the URL's HTTP headers whose values will be sent to the target endpoint. For each HTTP header's key, you must add a `URL.headers` prefix separated by dot-delimiter. For example:

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

A static key prefix used as a namespace grouping of URL's query parameters whose values will be sent to the target endpoint. For each query parameter's key, you must add a `URL.queries` prefix separated by dot-delimiter. For example:

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
<tr>
<td valign="top">

`tokenService.KeyStoreLocation`

</td>
<td valign="top">

Contains the name of the certificate configuration to be used. This property is required when using client certificates for authentication.

For more information, see [OAuth with X.509 Client Certificates](oauth-with-x-509-client-certificates-2c162aa.md).

</td>
</tr>
<tr>
<td valign="top">

`tokenService.KeyStorePassword`

</td>
<td valign="top">

Contains the password for the certificate configuration \(if one is needed\) when using client certificates for authentication.

For more information, see [OAuth with X.509 Client Certificates](oauth-with-x-509-client-certificates-2c162aa.md).

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

`clientAssertion.destinationName` 

</td>
<td valign="top">

Name of the destination that provides client assertions when using the *client assertion authentication* mechanism. Must be on the same subaccount or service instance as this destination. This key is used in case of automated client assertion fetching by the service.

For more information, see [Client Assertion with Automated Assertion Fetching by the Service](client-assertion-with-automated-assertion-fetching-by-the-service-1c34472.md).

</td>
</tr>
</table>



<a name="loiof4d28ea5a6ce441fb3dacce0a55d7a35__example"/>

## Example: AuthTokens Object Response

The response for "find destination" contains an `authTokens` object in the format given below. For more information on the fields in `authTokens`, see ["Find a Destination" Response Structure](find-a-destination-response-structure-83a3f3b.md).

> ### Sample Code:  
> ```
> "authTokens": [
>     {
>         "type": "Bearer",
>         "value": "eyJhbGciOiJSUzI1NiIsInR5cC...",
>         "issued_token_type": "urn:ietf:params:oauth:token-type:access_token",
>         "http_header": {
>             "key":"Authorization",
>             "value":"Bearer eyJhbGciOiJSUzI1NiIsInR5cC..."
>         }
>     }
> ]
> ```

