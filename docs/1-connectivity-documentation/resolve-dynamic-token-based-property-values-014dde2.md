<!-- loio014dde2fc479481a98403c75b2b3d127 -->

# Resolve Dynamic Token-Based Property Values

Learn how to resolve dynamic values in the additional properties of a destination from token claims.

This feature allows to resolve additional properties of a destination at retrieval time from the claims of the calling user's JWT. It lets you keep a single destination configuration whose additional properties adapt to the user making the request - for example, forwarding the caller's user name, zone ID or a nested identity attribute to the target system.

> ### Note:  
> Resolution is offered **only for additional properties**. The core destination properties are not modified, even if they contain placeholder-like text.



## Prerequisites

To use dynamic token-based property values, you need a configured destination with at least one additional property containing a placeholder.



## Placeholder Syntax

A placeholder has the form:

`{<jsonpath>}`

where `<jsonpath>` is a `JsonPath` expression starting with `$`, evaluated against the JWT claims of the request. Bracket notation is used for claim names - the same convention as `userIdSource` - which also handles claim names that contain dots:


<table>
<tr>
<th valign="top">

Placeholder

</th>
<th valign="top">

Resolves To

</th>
</tr>
<tr>
<td valign="top">

`{$.['user_name']}`

</td>
<td valign="top">

top-level `user_name` claim

</td>
</tr>
<tr>
<td valign="top">

`{$.['ext_attr']['subaccountid']}`

</td>
<td valign="top">

nested `ext_attr.subaccountid` claim

</td>
</tr>
<tr>
<td valign="top">

`{$.['xs.system.attributes']['xs.saml.groups']}`

</td>
<td valign="top">

nested claim whose keys contain dots

</td>
</tr>
</table>

A value may contain static text and more than one placeholder:

`"usernamePrefix": "prefix-{$.['user_name']}"`

`"id": "{$.['user_name']}@{$.['zid']}"`

`"grant_type": "urn:{$.['grant_type']}:token"`



## Which Token is Used

The claims are taken from the request headers in this order:

1.  `X-user-token` - if present, its claims are used.
2.  `Authorization` \(Bearer\) - used only when no `X-user-token` header is present.



## Resolution Rules

-   Known scalar claim \(string, number, or boolean\) - the placeholder is replaced with the claim value.
-   Unknown claim - the placeholder is left literal \(unchanged\); the request does not fail.
-   Malformed placeholder / invalid `JsonPath` - left literal; the request does not fail.
-   Non-scalar claim - the placeholder is left literal \(unchanged\); only scalar claims are resolved.



## Calling the "Find Destination" Endpoint

**Path**: `/destination-configuration/v1/destinations/<destination-name>`

**Example of a Call \(cURL\)**

> ### Sample Code:  
> ```
> curl "<uri>/destination-configuration/v1/destinations/<destination-name>" \
>   -X GET \
>   -H "Authorization: Bearer <jwtToken>" \
>   -H "X-user-token: <userJwtToken>"
> ```

**Example of a Configured Destination** 

> ### Sample Code:  
> ```
>  {
>   "Name": "demo-destination",
>   "URL": "https://example.com",
>   "Type": "HTTP",
>   "ProxyType": "Internet",
>   "Authentication": "NoAuthentication",
>   "customProp": "user-{$.['user_name']}"
> }
> ```

**Example of a Response** 

The `X-user-token` carries a JWT with claim `user_name = testUser`. The additional property `customProp` is resolved; core properties remain untouched:

> ### Sample Code:  
> ```
> {
>   "owner": {
>     "SubaccountId": "<id>",
>     "InstanceId": null
>   },
>   "destinationConfiguration": {
>     "Name": "demo-destination",
>     "URL": "https://example.com",
>     "Type": "HTTP",
>     "ProxyType": "Internet",
>     "Authentication": "NoAuthentication",
>     "customProp": "user-testUser"
>   }
> }
> ```



## Calling the "Consume API Destination" Endpoint

**Path**: `/destination-configuration/v2/destinations/<destination-name>@subaccount`

The *Consume API* endpoint supports the same placeholder resolution behavior as the *Find Destination* endpoint. Provide an `X-user-token header` to resolve placeholders from a specific user's claims. Resolution rules, token priority and failure handling are identical between both endpoints.

If the token had no `user_name` claim, `customProp` would be returned as `'user-{$.['user_name']}'`.

