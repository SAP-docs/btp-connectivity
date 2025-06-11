<!-- loiod716d41144c54838a42a1a14a21c7abd -->

# IAS-generated SAML Assertion to OAuth2 Bearer Token Chain

Use a predefined destination chain to generate and consume IAS \(Identity Authentication service\)-signed SAML assertions.

This predefined destination chain simplifies the process of generating and consuming IAS-signed SAML assertions. The chain works in a 2-step process. The first step consumes one destination to generate the IAS-signed SAML assertion, while the second step uses a different destination to consume the generated assertion in order to retrieve a token from a token server.

> ### Note:  
> For more information on identity authentication, see [SAP Cloud Identity Services](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/landing-page?version=Cloud).



<a name="loiod716d41144c54838a42a1a14a21c7abd__section_wxs_vmv_c2c"/>

## Chain Variable Consumption

To successfully consume the chain, the following headers must be included in the request to the *Find a Destination* REST API endpoint:


<table>
<tr>
<th valign="top">

Header Name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`X-chain-var-samlProviderDestinationName`

</td>
<td valign="top">

Specifies the name of the destination, which will be retrieved by the Destination service and whose properties will be used to generate the IAS-signed SAML assertion.

</td>
</tr>
<tr>
<td valign="top">

`X-chain-var-subjectToken` 

</td>
<td valign="top">

Specifies the value of the subject token \(an access token usually associated with the user principal\), which will be used by Destination service to perform the token exchange for a IAS-signed SAML assertion.

</td>
</tr>
<tr>
<td valign="top">

`X-chain-var-subjectTokenType` 

</td>
<td valign="top">

Specifes the type of the subject token, which will be used by Destination service to perform the token exchange for a IAS-signed SAML assertion. The only accepted value is **"urn:ietf:params:oauth:token-type:access\_token"**.

</td>
</tr>
</table>

**Related Information**  


[Token Retrieval Using IAS-Signed SAML2.0 Assertions](token-retrieval-using-ias-signed-saml2-0-assertions-a943bb7.md "Retrieve access tokens from token servers using IAS (Identity Authentication service)-signed SAML2.0 assertions.")

