<!-- loio283cd2d1c72147a18c69daf681650f07 -->

# OAuth JWT Bearer Authentication

Learn about the OAuth JWT bearer authentication type for HTTP destinations: use cases, supported properties and examples.



<a name="loio283cd2d1c72147a18c69daf681650f07__content"/>

## Content

[Overview](oauth-jwt-bearer-authentication-283cd2d.md#loio283cd2d1c72147a18c69daf681650f07__overview)

[Properties](oauth-jwt-bearer-authentication-283cd2d.md#loio283cd2d1c72147a18c69daf681650f07__properties)

[Example: AuthTokens Object Response](oauth-jwt-bearer-authentication-283cd2d.md#loio283cd2d1c72147a18c69daf681650f07__example)



<a name="loio283cd2d1c72147a18c69daf681650f07__overview"/>

## Overview

To allow an application to call another application, passing the user context, and fetch resources, the caller application must pass an access token. In this authorization flow, the initial user token is passed to the OAuth server as input data. This process is performed automatically by the Destination service, which helps simplifying the application development: You only have to construct the right request to the target URL, by using the outcome \(another access token\) of the service-side automation.

Back to [Content](oauth-jwt-bearer-authentication-283cd2d.md#loio283cd2d1c72147a18c69daf681650f07__content)



<a name="loio283cd2d1c72147a18c69daf681650f07__properties"/>

## Properties

To configure a destination of this authentication type, you must specify all the required properties. You can do this via SAP BTP cockpit \(see [Create HTTP Destinations](create-http-destinations-783fa1c.md)\), or using the [Destination Service REST API](destination-service-rest-api-23ccafb.md). The following table shows the properties along with their semantics.


<table>
<tr>
<th valign="top">

Field/Parameter \(Cockpit\)

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

`Authentication`

</td>
<td valign="top">

Authentication

</td>
<td valign="top">

`OAuth2JWTBearer` in this case.

</td>
</tr>
<tr>
<td valign="top">

`Client ID`

</td>
<td valign="top">

clientId

</td>
<td valign="top">

OAuth 2.0 client ID to be used for the user access token exchange.

</td>
</tr>
<tr>
<td valign="top">

`Client Secret`

</td>
<td valign="top">

clientSecret

</td>
<td valign="top">

OAuth 2.0 client secret to be used for the user access token exchange.

</td>
</tr>
<tr>
<td valign="top">

`Name`

</td>
<td valign="top">

Name

</td>
<td valign="top">

Name of the destination. Must be unique for the destination level.

</td>
</tr>
<tr>
<td valign="top">

`Proxy Type`

</td>
<td valign="top">

ProxyType

</td>
<td valign="top">

You can only use proxy type `Internet` or `OnPremise`. If `OnPremise` is used, the OAuth server must be accessed through the Cloud Connector.

</td>
</tr>
<tr>
<td valign="top">

`Token Service URL`

</td>
<td valign="top">

tokenServiceURL

</td>
<td valign="top">

The URL of the token service, against which the token exchange is performed. Depending on the `Token Service URL Type`, this property is interpreted in different ways during the automatic token retrieval:

-   For `Dedicated`, the token service URL is taken as is.
-   For `Common`, the token service URL is searched for the tenant placeholder `{tenant}`.

    `{tenant}` is resolved as the subdomain of the subaccount on behalf of which the caller is performing the call. If the placeholder is not found, `{tenant}` is inserted as a subdomain of the token service URL.

    See [Automated Access Token Retrieval](exchanging-user-jwts-via-oauth2usertokenexchange-destinations-39d4265.md#loio39d42654093e4f8db20398a06f7eab2b__retrrieval) for information about how the tenant is determined.

    The subaccount subdomain is mandated during creation of the subaccount, see [Create a Subaccount](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/05280a123d3044ae97457a25b3013918.html "Create subaccounts in your global account using the SAP BTP cockpit.") :arrow_upper_right:.


**Examples** of interpreting the token service URL for the token service URL type `Common`, if the call to the Destination service is on behalf of a subaccount subdomain with value `mytenant`:

-   ***https://authentication.us10.hana.ondemand.com/oauth/token*** → ***https://mytenant.authentication.us10.hana.ondemand.com/oauth/token***
-   ***https://\{tenant\}.authentication.us10.hana.ondemand.com/oauth/token*** → ***https://mytenant.authentication.us10.hana.ondemand.com/oauth/token***
-   ***https://authentication.myauthserver.com/tenant/\{tenant\}/oauth/token*** → ***https://authentication.myauthserver.com/tenant/mytenant/oauth/token***
-   ***https://oauth.\{tenant\}.myauthserver.com/token*** → ***https://oauth.mytenant.myauthserver.com/token*** 



</td>
</tr>
<tr>
<td valign="top">

`Token Service URL Type`

</td>
<td valign="top">

tokenServiceURLType

</td>
<td valign="top">

-   Choose `Dedicated` if the token service URL serves only a single tenant.
-   Choose `Common` if the token service URL serves multiple tenants.



</td>
</tr>
<tr>
<td valign="top">

`Type`

</td>
<td valign="top">

Type

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

URL

</td>
<td valign="top">

URL of the target endpoint.

</td>
</tr>
<tr>
<td valign="top" colspan="3">

**Optional**

</td>
</tr>
<tr>
<td valign="top">

`Description`

</td>
<td valign="top">

Description

</td>
<td valign="top">

A human-readable description of the destination.

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

`scope`

</td>
<td valign="top">

The value of the OAuth 2.0 `scope` parameter, expressed as a list of space-delimited, case-sensitive strings.

</td>
</tr>
<tr>
<td valign="top">

 

</td>
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

 

</td>
<td valign="top">

`tokenServiceURL.ConnectionTimeoutInSeconds`

</td>
<td valign="top">

Defines the connection timeout for the token service retrieval. The minimum value allowed is 0, the maximum is 60 seconds. If the value exceeds the allowed number, the default value \(10 seconds\) is used.

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

`tokenServiceURL.SocketReadTimeoutInSeconds`

</td>
<td valign="top">

Defines the read timeout for the token service retrieval. The minimum value allowed is 0, the maximum is 600 seconds. If the value exceeds the allowed number, the default value \(10 seconds\) is used.

</td>
</tr>
<tr>
<td valign="top">

 

</td>
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

 

</td>
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

 

</td>
<td valign="top">

`x_user_token.jwks`

</td>
<td valign="top">

Base64-encoded *JSON web key set*, containing the signing keys which are used to validate the JWT provided in the *X-User-Token* header.

For more information, see[JWK Set Format](https://tools.ietf.org/html/rfc7517#section-5).

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

`x_user_token.jwks_uri`

</td>
<td valign="top">

URI of the *JSON web key set*, containing the signing keys which are used to validate the JWT provided in the *X-User-Token* header.

> ### Restriction:  
> If the value is a private endpoint \(for example, *localhost*\), the Destination service will not be able to perform the verification of the X-User-Token header when using the "Find Destination" API.

For more information, see [OpenID Connect Discovery](https://openid.net/specs/openid-connect-discovery-1_0.html#ProviderMetadata).

</td>
</tr>
<tr>
<td valign="top">

 

</td>
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

 

</td>
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

 

</td>
<td valign="top">

`tokenService.KeyStoreLocation`

</td>
<td valign="top">

Contains the name of the certificate configuration to be used. This property is required when using client certificates for authentication. See [OAuth with X.509 Client Certificates](oauth-with-x-509-client-certificates-2c162aa.md).

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

`tokenService.KeyStorePassword`

</td>
<td valign="top">

Contains the password for the certificate configuration \(if one is needed\) when using client certificates for authentication. See [OAuth with X.509 Client Certificates](oauth-with-x-509-client-certificates-2c162aa.md).

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

`tokenService.addClientCredentialsInBody` 

</td>
<td valign="top">

Specifies whether the client credentials should be placed in the request body of the token request, rather than the `Authorization` header. Default is `true`.

</td>
</tr>
</table>

Back to [Content](oauth-jwt-bearer-authentication-283cd2d.md#loio283cd2d1c72147a18c69daf681650f07__content)



<a name="loio283cd2d1c72147a18c69daf681650f07__example"/>

## Example: AuthTokens Object Response

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

Back to [Content](oauth-jwt-bearer-authentication-283cd2d.md#loio283cd2d1c72147a18c69daf681650f07__content)

