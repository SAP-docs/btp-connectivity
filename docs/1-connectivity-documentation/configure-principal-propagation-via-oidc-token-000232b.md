<!-- loio000232bddce348ecb068fcbf9d13717d -->

# Configure Principal Propagation via OIDC Token

Configure an OpenID-Connect \(OIDC\) token for principal propagation \(user propagation\) from your application to an on-premise system.

> ### Note:  
> For more information on OIDC, see [OpenID Specifications](https://openid.net/developers/specs/).

> ### Note:  
> The on-premise use cases described in this guide are also applicable to virtual private cloud \(VPC\) environments.



<a name="loio000232bddce348ecb068fcbf9d13717d__tasks_pp_cs"/>

## Tasks


<table>
<tr>
<th valign="top">

Task Type

</th>
<th valign="top">

Task

</th>
</tr>
<tr>
<td valign="top">

![](images/CS_TASK_Admin_Dev_7c2c6d8.png)

Operator and/or Developer

</td>
<td valign="top">

[Scenario](configure-principal-propagation-via-oidc-token-000232b.md#loio000232bddce348ecb068fcbf9d13717d__scenario) 

</td>
</tr>
<tr>
<td valign="top">

![](images/CS_TASK_Dev_a4c82d5.png)

Developer

</td>
<td valign="top">

[Solution](configure-principal-propagation-via-oidc-token-000232b.md#loio000232bddce348ecb068fcbf9d13717d__solutions) 

</td>
</tr>
</table>



<a name="loio000232bddce348ecb068fcbf9d13717d__scenario"/>

## Scenario

![](images/CS_TASK_Admin_Dev_7c2c6d8.png)

For a Cloud Foundry application that uses the Connectivity service, you want the currently logged-in user to be propagated via the Cloud Connector to an on-premise system. This user is represented in the cloud application by an OIDC token. For more information, see [Principal Propagation](principal-propagation-e2cbb48.md) and the [OIDC specification](https://openid.net/connect/).

Back to [Tasks](configure-principal-propagation-via-oidc-token-000232b.md#loio000232bddce348ecb068fcbf9d13717d__tasks_pp_cs) 



<a name="loio000232bddce348ecb068fcbf9d13717d__solutions"/>

## Solution

![](images/CS_TASK_Dev_a4c82d5.png)

The Cloud Connector supports principal propagation for OIDC tokens. If on the cloud application side the user is represented by an OIDC token, the application can send the user principal to the Connectivity service \(thus reaching the Cloud Connector\), using the `SAP-Connectivity-Authentication` HTTP header.

The Cloud Connector validates the token, extracts the available user data, and enables further processing through a configured subject pattern for the resulting short-lived X.509 client certificate.

By default, the user principal is identified by one of the following JWT \(JSON web token\) attributes:

-   `user_name`
-   `email`
-   `mail`
-   `user_uuid`
-   `sub`

This list specifies the priority \(in descending order from top to bottom\) for the default value of `${name}` in the subject pattern of the X.509 client certificate. If a token has more than one of the above claims, the value of `${name}` is extracted from the claim with the highest priority by default.

For the example token below, the default value of `${name}` is `test@user.com`:

> ### Sample Code:  
> ```
> {
>   "aud": "111111111111-2222-3333-444444444444",
>   "iss": "https://issuer.com",
>   "exp": 2091269073,
>   "iat": 1601901108,
>   "jti": "111222333444555666777888999000",
>   "sub": "test",
>   "email": "test@users.com"
> }
> ```

The Cloud Connector administrator can control the exact value to be used as user principal for the *subject CN* of the X.509 client certificate by configuring a subject pattern. For more information, see [Configure Subject Patterns](configure-subject-patterns-58803a2.md).

Back to [Tasks](configure-principal-propagation-via-oidc-token-000232b.md#loio000232bddce348ecb068fcbf9d13717d__tasks_pp_cs) 

