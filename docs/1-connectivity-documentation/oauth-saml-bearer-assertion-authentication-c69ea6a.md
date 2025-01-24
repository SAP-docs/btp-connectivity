<!-- loioc69ea6aacd714ad2ae8ceb5fc3ceea56 -->

# OAuth SAML Bearer Assertion Authentication

Create and configure an *OAuth SAML Bearer Assertion* destination for an application.



## Context

You can call an OAuth2-protected remote system/API and propagate a user ID to the remote system by using the `OAuth2SAMLBearerAssertion` authentication type. The Destination service provides functionality for automatic token retrieval and caching, by automating the construction and sending of the SAML assertion. This simplifies application development, leaving you with only constructing the request to the remote system by providing the token, which is fetched for you by the Destination service. For more information, see [User Propagation via SAML 2.0 Bearer Assertion Flow](user-propagation-via-saml-2-0-bearer-assertion-flow-3cb7b81.md).



## Properties

The table below lists the destination properties for *OAuth2SAMLBearerAssertion* authentication type. You can find the values for these properties in the provider-specific documentation of OAuth-protected services. Usually, only a subset of the optional properties is required by a particular service provider.


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

Name of the destination. Must be unique for the destination level.

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

Authentication type. Use `OAuth2SAMLBearerAssertion` as value.

</td>
</tr>
<tr>
<td valign="top">

`KeyStoreLocation`

</td>
<td valign="top">

Contains the name of the certificate configuration to be used for *per-destination* SAML assertion signing. This certificate will be used instead of the standard subaccount-wide signing key.

For more information, see [Set up Trust Between Systems](set-up-trust-between-systems-82dbeca.md).

</td>
</tr>
<tr>
<td valign="top">

`KeyStorePassword` 

</td>
<td valign="top">

Contains the password for the certificate configuration \(if one is needed\) when using a *per-destination* SAML assertion signing certificate.

</td>
</tr>
<tr>
<td valign="top">

`audience`

</td>
<td valign="top">

Intended audience for the assertion, which is verified by the OAuth authorization server.

