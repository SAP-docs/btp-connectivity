<!-- loiod81e1683bd434823abf3ceefc4ff157f -->

# SAML Assertion Authentication

Create and configure an *SAML Assertion* destination for an application.



## Context

The Destination service lets you generate SAML assertions as per SAML 2.0 specification. You can retrieve a generated SAML assertion from the Destination service by using the `SAMLAssertion` authentication type, whereas [OAuth SAML Bearer Assertion Authentication](oauth-saml-bearer-assertion-authentication-c69ea6a.md) sends the generated SAML assertion to an OAuth server to get a token. The Destination service provides functionality for caching the generated SAML assertion for later use, and caching by the app whenever needed, which helps simplifying application development.



## Properties

The table below lists the destination properties for the *SAMLAssertion* authentication type.


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

Choose `Internet`, `PrivateLink`, or `OnPremise`.

</td>
</tr>
<tr>
<td valign="top">

`CloudConnectorLocationId`

</td>
<td valign="top">

\(only if `ProxyType=OnPremise`\) Starting with Cloud Connector 2.9.0, you can connect multiple Cloud Connectors to an account , PrivateLinkas long as their location ID is different. The value defines the location ID identifying the Cloud Connector over which the connection is opened.

The default value is an empty string identifying the Cloud Connector that is connected without any location ID, which is also the case for all Cloud Connector versions prior to 2.9.0.

</td>
</tr>
<tr>
<td valign="top">

`Authentication`

</td>
<td valign="top">

Authentication type. Use `SAMLAssertion` as value.

</td>
</tr>
<tr>
<td valign="top">

`audience`

</td>
<td valign="top">

Value of the `Audience` tag, which is part of the generated SAML assertion. For more information, see[SAML 2.0 specification](http://saml.xml.org/saml-specifications).

</td>
</tr>
<tr>
<td valign="top">

`authnContextClassRef`

</td>
<td valign="top">

Value of the `AuthnContextClassRef` tag, which is part of generated SAML assertion. For more information, see [SAML 2.0 specification](http://saml.xml.org/saml-specifications).

</td>
</tr>
<tr>
<td valign="top" colspan="2">

**Additional**

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

`nameQualifier`

</td>
<td valign="top">

When this property is set, the `NameQualifier` under the `NameId` tag of the generated SAML assertion is determined in accordance to the value.

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

Recipient of the SAML assertion.

</td>
</tr>
<tr>
<td valign="top">

`nameIdFormat`

</td>
<td valign="top">

Value of the `NameIdFormat` tag, which is part of generated SAML Assertion. For more information, see [SAML 2.0 specification](http://saml.xml.org/saml-specifications).

</td>
</tr>
<tr>
<td valign="top">

`userIdSource`

</td>
<td valign="top">

When this property is set, the user ID in the `NameId` tag of the generated SAML assertion is determined in accordance to the value of this attribute. For more information, see [User Propagation via SAML 2.0 Bearer Assertion Flow](user-propagation-via-saml-2-0-bearer-assertion-flow-3cb7b81.md).

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
Name=destinationSamlAssertion
Type=HTTP
URL=https://myXXXXXX-api.s4hana.ondemand.com
Authentication=SAMLAssertion
ProxyType=Internet
audience=https://myXXXXXX.s4hana.ondemand.com
authnContextClassRef=urn:oasis:names:tc:SAML:2.0:ac:classes:X509
```

The response for "find destination" contains an `authTokens` object in the format given below. For more information on the fields in `authTokens`, see ["Find a Destination" Response Structure](find-a-destination-response-structure-83a3f3b.md).

> ### Sample Code:  
> ```
> "authTokens": [
>     {
>         "type": "SAML2.0",
>         "value": "PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZ...",
>         "http_header": {
>             "key":"Authorization",
>             "value":"SAML2.0 PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZ..."
>         }
>     }
> ]
> ```

**Related Information**  


[Create HTTP Destinations](create-http-destinations-783fa1c.md "Create HTTP destinations in the Destinations editor (SAP BTP cockpit).")

[Destination Examples](destination-examples-3a2d575.md "Find configuration examples for HTTP and RFC destinations in SAP BTP, using different authentication types.")

[Exchanging User JWTs via OAuth2UserTokenExchange Destinations](exchanging-user-jwts-via-oauth2usertokenexchange-destinations-39d4265.md "Automatic token retrieval using the OAuth2UserTokenExchange authentication type for HTTP destinations.")

