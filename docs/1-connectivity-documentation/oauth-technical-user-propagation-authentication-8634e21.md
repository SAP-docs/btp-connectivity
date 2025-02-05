<!-- loio8634e210446844d09ae9627b450822fd -->

# OAuth Technical User Propagation Authentication

Learn about the *OAuth2TechnicalUserPropagation* authentication type for HTTP destinations: use cases, supported properties and examples.



<a name="loio8634e210446844d09ae9627b450822fd__section_g21_5wt_hvb"/>

## Overview

SAP BTP supports the propagation of technical users from the cloud application towards on-premise systems. In the Destination service, an access token representing the technical user is retrieved, which can then be sent in a header to the Connectivity service. This is similar to *principal propagation*, but in this case, a technical user is propagated instead of a business user.

The retrieval of the access token performs the OAuth 2.0 client credentials flow, according to the token service configurations in the destination. The token service is called from the Internet, not from the [Cloud Connector](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/e6c7616abb5710148cfcf3e75d96d596.html).

> ### Note:  
> The retrieved access token is cached for the duration of its validity.

> ### Restriction:  
> This authentication type is not yet available for destination configuration via the cockpit.



<a name="loio8634e210446844d09ae9627b450822fd__section_al2_cjh_ytb"/>

## Properties

The table below lists the destination properties for the *OAuth2TechnicalUserPropagation* authentication type.


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

You can only use proxy type `OnPremise`.

> ### Remember:  
> The token service is not accessed through the Cloud Connector, but through the Internet.



</td>
</tr>
<tr>
<td valign="top">

`Authentication`

</td>
<td valign="top">

Authentication type. Use `OAuth2TechnicalUserPropagation` as value.

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

The URL of the token service, against which the token exchange is performed. Depending on the `Token Service URL Type`, this property is interpreted in different ways during the automatic token retrieval:

-   For `Dedicated`, the token service URL is taken as is.
-   For `Common`, the token service URL is searched for the tenant placeholder `{tenant}`.

    `{tenant}` is resolved as the subdomain of the subaccount on behalf of which the caller is performing the call. If the placeholder is not found, `{tenant}` is inserted as a subdomain of the token service URL.

    Consult the [Destination Service REST API](destination-service-rest-api-23ccafb.md) to see how the subdomain of the subaccount is specified. The subaccount subdomain is mandated during creation of the subaccount, see [Create a Subaccount](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/05280a123d3044ae97457a25b3013918.html).


**Examples** of interpreting the `tokenServiceURL` for `tokenServiceURLType`=`Common`, if the call to the Destination service is on behalf of a subaccount subdomain with value `mytenant`:

-   ***https://authentication.us10.hana.ondemand.com/oauth/token*** → ***https://mytenant.authentication.us10.hana.ondemand.com/oauth/token***
-   ***https://\{tenant\}.authentication.us10.hana.ondemand.com/oauth/token*** → ***https://mytenant.authentication.us10.hana.ondemand.com/oauth/token***
-   ***https://authentication.myauthserver.com/tenant/\{tenant\}/oauth/token*** → ***https://authentication.myauthserver.com/tenant/mytenant/oauth/token***
-   ***https://oauth.\{tenant\}.myauthserver.com/token*** → ***https://oauth.mytenant.myauthserver.com/token*** 



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

User for basic authentication to the OAuth server \(if required\).

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

> ### Note:  
> If set to `false`, but `tokenServiceUser` / `tokenServicePassword` are also set, `tokenServiceUser` / `tokenServicePassword` will be taken with priority.



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
> When the OAuth authorization server is called, it accepts the trust settings of the destination. For more information, see [Server Certificate Authentication](server-certificate-authentication-e75d7f1.md).

> ### Caution:  
> When using the OAuth service of the SAP BTP *Neo* environment \(*https://api.\{landscape-domain\}/oauth2/apitoken/v1?grant\_type=client\_credentials or oauthasservices.\{landscape-domain\}/oauth2/apitoken/v1?grant\_type=client\_credentials*\) as `TokenServiceURL`, or any other OAuth token service which accepts client credentials **only as Authorization header**, you must also set the `clientId` and `clientSecret` values for `tokenServiceUser` and `tokenServicePassword` properties.



<a name="loio8634e210446844d09ae9627b450822fd__section_ptz_vwt_hvb"/>

## Example: OAuth Technical User Propagation Destination

> ### Sample Code:  
> ```
> Name=technical-user-example
> Type=HTTP
> URL=http://protected-url.example.com
> ProxyType=OnPremise
> Authentication=OAuth2TechnicalUserPropagation
> clientId=clientId
> clientSecret=secret1234
> tokenServiceURL=http://authserver.example.com/oauth/token
> ```



<a name="loio8634e210446844d09ae9627b450822fd__section_ugv_vwt_hvb"/>

## Example: authTokens Object in *Find Destination* Response

The response for *Find Destination* will contain an `authTokens` object in the format given below. For more information on the fields in `authTokens`, see ["Find a Destination" Response Structure](find-a-destination-response-structure-83a3f3b.md).

For usage of the `SAP-Connectivity-Technical-Authentication` header, see [Authentication Types](authentication-to-the-on-premise-system-67b0b94.md#loio67b0b94f09f2446598787eea0855e56b__types).

> ### Sample Code:  
> ```
> "authTokens": [
>     {
>         "type": "Bearer",
>         "value": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiI...",
>         "http_header": {
>             "key":"SAP-Connectivity-Technical-Authentication",
>             "value":"Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiI..."
>         }
>     }
> ]
> ```