For more information, see [SAML 2.0 Bearer Assertion Profiles for OAuth 2.0](https://tools.ietf.org/id/draft-ietf-oauth-saml2-bearer-07.html#assertion_reqs).

> ### Note:  
> If the `SAMLAssertionProvider` property of the destination is set to `ClientProvided`, this property will not be used.



</td>
</tr>
<tr>
<td valign="top">

`clientKey`

</td>
<td valign="top">

Key that identifies the consumer to the authorization server.

</td>
</tr>
<tr>
<td valign="top">

`tokenServiceURL`

</td>
<td valign="top">

The URL of the token service, against which the token exchange is performed. Depending on the `Token Service URL` type, this property is interpreted in different ways during the automatic token retrieval:

-   For `Dedicated`, the token service URL is taken as is.
-   For `Common`, the token service URL is searched for the tenant placeholder `{tenant}`.

    `{tenant}` is resolved as the subdomain of the subaccount on behalf of which the caller is performing the call. If the placeholder is not found, `{tenant}` is inserted as a subdomain of the token service URL.

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

`tokenServiceURLType`

</td>
<td valign="top">

Either `Dedicated` - if the token service URL serves only a single tenant, or `Common` - if the token service URL serves multiple tenants.

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
<td valign="top">

\(Deprecated\) `SystemUser`

</td>
<td valign="top">

User to be used when requesting an access token from the OAuth authorization server. If this property is not specified, the currently logged-in user is used.

> ### Caution:  
> This property is deprecated and will be removed soon. We recommend that you work on behalf of specific \(named\) users instead of working with a technical user.
> 
> As an alternative for technical user communication, we strongly recommend that you use one of these authentication types:
> 
> -   Basic Authentication \(see [Client Authentication Types for HTTP Destinations](client-authentication-types-for-http-destinations-4e13a04.md)\)
> 
> -   Client Certificate Authentication \(see [Client Authentication Types for HTTP Destinations](client-authentication-types-for-http-destinations-4e13a04.md)\)
> -   [OAuth Client Credentials Authentication](oauth-client-credentials-authentication-4e1d742.md)
> 
> To extend an OAuth access token's validity, consider using an OAuth refresh token.



</td>
</tr>
<tr>
<td valign="top">

`authnContextClassRef`

</td>
<td valign="top">

Value of the `AuthnContextClassRef` tag, which is part of generated `OAuth2SAMLBearerAssertion` authentication. For more information, see [SAML 2.0 specification](http://saml.xml.org/saml-specifications).

</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Additional**

</td>
</tr>
<tr>
<td valign="top">

`SAMLAssertionProvider`

</td>
<td valign="top">

Specifies how the SAML assertion will be provided to the token service. There are two possible values:

-   `DestinationServiceGenerated`: specifies that Destination service will generate the SAML assertion, sign it using the subaccount trust certificate, and pass it to the token service.
-   `ClientProvided`: specifies that the client will provide the SAML assertion externally to the Destination service, and the service will pass it to the token service.

If the property is missing, the Destination service will treat it by default as if the property was set to `DestinationServiceGenerated`.

</td>
</tr>
<tr>
<td valign="top">

`nameQualifier`

</td>
<td valign="top">

Security domain of the user for which access token is requested.

</td>
</tr>
<tr>
<td valign="top">

`companyId`

</td>
<td valign="top">

Company identifier.

</td>
</tr>
<tr>
<td valign="top">

`assertionIssuer`

</td>
<td valign="top">

Issuer of the SAML assertion.

</td>
</tr>
<tr>
<td valign="top">

`assertionRecipient`

</td>
<td valign="top">

Recipient of the SAML assertion. If not set, the token service URL will be the assertion's recipient.

</td>
</tr>
<tr>
<td valign="top">

`nameIdFormat`

</td>
<td valign="top">

Value of the `NameIdFormat` tag, which is part of generated `OAuth2SAMLBearerAssertion` authentication. For more information, see [SAML 2.0 specification](http://saml.xml.org/saml-specifications).

</td>
</tr>
<tr>
<td valign="top">

`userIdSource`

</td>
<td valign="top">

When this property is set, the generated SAML2 assertion uses the currently logged-in user as a value for the `NameId` tag. See [User Propagation via SAML 2.0 Bearer Assertion Flow](user-propagation-via-saml-2-0-bearer-assertion-flow-3cb7b81.md).

</td>
</tr>
<tr>
<td valign="top">

`scope`

</td>
<td valign="top">

The value of the OAuth 2.0 scope parameter, expressed as a list of space-delimited, case-sensitive strings.

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

Contains the name of the certificate configuration to be used for mTLS towards the token service. This property is required when using [OAuth with X.509 Client Certificates](oauth-with-x-509-client-certificates-2c162aa.md).

</td>
</tr>
<tr>
<td valign="top">

`tokenService.KeyStorePassword`

</td>
<td valign="top">

Contains the password for the certificate configuration \(if one is needed\) when using [OAuth with X.509 Client Certificates](oauth-with-x-509-client-certificates-2c162aa.md).

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

`x_user_token.jwks`

</td>
<td valign="top">

Base64-encoded *JSON web key set*, containing the signing keys which are used to validate the JWT provided in the *X-User-Token* header.

For more information, see[JWK Set Format](https://tools.ietf.org/html/rfc7517#section-5).

</td>
</tr>
<tr>
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

`skipUserAttributesPrefixInSAMLAttributes`

</td>
<td valign="top">

If set to true, any additional attributes taken from the OAuth server's user information endpoint, under the *user\_attributes* section, will be added to the assertion without the prefix that the Destination service would usually add to them. For more information, see [User Propagation via SAML 2.0 Bearer Assertion Flow](user-propagation-via-saml-2-0-bearer-assertion-flow-3cb7b81.md).

</td>
</tr>
<tr>
<td valign="top">

`includeSigningCertificateInSAMLAssertion`

</td>
<td valign="top">

If set to true, the public part of the signing certificate, used for signing the SAML assertion, will be included in the XML structure of the assertion. Some assertion recipients may require this to accept the assertion.

</td>
</tr>
<tr>
<td valign="top">

`skipUserUuidInSAMLAttributes`

</td>
<td valign="top">

If set to true, any SAML assertion attribute with name 'user\_uuid' will not be added to the resulting SAML assertion XML, even if such was found in the JWT, specifying the user's identity.

</td>
</tr>
</table>



## Example

The connectivity destination below provides HTTP access to the OData API of the SuccessFactors Jam.

```ini
URL=https://demo.sapjam.com/OData/OData.svc
Name=sap_jam_odata
ProxyType=Internet
Type=HTTP
Authentication=OAuth2SAMLBearerAssertion
tokenServiceURL=https://demo.sapjam.com/api/v1/auth/token
clientKey=<unique_generated_string>
audience=cubetree.com
nameQualifier=www.successfactors.com
apiKey=<apiKey>
```

The response for "find destination" contains an `authTokens` object in the format given below. For more information on the fields in `authTokens`, see ["Find Destination" Response Structure](find-destination-response-structure-83a3f3b.md).

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

**Related Information**  


[Create HTTP Destinations](create-http-destinations-783fa1c.md "Create HTTP destinations in the Destinations editor (SAP BTP cockpit).")

[Destination Examples](destination-examples-3a2d575.md "Find configuration examples for HTTP and RFC destinations in SAP BTP, using different authentication types.")

[User Propagation via SAML 2.0 Bearer Assertion Flow](user-propagation-via-saml-2-0-bearer-assertion-flow-3cb7b81.md "Learn about the process for automatic token retrieval, using the OAuth2SAMLBearerAssertion authentication type for HTTP destinations.")

[User Propagation between Cloud Foundry Applications](user-propagation-between-cloud-foundry-applications-8ebf60c.md "Propagate the identity of a user between Cloud Foundry applications that are located in different subaccounts or regions.")

[Exchanging User JWTs via OAuth2UserTokenExchange Destinations](exchanging-user-jwts-via-oauth2usertokenexchange-destinations-39d4265.md "Automatic token retrieval using the OAuth2UserTokenExchange authentication type for HTTP destinations.")

