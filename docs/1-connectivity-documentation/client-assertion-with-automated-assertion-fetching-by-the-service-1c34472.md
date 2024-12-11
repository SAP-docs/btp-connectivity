<!-- loio1c344728e9604191977795433ab668f7 -->

# Client Assertion with Automated Assertion Fetching by the Service

Use the *Find Destination* API to fetch client assertions automatically when using client assertion with OAuth flows for a destination.

The *Find Destination* API lets you fetch client assertions automatically and then use them for retrieving tokens from authorization servers that accept client assertions as a client authentication mechanism.

To apply this mechanism, you must use the following of destination configurations:

-   Destination that provides the client assertion - with specified token service that issues client assertions
-   Destination that uses the client assertion - with specified token service that uses client assertion as a client authentication mechanism

> ### Caution:  
> Only *OAuth2ClientCredentials* authentication type is allowed for destinations that provide client assertions.The following authentication types are supported for destinations that use client assertions: *OAuth2Password*, *OAuth2ClientCredentials*, *OAuth2AuthorizationCode*, *OAuth2TechnicalUserPropagation*, *OAuth2TokenExchange*.



<a name="loio1c344728e9604191977795433ab668f7__section_i5b_4bl_cxb"/>

## Define the Client Assertion Type

The client assertion type must be defined as a property in the destination that provides the client assertion:


<table>
<tr>
<th valign="top">

Property

</th>
<th valign="top">

Value

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`clientAssertion.type`

</td>
<td valign="top">

Absolute URI

</td>
<td valign="top">

The format of the assertion as defined by the authorization server. The supported values are:

-   "urn:ietf:params:oauth:client-assertion-type:saml2-bearer" =\> indicating a SAML Bearer Assertion.
-   "urn:ietf:params:oauth:client-assertion-type:jwt-bearer" =\> indicating a JWT Bearer Token.



</td>
</tr>
</table>



<a name="loio1c344728e9604191977795433ab668f7__section_xh2_4bl_cxb"/>

## Use a Property to Add a Reference to the Destination that Provides the Client Assertion

The destination that provides the client assertion can be specified in a property of the destination that uses client assertions:


<table>
<tr>
<th valign="top">

Property

</th>
<th valign="top">

Value

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`clientAssertion.destinationName`

</td>
<td valign="top">

Name of a destination

</td>
<td valign="top">

Name of the destination that provides the client assertion. Must be on the same subaccount or service instance as the destination that uses client assertions.

</td>
</tr>
</table>

> ### Caution:  
> If headers `X-client-assertion` and `X-client-assertion-type` are specified in the *Find Destination* API call, the `clientAssertion.destinationName` property will not be used for an automated assertion fetching mechanism.



<a name="loio1c344728e9604191977795433ab668f7__section_f33_4bl_cxb"/>

## Use a Header to Specify the Destination that Provides the Client Assertion

Alternatively, the destination that provides the client assertion can also be specified in a header in the *Find Destination* API.


<table>
<tr>
<th valign="top">

Header

</th>
<th valign="top">

Value

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`X-client-assertion-destination-name`

</td>
<td valign="top">

Name of a destination

</td>
<td valign="top">

Name of the destination that provides the client assertion. Must be on the same subaccount or service instance as the destination that uses client assertions.

</td>
</tr>
</table>

If specified, this header overrides the property `clientAssertion.destinationName` in the destination that uses client assertions.

> ### Caution:  
> Usage of headers `X-client-assertion` and `X-client-assertion-type` is not allowed if this header is present.



<a name="loio1c344728e9604191977795433ab668f7__section_zlj_4bl_cxb"/>

## Example: Destination that Provides Client Assertions

> ### Sample Code:  
> ```
> Name=Provides_Client_Assertion_Destination
> Type=HTTP
> URL= https://xxxx.example.com
> ProxyType=Internet
> Authentication=OAuth2ClientCredentials
> clientId=clientId
> clientSecret=secret1234
> tokenServiceURL=https://authserver1.example.com/oauth/token/
> clientAssertion.type=urn:ietf:params:oauth:client-assertion-type:jwt-bearer
> ```



<a name="loio1c344728e9604191977795433ab668f7__section_hlk_4bl_cxb"/>

## Example: Destination that Uses Client Assertions

> ### Sample Code:  
> ```
> Name=Uses_Client_Assertion_Destination
> Type=HTTP
> URL= https://xxxx.example.com
> ProxyType=Internet
> Authentication=OAuth2ClientCredentials
> clientId=clientId
> tokenServiceURL=https://authserver2.example.com/oauth/token/
> clientAssertion.destinationName=Provides_Client_Assertion_Destination
> ```



<a name="loio1c344728e9604191977795433ab668f7__section_ky3_mbl_cxb"/>

## Example: *Find Destination* API Call for Client Assertion Authentication with Automated Assertion Fetching

curl call:

> ### Sample Code:  
> ```
> curl --location --request GET 'https://<destination_service_host>/destination-configuration/v1/destinations/<name_of_destination_that_uses_client_assertions>' \
> --header 'Authorization: Bearer <access_token>'
> ```

