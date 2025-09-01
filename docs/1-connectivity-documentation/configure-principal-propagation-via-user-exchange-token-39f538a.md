<!-- loio39f538ad62e144c58c056ebc34bb6890 -->

# Configure Principal Propagation via User Exchange Token

Configure a user exchange token for principal propagation \(user propagation\) from your application to an on-premise system.

> ### Note:  
> The on-premise use cases described in this guide are also applicable to virtual private cloud \(VPC\) environments.

> ### Restriction:  
> Principal Propagation via user exchange token is not supported with IAS proxy authorization. In this case, the principal should be propagated through the "SAP-Connectivity-Authentication" header.
> 
> For more information, see [Authentication to the On-Premise System](authentication-to-the-on-premise-system-67b0b94.md).



<a name="loio39f538ad62e144c58c056ebc34bb6890__tasks_pp_cs"/>

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

[Scenario](configure-principal-propagation-via-user-exchange-token-39f538a.md#loio39f538ad62e144c58c056ebc34bb6890__scenario) 

</td>
</tr>
<tr>
<td valign="top" rowspan="2">

![](images/CS_TASK_Dev_a4c82d5.png)

Developer

</td>
<td valign="top">

[Solutions](configure-principal-propagation-via-user-exchange-token-39f538a.md#loio39f538ad62e144c58c056ebc34bb6890__solutions) 

</td>
</tr>
<tr>
<td valign="top">

[Generate the Authentication Token](configure-principal-propagation-via-user-exchange-token-39f538a.md#loio39f538ad62e144c58c056ebc34bb6890__generate) 

</td>
</tr>
</table>



<a name="loio39f538ad62e144c58c056ebc34bb6890__scenario"/>

## Scenario

![](images/CS_TASK_Admin_Dev_7c2c6d8.png)

For a Cloud Foundry application that uses the Connectivity service, you want the currently logged-in user to be propagated to an on-premise system. For more information, see [Principal Propagation](principal-propagation-e2cbb48.md).

> ### Note:  
> When performing a token exchange, the resulting token may lose some of its fields.

Back to [Tasks](configure-principal-propagation-via-user-exchange-token-39f538a.md#loio39f538ad62e144c58c056ebc34bb6890__tasks_pp_cs) 



<a name="loio39f538ad62e144c58c056ebc34bb6890__solutions"/>

## Solutions

![](images/CS_TASK_Dev_a4c82d5.png)

You have two options to implement user propagation:

1.  **Recommended**: The application sends one header containing the user exchange token to the Connectivity proxy:

    ```
    Header: "Proxy-Authorization" : "Bearer <userExchangeAcessToken>"
    ```

    This option is described in detail in [Generate the Authentication Token](configure-principal-propagation-via-user-exchange-token-39f538a.md#loio39f538ad62e144c58c056ebc34bb6890__generate) below.

2.  The application sends two headers to the Connectivity proxy:

    ```
    Header: "SAP-Connectivity-Authentication" : "Bearer <userToken>" 
    
    Header: "Proxy-Authorization" : "Bearer <accessToken>"
    ```

    For more information about this solution, see also [Consuming the Connectivity Service](consuming-the-connectivity-service-313b215.md).

    > ### Note:  
    > This solution is supported to guarantee backward compatibility.


Back to [Tasks](configure-principal-propagation-via-user-exchange-token-39f538a.md#loio39f538ad62e144c58c056ebc34bb6890__tasks_pp_cs) 



<a name="loio39f538ad62e144c58c056ebc34bb6890__generate"/>

## Generate the Authentication Token

![](images/CS_TASK_Dev_a4c82d5.png)

To propagate a user to an on-premise system, you must call the Connectivity proxy using a special JWT \(JSON Web token\). This token is obtained by exchanging a valid user token following the [OAuth2 JWT Bearer grant type](https://tools.ietf.org/html/rfc7523#section-2.1).

> ### Note:  
> When using this type of exchange, some of the attributes inside the original user token may not be present in the created JWT.

-   [Example: Obtaining a User Token Following the JWT Bearer Grant Type](configure-principal-propagation-via-user-exchange-token-39f538a.md#loio39f538ad62e144c58c056ebc34bb6890__ex_user)
-   [Example: Calling the Connectivity Proxy with the Exchanged User Token](configure-principal-propagation-via-user-exchange-token-39f538a.md#loio39f538ad62e144c58c056ebc34bb6890__ex_proxy)

**Example: Obtaining a User Token Following the [JWT Bearer Grant Type](http://docs.cloudfoundry.org/api/uaa/version/74.0.0/#jwt-bearer-token-grant)**

*Request:*

> ### Sample Code:  
> ```
> POST https://<host: the value of 'url' from Connectivity service credentials in VCAP_SERVICES>/oauth/token
> Accept: application/json
> Content-Type: application/x-www-form-urlencoded
> 
> client_id=<connectivity_service_client_id>
> client_secret=<connectivity_service_client_secret>
> grant_type=urn:ietf:params:oauth:grant-type:jwt-bearer
> token_format=jwt
> response_type=token
> assertion=<logged-in-user-JWT>
> ```

*Response:*

> ### Sample Code:  
> ```
> {
>     "access_token" : "<new-user-JWT>",
>     "token_type" : "bearer",
>     "expires_in" : 43199,
>     "scope" : "<token-scopes>",
>     "jti" : "7cc917b8bf6347a2aa18d7ac8f38a1c2"
> }
> ```

The JWT in `access_token`, also referred to as *user exchange token*, now contains the user details. It is used to consume the Connectivity service.

In case of a Java application, you can use a library that implements the user exchange OAuth flow. Here is an example of how the `userExchangeAcessToken` can be obtained using the [XSUAA Token Client and Token Flow API](https://github.com/SAP/cloud-security-xsuaa-integration/tree/master/token-client):

> ### Caution:  
> Make sure you get the latest API version.

A sample Maven dependency declaration:

```
<dependency>
	<groupId>com.sap.cloud.security.xsuaa</groupId> 
	<artifactId>token-client</artifactId> 
	<version><latest version (e.g.: 2.7.7)></version> 
</dependency>
```

> ### Remember:  
> The XSUAA Token Client library works with multiple HTTP client libraries. Make sure you have one as Maven dependency.

The following sample uses the Apache REST client:

> ### Sample Code:  
> ```
> // service instance specific OAuth client credentials shall be used
> String connectivityServiceClientId = credentials.getString(CLIENT_ID);
> String connectivityServiceClientSecret = credentials.getString(CLIENT_SECRET);
> 
> // get the URL to xsuaa from the environment variables
> URI xsuaaUri = new URI(xsuaaCredentials.getString("token_service_url"));
>  
> // use the XSUAA client library to ease the implementation of the user token exchange flow
> XsuaaTokenFlows tokenFlows = new XsuaaTokenFlows(new DefaultOAuth2TokenService(), new XsuaaDefaultEndpoints(xsUaaUri.toString()), new ClientCredentials(connectivityServiceClientId, connectivityServiceClientSecret));
> String userExchangeAcessToken = tokenFlows.userTokenFlow().token(<jwtToken_to_exchange>).execute().getAccessToken();
> ```

For more information about caching, see also [XSUAA Token Client and Token Flow API - Cache](https://github.com/SAP/cloud-security-xsuaa-integration/tree/master/token-client#cache).

> ### Note:  
> `xsuaaCredentials.getString("token_service_url")` replaces the deprecated property `xsuaaCredentials.getString("url")`, which will be removed soon.

See also: [XSUAA Token Client and Token Flow API](https://github.com/SAP/cloud-security-xsuaa-integration/blob/master/token-client).

After obtaining the `userExchangeAcessToken`, you can use it to consume the Connectivity service.

Back to [Generate the Authentication Token](configure-principal-propagation-via-user-exchange-token-39f538a.md#loio39f538ad62e144c58c056ebc34bb6890__generate)

**Example: Calling the Connectivity Proxy with the Exchanged User Token**

As a prerequisite to this step, you must configure the Connectivity proxy to be used by your client, see [Set up the HTTP Proxy for On-Premise Connectivity](consuming-the-connectivity-service-313b215.md#loio313b215066a8400db461b311e01bd99b__section_HttpProxy).

Once the application has retrieved the user exchange token, it must pass the token to the Connectivity proxy via the `Proxy-Authorization` header. In this example, we use `urlConnection` as a client.

> ### Sample Code:  
> ```
> // set user exchange token as Proxy-Authorization header in the URL connection
> urlConnection.setRequestProperty("Proxy-Authorization", "Bearer " + userExchangeAcessToken);
> ```

> ### Note:  
> Alternatively, you can use the *basic authentication* scheme:

> ### Sample Code:  
> ```
> // Basic authentication to Connectivity Proxy
> String credentials = MessageFormat.format("{0}:{1}", userExchangeAcessToken, "");
> byte[] encodedBytes = Base64.encodeBase64(credentials.getBytes());
> urlConnection.setRequestProperty("Proxy-Authorization", "Basic " + new String(encodedBytes));
> ```

Back to [Generate the Authentication Token](configure-principal-propagation-via-user-exchange-token-39f538a.md#loio39f538ad62e144c58c056ebc34bb6890__generate)

Back to [Tasks](configure-principal-propagation-via-user-exchange-token-39f538a.md#loio39f538ad62e144c58c056ebc34bb6890__tasks_pp_cs) 

