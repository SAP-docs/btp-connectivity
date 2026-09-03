<!-- loio1785b5b6378e42028b19cc80738f3ff3 -->

# Actions

Actions let the Transparent Proxy attach a client-side authentication flow to a destination. When an action is configured, the Transparent Proxy obtains a token at request time and sets it on the request forwarded to the target system.

Depending on the action, the token is set either as the `Authorization` header \(for tokens meant for the target system\) or as the `SAP-Connectivity-Technical-Authentication` header \(for a technical token meant for the Connectivity Proxy\).

Actions are used to enable *Identity Authentication service* \(IAS\) principal propagation and technical access directly from the Transparent Proxy, without additional server-side configuration on the destination.



## Supported Actions


<table>
<tr>
<th valign="top">

Action

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`OAuth2JWTBearer`

</td>
<td valign="top">

*Principal propagation*. Exchanges the caller's IAS token for a new IAS access token using the JWT bearer grant, so the target system receives a token that represents the calling user.

The minted token is set as the `Authorization` header.

</td>
</tr>
<tr>
<td valign="top">

`OAuth2ClientCredentials`

</td>
<td valign="top">

*Technical access*. Obtains a technical \(machine-to-machine\) IAS access token using the client credentials grant. The caller's identity is not used.

</td>
</tr>
<tr>
<td valign="top">

`OAuth2TechnicalUserPropagation`

</td>
<td valign="top">

*Technical access for on-premise connectivity*. Obtains a technical \(machine-to-machine\) IAS access token and sets it as the `SAP-Connectivity-Technical-Authentication` header, which is consumed by the Connectivity Proxy rather than forwarded to the target system. This action only applies to `OnPremise` destinations. The caller's identity is not used, and any caller-supplied `Authorization` header is removed so it cannot be forwarded.

</td>
</tr>
</table>



## Configuring an Action

Actions are configured under *spec.actions* of a destination custom resource. Each action has:

-   `name`: the action type, one of `OAuth2JWTBearer`, `OAuth2ClientCredentials`, or `OAuth2TechnicalUserPropagation`.
-   `secretRef`: a reference to a *Kubernetes Secret* that holds the credentials used to obtain the token. `name` and `key` are required; `namespace` is optional and defaults to the namespace of the destination.
-   `triggers` \(optional\): conditions that control when the action is applied. See section *Triggers* below.

The secret referenced by `secretRef` must contain, at the given `key`, a JSON object with the credentials \(for example, client ID and client secret, or a client certificate and key\).

> ### Sample Code:  
> ```
> apiVersion: destination.connectivity.api.sap/v1
>   kind: Destination
>   metadata:
>     name: jwtbearer-example
>   spec:
>     destinationRef:
>       name: http
>     actions:
>       - name: OAuth2JWTBearer
>         secretRef:
>           name: jwtbearer-credentials
>           key: credentials
>         triggers:
>           - name: exactMatch
>             matches:
>               - destinationProperty: HTML5.ForwardAuthToken
>                 value: "true"
>           - name: exist
>             destinationProperties:
>               - "tokenService.body.resource"
>   
> ```

> ### Sample Code:  
> OAuth2TechnicalUserPropagation
> 
> ```
> apiVersion: destination.connectivity.api.sap/v1
>   kind: Destination
>   metadata:
>     name: technicaluserpropagation-example
>   spec:
>     destinationRef:
>       name: onpremise-http
>     actions:
>       - name: OAuth2TechnicalUserPropagation
>         secretRef:
>           name: technicaluserpropagation-credentials
>           key: credentials
>   
> ```



## Triggers

By default, an action is applied to every request. Add one or more triggers to apply an action only when the destination meets certain conditions. When multiple triggers are configured, *all* of them must be given for the action to run.

Two trigger types are available:

**exist**

Applies the action when the listed destination properties and/or destination labels are present, regardless of their values.

-   `destinationProperties` – a list of destination property names that must exist.
-   `destinationLabelKeys` – a list of destination label keys that must exist.

At least one of `destinationProperties` or `destinationLabelKeys` must be provided.

**exactMatch**

Applies the action only when every listed condition matches. Provide the conditions under `matches`. Each condition targets either a destination property or a destination label:


<table>
<tr>
<th valign="top">

Fields

</th>
<th valign="top">

Matches when

</th>
</tr>
<tr>
<td valign="top">

`destinationProperty` + value

</td>
<td valign="top">

the destination property equals value.

</td>
</tr>
<tr>
<td valign="top">

`OAuth2ClientCredentials`

</td>
<td valign="top">

*Technical access*. Obtains a technical \(machine-to-machine\) IAS access token using the client credentials grant. The caller's identity is not used. The minted token is set as the `Authorization` header.

</td>
</tr>
<tr>
<td valign="top">

`OAuth2TechnicalUserPropagation`

