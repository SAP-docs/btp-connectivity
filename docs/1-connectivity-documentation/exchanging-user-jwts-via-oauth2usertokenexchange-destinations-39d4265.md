<!-- loio39d42654093e4f8db20398a06f7eab2b -->

# Exchanging User JWTs via OAuth2UserTokenExchange Destinations

Automatic token retrieval using the `OAuth2UserTokenExchange` authentication type for HTTP destinations.



<a name="loio39d42654093e4f8db20398a06f7eab2b__content"/>

## Content

[Prerequisites](exchanging-user-jwts-via-oauth2usertokenexchange-destinations-39d4265.md#loio39d42654093e4f8db20398a06f7eab2b__prereq)

[Automated Access Token Retrieval](exchanging-user-jwts-via-oauth2usertokenexchange-destinations-39d4265.md#loio39d42654093e4f8db20398a06f7eab2b__retrrieval)

[Scenarios](exchanging-user-jwts-via-oauth2usertokenexchange-destinations-39d4265.md#loio39d42654093e4f8db20398a06f7eab2b__scenarios)



<a name="loio39d42654093e4f8db20398a06f7eab2b__prereq"/>

## Prerequisites

You have configured an OAuth2UserTokenExchange destination. See [OAuth User Token Exchange Authentication](oauth-user-token-exchange-authentication-e3c333f.md).

The token to be exchanged must have the **uaa.user** scope to enable the token exchange. See [SAP Authorization and Trust Management Service](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/6373bb7a96114d619bfdfdc6f505d1b9.html "The global account and subaccounts get their users from identity providers. Administrators make sure that users can only access their dedicated subaccount by making sure that there is a dedicated trust relationship only between the identity providers and the respective subaccounts. Developers configure and deploy application-based security artifacts containing authorizations, and administrators assign these authorizations using the SAP BTP cockpit.") :arrow_upper_right: for more details.

Back to [Content](exchanging-user-jwts-via-oauth2usertokenexchange-destinations-39d4265.md#loio39d42654093e4f8db20398a06f7eab2b__content)



<a name="loio39d42654093e4f8db20398a06f7eab2b__retrrieval"/>

## Automated Access Token Retrieval

For destinations of authentication type `OAuth2UserTokenExchange`, you can use the automated token retrieval functionality via the "find destination" endpoint, see [Call the Destination Service](consuming-the-destination-service-7e30625.md#loio7e306250e08340f89d6c103e28840f30__section_CallDestinationService).

If you provide the user token exchange header with the request to the Destination service and its value is not empty, it is used instead of the `Authorization` header to specify the user and the tenant subdomain. It will be the token for which token exchange is performed.

-   The header value must be a user JWT \(JSON Web token\) in encoded form, see [RFC 7519](https://tools.ietf.org/html/rfc7519).
-   If the user token exchange header is not provided with the request to the Destination Service or it is provided, but its value is empty, the token from the `Authorization` header is used instead. In this case, the JWT in the `Authorization` header must be a user JWT in encoded form, otherwise the token exchange does not work.

For information about the response structure of this request, see ["Find a Destination" Response Structure](find-a-destination-response-structure-83a3f3b.md).

Back to [Content](exchanging-user-jwts-via-oauth2usertokenexchange-destinations-39d4265.md#loio39d42654093e4f8db20398a06f7eab2b__content)



<a name="loio39d42654093e4f8db20398a06f7eab2b__scenarios"/>

## Scenarios

To achieve specific token exchange goals, you can use the following headers and values when calling the Destination service:


<table>
<tr>
<th valign="top">

Goal

</th>
<th valign="top">

User Token Exchange Header

</th>
<th valign="top">

Authorization Header

</th>
</tr>
<tr>
<td valign="top">

Exchange a user token:

-   Issued on behalf of the **application provider tenant**
-   Using a destination in the **application provider tenant**



</td>
<td valign="top">

Not used

</td>
<td valign="top">

`The user token to be exchanged`

Previously retrieved by the application via exchanging the initial user token, passed to the application \(to another user access token\) via the client credentials of the Destination service instance \(bound to the application\), using the provider tenant-specific token service URL.

</td>
</tr>
<tr>
<td valign="top">

Exchange a user token:

-   Issued on behalf of a tenant, **subscribed to your application**
-   Using a destination in the **application provider tenant**



</td>
<td valign="top">

`<User token to be exchanged>`

</td>
<td valign="top">

`Access token`

Retrieved via the client credentials of the Destination service instance \(bound to the application\), using the provider tenant-specific token service URL.

</td>
</tr>
<tr>
<td valign="top">

Exchange a user token:

-   Issued on behalf of a tenant, **subscribed to your application**
-   Using a destination in the **subscriber tenant**



</td>
<td valign="top">

`<User token to be exchanged>` 

</td>
<td valign="top">

`Access token`

Retrieved via the client credentials of the Destination service instance \(bound to the application\), using the subscriber tenant-specific token service URL.

</td>
</tr>
</table>

Back to [Content](exchanging-user-jwts-via-oauth2usertokenexchange-destinations-39d4265.md#loio39d42654093e4f8db20398a06f7eab2b__content)

