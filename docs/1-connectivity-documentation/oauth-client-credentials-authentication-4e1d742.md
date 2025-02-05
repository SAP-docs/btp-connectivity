<!-- loio4e1d742a3d45472d83b411e141729795 -->

# OAuth Client Credentials Authentication

Create and configure an *OAuth2ClientCredentials* destination to consume OAuth-protected resources from an application.

SAP BTP supports applications to use the OAuth client credentials flow for consuming OAuth-protected resources.

The client credentials are used to request an access token from an OAuth authorization server.

> ### Note:  
> The retrieved access token is cached and auto-renovated. When a token is about to expire, a new token is created shortly before the expiration of the old one.



<a name="loio4e1d742a3d45472d83b411e141729795__section_zzr_x3w_cfb"/>

## Configuration Steps

You can create and configure an *OAuth2ClientCredentials* destination using the properties listed below, and deploy it on SAP BTP. To create and configure a destination, follow the steps described in [Managing Destinations](managing-destinations-84e45e0.md).



<a name="loio4e1d742a3d45472d83b411e141729795__section_pzj_y3w_cfb"/>

## Properties

The table below lists the destination properties required for the *OAuth2ClientCredentials* authentication type.


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

Destination name. Must be unique for the destination level.

</td>
</tr>
<tr>
<td valign="top">

`Type`

</td>
<td valign="top">

Destination type. Use `HTTP` as value for all HTTP\(S\) destinations.

</td>
</tr>
<tr>
<td valign="top">

URL

</td>
<td valign="top">

URL of the protected resource on the called application.

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

Authentication type. Use `OAuth2ClientCredentials` as value.

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

URL of the token service, against which token retrieval is performed. Depending on the `tokenServiceURLType`, this property is interpreted in different ways during automatic token retrieval:

-   For `Dedicated`, the `tokenServiceURL` is used as is.
-   For `Common`, the `tokenServiceURL` is searched for the tenant placeholder ***\{tenant\}***. It is resolved as subdomain of the subaccount on whose behalf the caller is performing the call to the Destination service API for fetching the destination.

    If the placeholder is not found, ***\{tenant\}*** is processed as a subdomain of the `tokenServiceURL`.

    See the [Destination service REST API](https://api.sap.com/api/SAP_CP_CF_Connectivity_Destination/resource) to learn how the subaccount's subdomain is specified. The subaccount subdomain is mandated during creation of the subaccount, see [Create a Subaccount](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/05280a123d3044ae97457a25b3013918.html) \(SAP BTP Core documentation\).


Examples of interpreting of the `tokenServiceURL` for `tokenServiceURLType` `Common`, if the call to the Destination service is done on behalf of a subaccount with subdomain value ***mytenant***:

-   https://authentication.us10.hana.ondemand.com/oauth/token → https://**mytenant**.authentication.us10.hana.ondemand.com/oauth/token
-   https://**\{tenant\}**.authentication.us10.hana.ondemand.com/oauth/token → https://**mytenant**.authentication.us10.hana.ondemand.com/oauth/token
-   https://authentication.myauthserver.com/tenant/**\{tenant\}**/oauth/token → https://authentication.myauthserver.com/tenant/**mytenant**/oauth/token
-   https://oauth.**\{tenant\}**.myauthserver.com/token → https://oauth.**mytenant**.myauthserver.com/token



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

`tokenServiceUser`

</td>
<td valign="top">

User for basic authentication to OAuth server \(if required\).

</td>
</tr>
<tr>
<td valign="top">

`tokenServicePassword`

</td>
<td valign="top">

Password for `tokenServiceUser` \(if required\).

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

The value of the OAuth 2.0 scope parameter expressed as a list of space-delimited, case-sensitive strings.

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

> ### Note:  
> If set to `false`, but `tokenServiceUser` / `tokenServicePassword` are set, `tokenServiceUser` / `tokenServicePassword` are taken with priority.



</td>
</tr>
<tr>
<td valign="top">

`clientAssertion.type`

</td>
<td valign="top">

When using this destination as a client assertion provider, you can specify the format of the client assertion as defined by the authorization server. The supported values are:

-   "urn:ietf:params:oauth:client-assertion-type:saml2-bearer" =\> indicating a SAML Bearer assertion.
-   "urn:ietf:params:oauth:client-assertion-type:jwt-bearer" =\> indicating a JWT Bearer token.

This is used in case of automated client assertion fetching by the service.

For more information, see [Client Assertion with Automated Assertion Fetching by the Service](client-assertion-with-automated-assertion-fetching-by-the-service-1c34472.md).

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
</table>

> ### Note:  
> When the OAuth authorization server is called, it accepts the trust settings of the destination, see [Server Certificate Authentication](server-certificate-authentication-e75d7f1.md).

When using an SAP BTP Neo OAuth service \(`https://api.{landscape-domain}/oauth2/apitoken/v1?grant_type=client_credentials` or `oauthasservices.{landscape-domain}/oauth2/apitoken/v1?grant_type=client_credentials`\) as `TokenServiceURL`, or any other OAuth token service which accepts client credentials only as authorization header, you must set the `clientId` and `clientSecret` values also for the `tokenServiceUser` and `tokenServicePassword` properties.



<a name="loio4e1d742a3d45472d83b411e141729795__section_ijx_thr_1mb"/>

## Example: Neo OAuth Token Service

> ### Sample Code:  
> ```
> URL=https://api.{landscape-domain}/desired-service-path
> Name=sapOAuthCC
> ProxyType=Internet
> Type=HTTP
> Authentication=OAuth2ClientCredentials
> tokenServiceURL=(https://api.{landscape-domain}/oauth2/apitoken/v1?grant_type=client_credentials
> tokenServiceUser=clientIdValue
> tokenServicePassword=secretValue
> clientId=clientIdValue
> clientSecret=secretValue
> ```



<a name="loio4e1d742a3d45472d83b411e141729795__section_bgl_y3w_cfb"/>

## Example: OAuth Token Service Accepting Client Credentials as Body

> ### Sample Code:  
> ```
> URL=https://demo.sapjam.com/OData/OData.svc
> Name=sap_jam_odata
> ProxyType=Internet
> Type=HTTP
> Authentication=OAuth2ClientCredentials
> tokenServiceURL=http://demo.sapjam.com/api/v1/auth/token
> tokenServiceUser=tokenserviceuser
> tokenServicePassword=pass
> clientId=clientId
> clientSecret=secret
> ```



<a name="loio4e1d742a3d45472d83b411e141729795__section_or5_lgr_1mb"/>

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