</td>
<td valign="top">

*Technical access for on-premise connectivity*. Obtains a technical \(machine-to-machine\) IAS access token and sets it as the `SAP-Connectivity-Technical-Authentication` header, which is consumed by the Connectivity Proxy rather than forwarded to the target system. This action only applies to `OnPremise` destinations. The caller's identity is not used, and any caller-supplied `Authorization` header is removed so it cannot be forwarded.

</td>
</tr>
</table>



## Compatibility with the Destination Authentication Type

An action can only be applied when it does not conflict with the credentials the destination already provides. An action is allowed when the destination's authentication is `NoAuthentication`, `ClientHandledAuthentication`, or the same type as the action itself; any other authentication type is rejected. The following combinations are allowed:


<table>
<tr>
<th valign="top">

Destination Authentication

</th>
<th valign="top">

OAuth2JWTBearer

</th>
<th valign="top">

OAuth2ClientCredentials

</th>
<th valign="top">

OAuth2TechnicalUserPropagation

</th>
</tr>
<tr>
<td valign="top">

`NoAuthentication`

</td>
<td valign="top">

yes

</td>
<td valign="top">

yes

</td>
<td valign="top">

yes

</td>
</tr>
<tr>
<td valign="top">

`ClientHandledAuthentication`

</td>
<td valign="top">

yes

</td>
<td valign="top">

yes

</td>
<td valign="top">

yes

</td>
</tr>
<tr>
<td valign="top">

`OAuth2JWTBearer`

</td>
<td valign="top">

yes

</td>
<td valign="top">

no

</td>
<td valign="top">

no

</td>
</tr>
<tr>
<td valign="top">

`OAuth2ClientCredentials`

</td>
<td valign="top">

no

</td>
<td valign="top">

yes

</td>
<td valign="top">

no

</td>
</tr>
<tr>
<td valign="top">

`OAuth2TechnicalUserPropagation`

</td>
<td valign="top">

no

</td>
<td valign="top">

no

</td>
<td valign="top">

yes

</td>
</tr>
<tr>
<td valign="top">

Any other authentication type

</td>
<td valign="top">

no

</td>
<td valign="top">

no

</td>
<td valign="top">

no

</td>
</tr>
</table>

If an action is not compatible with the destination's authentication type, the destination is not configured and requests to it fail. The destination's status reports that the authentication type is not compatible with the configured action.



## Additional Requirements for OAuth2TechnicalUserPropagation

Beyond authentication-type compatibility, `OAuth2TechnicalUserPropagation` has two runtime requirements that are enforced when a request is processed:

-   The destination must have `ProxyType` `OnPremise`. If it does not, the request fails and the destination status reports that the action requires an `OnPremise` destination.
-   The destination must provide a non-empty `tokenServiceURL`. If it is not present, the request fails and the status reports the missing token service configuration.

Unlike the other actions, `OAuth2TechnicalUserPropagation` does not set the `Authorization` header. It sets the `SAP-Connectivity-Technical-Authentication` header \(overwriting any existing value\) and removes any caller-supplied `Authorization` header from the forwarded request. Its token is not fed to any subsequent `Authorization`-based action in the same destination.



## Prerequisites for IAS Actions

All actions require IAS configuration on the SAP BTP destination:

-   `OAuth2JWTBearer` requires the IAS dependency name \(`tokenService.body.resource`\).

    For more information, see [OAuth JWT Bearer Authentication](oauth-jwt-bearer-authentication-a728ae0.md).

-   `OAuth2ClientCredentials` requires the IAS dependency name \(`tokenService.body.resource`\) and the token service URL \(`tokenServiceURL`\).

    For more information, see [OAuth Client Credentials Authentication](oauth-client-credentials-authentication-cf15900.md).

-   `OAuth2TechnicalUserPropagation` requires the IAS dependency name \(`tokenService.body.resource`\) and the token service URL \(`tokenServiceURL`\). The destination must use proxy type `OnPremise`.

    For more information, see [Technical User Propagation](technical-user-propagation-8b6e019.md).


These values are taken from the destination configuration returned by the Destination service. If a required value is missing, the destination is not configured and its status indicates the missing information.



## Validation and status

When a Destination custom resource is created or changed, the Transparent Proxy validates its actions and reports the result in the resource's status conditions. Configuration problems that prevent an action from being applied include:

-   The referenced Secret does not exist, cannot be read, or does not contain the specified key.
-   A trigger is malformed \(unknown trigger type or an invalid combination of fields\).
-   The action is not compatible with the destination's authentication type.
-   Required IAS configuration is missing from the destination.
-   For `OAuth2TechnicalUserPropagation`: the destination is not an `OnPremise` destination, or it is missing `tokenServiceURL`.

While such a condition is present, the destination is not usable and requests to it fail. Correct the configuration and the destination becomes available again.

