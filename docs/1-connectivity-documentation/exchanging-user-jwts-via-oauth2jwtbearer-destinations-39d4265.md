<!-- loio39d42654093e4f8db20398a06f7eab2b -->

# Exchanging User JWTs via OAuth2JWTBearer Destinations

Automatic token retrieval using the `OAuth2JWTBearer` authentication type for HTTP destinations.



<a name="loio39d42654093e4f8db20398a06f7eab2b__content"/>

## Content

[Prerequisites](exchanging-user-jwts-via-oauth2jwtbearer-destinations-39d4265.md#loio39d42654093e4f8db20398a06f7eab2b__prereq)

[Automated Access Token Retrieval](exchanging-user-jwts-via-oauth2jwtbearer-destinations-39d4265.md#loio39d42654093e4f8db20398a06f7eab2b__retrrieval)

[Scenarios](exchanging-user-jwts-via-oauth2jwtbearer-destinations-39d4265.md#loio39d42654093e4f8db20398a06f7eab2b__scenarios)



<a name="loio39d42654093e4f8db20398a06f7eab2b__prereq"/>

## Prerequisites

You have configured an *OAuth2JWTBearer* destination. See [OAuth JWT Bearer Authentication](oauth-jwt-bearer-authentication-283cd2d.md).

Back to [Content](exchanging-user-jwts-via-oauth2jwtbearer-destinations-39d4265.md#loio39d42654093e4f8db20398a06f7eab2b__content)



<a name="loio39d42654093e4f8db20398a06f7eab2b__retrrieval"/>

## Automated Access Token Retrieval

You can make use of the automated access token retrieval functionality, available via:

-   The ["Find a destination"](destination-service-rest-api-23ccafb.md) endpoint.

    For information about the response structure, see ["Find a Destination" Response Structure](find-a-destination-response-structure-83a3f3b.md).

-   the ["Consume a destination"](referring-resources-using-the-consume-rest-api-78ba73a.md) endpoint.

The logic for controlling the token that gets exchanged is simple.

**Using the `X-user-token` Header**

If the `X-user-token` header is provided with the request to the Destination service and its value is not empty, it will be used with priority over the `Authorization` header for the token exchange operation. This means that the user token from this header will be used when determining the user and the tenant subdomain. It will also be the token for which token exchange is performed.

**Using the `Authorization` Header**

If `X-user-token header` is not provided with the request to the Destination service, or it is provided, but its value is empty, the token from the `Authorization` header will be used. The value of the header must be a user JWT \(JSON Web token\) in encoded form \(see [RFC 7519](https://tools.ietf.org/html/rfc7519)\). Otherwise, token exchange will not work.

Back to [Content](exchanging-user-jwts-via-oauth2jwtbearer-destinations-39d4265.md#loio39d42654093e4f8db20398a06f7eab2b__content)



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

The user token to be exchanged, previously retrieved by the application via exchanging the initial user token, passed to the application \(to another user access token\) via the client credentials of the Destination service instance \(bound to the application\), using the provider tenant-specific token service URL.

</td>
</tr>
<tr>
<td valign="top">

Exchange a user token:

-   Issued on behalf of a tenant, **subscribed to your application**
-   Using a destination in the **application provider tenant**



</td>
<td valign="top">

<User token to be exchanged\>

</td>
<td valign="top">

Access token retrieved via the client credentials of the Destination service instance \(bound to the application\), using the provider tenant-specific token service URL.

</td>
</tr>
<tr>
<td valign="top">

Exchange a user token:

-   Issued on behalf of a tenant, **subscribed to your application**
-   Using a destination in the **subscriber tenant**



</td>
<td valign="top">

<User token to be exchanged\>

</td>
<td valign="top">

Access token retrieved via the client credentials of the Destination service instance \(bound to the application\), using the subscriber tenant-specific token service URL.

</td>
</tr>
</table>

Back to [Content](exchanging-user-jwts-via-oauth2jwtbearer-destinations-39d4265.md#loio39d42654093e4f8db20398a06f7eab2b__content)

